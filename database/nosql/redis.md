

# redis on windows


https://github.com/MSOpenTech/redis/releases


windows服务加入，不会启动redis-server

redis-server --service-install redis.windows.conf --loglevel verbose

windows服务移除，不会关闭redis-server

redis-server --service-uninstall

windows服务开启

redis-server --service-start

windows服务关闭

redis-server --service-stop

This optional argument may be used with any of the preceding commands to set the name of the installed service. This argument should follow the service-install, service-start, service-stop or service-uninstall commands, and precede any arguments to be passed to Redis via the service-install command.

The following would install and start three separate instances of Redis as a service:

redis-server --service-install --service-name redisService1 --port 10001

redis-server --service-start --service-name redisService1

redis-server --service-install --service-name redisService2 --port 10002

redis-server --service-start --service-name redisService2

redis-server --service-install --service-name redisService3 --port 10003

redis-server --service-start --service-name redisService3


## logs

### backlog

avoid slow clients connections issues

- 相关配置项

  - tcp-backlog
  
### log

- 相关配置项

  - loglevel
  - logfile
  - syslog-enabled
  
  
repl-backlog-size

当从库与主库失去连接时，数据改变会存进 复制backlog，待主从重新连接时数据同步入从库 这个log文件的size越大，主从可失去连接的时间就能越长
