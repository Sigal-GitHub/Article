第4集 Nginx1.19性能优化与测试
-------------------------------------------------------------------

一.Nginx进程与线程模式:
1.进程线程模式：主进程->多Worker工作进程(Cpu核数)->单线程(默认)
2.内存消耗极低

二.Linux下高并发打开文件数:
1.查看
ulimit -n
1024

2.设置
vi /etc/security/limits.conf

最后加上

*               soft    nofile           65535
*               hard    nofile           65535

3.重启生效
init 6

重启再使用 ulimit -n 就能看到生效了

三.Nginx配置参考:
1.worker_processes  2;
nginx运行工作进程个数，一般设置cpu的核心，如：worker_processes 2。
cat /proc/cpuinfo |grep processor命令可查看核数

2.worker_cpu_affinity 0001 0010;
运行CPU亲和力，与worker_processes对应，如：worker_cpu_affinity 0001 0010。

3.worker_rlimit_nofile 65535;
Nginx最多可以打开文件数，与ulimit -n保持一致，如：worker_rlimit_nofile 65535。

4.events
事件处理模型。

5.use epoll;
epoll是linux2.6内核的一个新的系统调用，epoll在设计之初，就是为了替代select, poll线性复杂度的模型，nginx采用边沿触发。

6.worker_connections 65535;
是单个worker进程允许客户端最大连接数，这个数值一般根据服务器性能和内存来制定，实际最大值就是worker进程数乘以work_connections，实际我们填入一个65535，足够了。

7.keepalived_timeout 60;
客户端连接保持会话超时时间，超过这个时间，服务器断开这个链接。

8.keepalive_requests 10240;
参数限制了一个HTTP长连接最多可以处理完成的最大请求数, 默认是100。当连接处理完成的请求数达到最大请求数后，将关闭连接。

四.Stub_status测试
1.开启Stub_status模块:
/usr/local/nginx/sbin/nginx -V
有--with-http_stub_status_module说明已经开启该模块

2.Stub_status模块使用:
location /status {
   stub_status;
}

3.结果分析:
1).Active connections: 2
The current number of active client connections including Waiting connections.
当前活跃连接数。

2)server accepts handled requests 131 131 397
accepts(The total number of accepted client connections)
接受的客户端连接的总数。

handled(The total number of handled connections)
处理的连接总数。

requests(The total number of client requests)
客户端请求的总数。

4.Reading: 0 Writing: 1 Waiting: 1
Reading:The current number of connections where nginx is reading the request header.
nginx正在读取请求头的当前连接数。

Writing:The current number of connections where nginx is writing the response back to the client.
nginx将响应写回客户端的当前连接数。

Waiting:The current number of idle client connections waiting for a request.
等待请求的当前空闲客户端连接数。

4.ab压力测试
#cmder，ab在win下上限是20000
ab -n10 -c10 http://bbs.linux.com/index.html

ab -n1000 -c1000 http://bbs.linux.com/index.html

ab -n10000 -c10000 http://bbs.linux.com/index.html