Start etcd in one shell session with:

  $ ./etcd-v3.1.8-linux-amd64/etcd

In another shell session, set up some keys:

  $ ./etcd-v3.1.8-linux-amd64/etcdctl set /keystone/DEFAULT/admin_token very_secret_from_etcd

In the same session, run confd:

  $ ./confd -prefix=/keystone -confdir=$PWD -onetime -backend etcd -node http://127.0.0.1:2379

Look at the output file:

  $ cat /tmp/myconfig.conf
