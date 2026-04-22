    sudo usermod -aG sudo xqw
    
    sudo visudo    //  打开 /etc/sudoers 文件
    
    root    ALL=(ALL:ALL) ALL
    xqw     ALL=(ALL:ALL) ALL     // xqw     ALL=(ALL:ALL) NOPASSWD: ALL

