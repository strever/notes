


## linux commands

- chown用法

用来更改某个目录或文件的用户名和用户组的
chown 用户名:组名 文件路径（可以是就对路径也可以是相对路径）
例1：chown root:root /tmp/tmp1
就是把tmp下的tmp1的用户名和用户组改成root和root（只修改了tmp1的属组）.
例2：chown -R root:root /tmp/tmp1
就是把tmp下的tmp1下的所有文件的属组都改成root和root。








```shell

grep -rl 'D:\/pingan\/codes'|xargs sed -i 's/D:\/pingan\/codes/D:\/documents\/eclipse\/workspace/g'


```


## windows shell

```shell

$ netstat -aon|findstr ":80"
$ tasklist|findstr "4"
$ netsh http show servicestate

```
