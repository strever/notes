

- non-thread

cgi


- thread-safe

used for apache module worker MPM or iis multi-thread




ini_set('display_errors', 1);




# session

无论是通过调用函数 session_start() 手动开启会话， 还是使用配置项 session.auto_start 自动开启会话， 对于基于文件的会话数据保存（PHP 的默认行为）而言， 在会话开始的时候都会给会话数据文件加锁， 直到 PHP 脚本执行完毕或者显式调用 session_write_close() 来保存会话数据。 在此期间，其他脚本不可以访问同一个会话数据文件。
对于大量使用 Ajax 或者并发请求的网站而言，这可能是一个严重的问题。 解决这个问题最简单的做法是如果修改了会话中的变量， 那么应该尽快调用 session_write_close() 来保存会话数据并释放文件锁。 还有一种选择就是使用支持并发操作的会话保存管理器来替代文件会话保存管理器。

会话开始的时候，PHP 会调用 open 管理器，然后再调用 read 回调函数来读取内容，该回调函数返回已经经过编码的字符串。 然后 PHP 会将这个字符串解码，并且产生一个数组对象，然后保存至 $_SESSION 超级全局变量。

当 PHP 关闭的时候（或者调用了 session_write_close() 之后）， PHP 会对 $_SESSION 中的数据进行编码， 然后和会话 ID 一起传送给 write 回调函数。 write 回调函数调用完毕之后，PHP 内部将调用 close 回调函数。

销毁会话时，PHP 会调用 destroy 回调函数。


# cli sapi

在运行时，不会把工作目录改为脚本的当前目录

CLI SAPI 强制覆盖了 php.ini 中的某些设置

- html_errors false
- implicit_flush true  在命令行模式下，所有来自 print 和 echo 的输出将被立即写到输出端，而不作任何地缓冲操作
- max_execution_time 0 无限
- register_argc_argv true 将总是可以在 CLI SAPI 中访问到 argc（传送给应用程序参数的个数）和 argv（包含有实际参数的数组）。

标配打开三个流

- STDIN
- STDOUT
- STDERR

`php -r 'fwrite(STDERR, "stderr\n");'`

无需自己来关闭这些流，PHP 会自动完成这些操作。



