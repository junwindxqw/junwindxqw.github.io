<img width="306" height="255" alt="Image" src="https://github.com/user-attachments/assets/6ef44a49-5ddc-4a70-a029-189501f71d1c" />

解决办法： 
- 把需要联表查询的条件，提前查出来。 用 in ， 附加到主表。
- 比如有个筛选条件是user表的昵称
```php
$uWhere = [];
if (isset($filter['nickname'])) {
    $uWhere['nickname'] = ['like', "%{$filter['nickname']}%"];
    unset($filter['nickname'], $op['nickname']);
}
// user表的其它筛选条件都可以放在$uWhere中
if (!empty($uWhere )) {
     // 绑定userId条件到主查表中，因为主查表中是有userId字段的，这样就把本身要join user 的查询给干掉了。
    $filter['userId'] = Db::name('user')->where($uWhere)->column('id') ?? [];
    $op['userId'] = 'in';
}

// 其它条件处理 ... 

$this->request->get(['filter' => json_encode($filter)]);
$this->request->get(['op' => json_encode($op)]);
list($where, $sort, $order, $offset, $limit) = $this->buildparams();

// 此时 多 join 就被干为 单表查询了。 实测速度提升明显。
$list = Db::name('xxx')
      ->where($where)
      ->field('*')
      ->order("id desc")
      ->paginate($limit);
```

后面如果需要join表中的字段，可以再查出来，比如user表的nickname
```php
$row = $list->rows();
$userList = Db::name('user')->whereIn('id', array_column($row, 'userId'))->column('nickname', 'id');
```

