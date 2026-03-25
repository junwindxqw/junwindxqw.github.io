<img width="306" height="255" alt="Image" src="https://github.com/user-attachments/assets/6ef44a49-5ddc-4a70-a029-189501f71d1c" />

解决办法： 

    把需要联表查询的条件，提前查出来。 用 in ， 附加到主表。

```php
$oWhere = [
    'userid' => ['in', [1,2,3]],
    'cid' => ['in', [4,5,6]],
    ......
];
```

<img width="587" height="313" alt="Image" src="https://github.com/user-attachments/assets/1bc2f396-5d80-4480-b4d0-861a72a26db9" />