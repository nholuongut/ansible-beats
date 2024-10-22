# An Ansible role to deploy Elastic [Beats](https://www.elastic.co/products/beats) modules shipper.
![](https://i.imgur.com/waxVImv.png)
### [View all Roadmaps](https://github.com/nholuongut/all-roadmaps) &nbsp;&middot;&nbsp; [Best Practices](https://github.com/nholuongut/all-roadmaps/blob/main/public/best-practices/) &nbsp;&middot;&nbsp; [Questions](https://www.linkedin.com/in/nholuong/)
<br/>

**Only one shipper can be installed at a time using this role. If you want to install several shippers, run the role multiple times**

Requirements
------------

Supported targets:

- Debian 8 "Jessie"
- Debian 9 "Stretch"
- Debian 10 "Buster"
- RedHat EL 7
- Ubuntu 16.04 "Xenial"
- Ubuntu 20.04 "Bionic"


Role Variables
--------------

- `beats__shipper` - Beats software shipper to install. Supported: filebeat, metricbeat, heartbeat
- `beats__modules` - List of modules templates configuration files to add
- `beats__modules_sourcedir` - Modules templates directory. Default: `templates/`
- `beats__autostart` - Should autostart the daemon at installation step. Default: `yes`
- `beats__extra_options` - options to add at the end of configuration file
- `beats__logstash_enabled` - Is Logstash output enabled. Default: `false`
- `beats__logstash_index` - The index root name to write evetns to. Default: `undefined. which default to builtin value`
- `beats__logstash_hosts` - The list of downstream Logstash servers. Default: `["localhost:5044"]`
- `beats__elasticsearch_enabled` - Is ElasticSearch output enabled. Default: `false`
- `beats__elasticsearch_hosts` - The list of downstream ElasticSearch servers. Default: `["localhost:9200"]`
- `beats__elasticsearch_protocol` - ElasticSearch connection protocl. Default: "http"
- `beats__elasticsearch_user` - If auth enabled, provide username
- `beats__elasticsearch_password` - If auth enabled, provide password

Dependencies
------------

Ansible roles, can be pulled by ansible-galaxy or by hand in roles/

- `nholuong.elastic_repo`: https://galaxy.ansible.com/nholuong/elastic_repo/.


Usage
-----

Clone this repo into your roles directory:

    $ git clone https://github.com/nholuongut/ansible-beats.git roles/beats

Or use Ansible galaxy requirements.yml

    # nholuong.beats galaxy role

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - role: nholuong.beats
           elastic_repo__branch: 6.x
           beats__shipper: "filebeat"
           beats__elasticsearch_enabled: true
           beats__elasticsearch_hosts: ["192.168.1.1:9200", "192.168.1.2:9200"]
           beats__modules: ['system.yml.j2']
           beats__modules_sourcedir: "modules/"
           beats__extra_options: |
             xpack.monitoring.enabled: true
             logging.level: debug

Or can be configured in inventory files this way using oneliner:
```
[all:vars]
beats__logstash_hosts=["toto:5004"]
beats__modules=["system.yml.j2"]
```

TODO
-----

List of stuff to improve in this role
- readd tls stuff when needed

# 🚀 I'm are always open to your feedback.  Please contact as bellow information:
### [Contact ]
* [Name: nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com)

![](https://i.imgur.com/waxVImv.png)
![](Donate.png)
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.🌟
