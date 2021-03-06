# JKIT CLI

JKIT cli help you control deploying/installing/operating OKD on KVM

In order to use JKIT, you should install click package by pip

```
pip2 install click
```

*CLI command syntax*
```
./jkit.py --deploy_type=okd --op=[start,stop,teardown,deploy,provision,install] --tag: Change tag name -vvvv 

* optiopns
--deploy_type: okd is only one option. It can be enhanced(ex. metrics/scale)
               'okd' is default so it can be skipped.
         --op: main operate 
               'deploy' is default.
        --tag: 'all.yml' parameter is default.
```


*Detail workflow*

- operate `deploy`
  - KVM install
  - VM creation 
  - Prerequisites
    - Install neccessary packages
    - Docker
    - etc
  - Execute Prerequisites playbook by official OKD ansible playbook
  - Install OKD

```
./jkit.py --op=deploy
```

- operate `provision`
  - KVM install
  - VM creation 
  - Prerequisites
    - Install neccessary packages
    - Docker
    - etc

```
./jkit.py --op=provision
```

- operate `install`
  - Execute Prerequisites playbook by official OKD ansible playbook
  - Install OKD 
  - If you already have VM or if you encounted any issues during OKD installation
  
```
./jkit.py --op=install
```

- operate `start/stop/suspend/destroy/teardown`
  - start/stop 
  - vm status
  - teardown
    - Delete VMs
    - Delete DNSMasq Config file
    - Delete hosts from Known_hosts


```
./jkit.py --op=[start,stop,suspend,destroy,teardown] --tag=test
```
