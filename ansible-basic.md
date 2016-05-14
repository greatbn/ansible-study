###shell
`ansible <alias_host> -m 'module_name' -a 'argument' <--become> <--ask-become-pass>`

eg: `ansible all -m 'shell' -a 'echo Sa Phi'`

###copy file

`ansible <alias_host> -m copy -a "src=path_to_file dest=path_to_file"`

eg: `ansible all -m copy -a "src=/etc/hosts dest=/etc/hosts"`

<img src="http://i.imgur.com/6SPz4XO.png">

###`file` module

- change permission , owner file

`ansible <alias_host> -m file -a "dest=/path_to_file mode=xxx owner=user group=group"`

eg: `ansible web -m file -a "dest=/tmp/a.txt mode=600 owner=saphi group=saphi"`

- make a directory

eg: `ansible web -m file -a "dest=/tmp/b mode=664 owner=saphi group=saphi state=directory"`

- delete a file

eg: `ansible web -m file -a "dest=/tmp/b state=absent"`

###manage package

- there are two modules is yum and apt

- install packge

eg: `ansible www -m apt -a "name=nginx state=present" --become --ask-become-pass`

<img src="http://i.imgur.com/JbrNVZk.png">

- install package at the latest version

eg: `ansible www -m apt -a "name=nginx state=latest" --become --ask-become-pass`

- remove package

eg: `ansible www -m apt -a "name=nginx state=absent" --become --ask-become-pass`

###user and group

- add user

eg: `ansible www -m user -a "name=manh password=123456" --become --ask-become-pass`

<img src="http://i.imgur.com/7gLisGd.png">

- remove user

eg: `ansible www -m user -a "name=manh state=absent" --become --ask-become-pass`

###deploy from source

eg: `ansible www -m git -a "repo=https://github.com/aaa/www dest=/src/myapp version=HEAD"`


<img src="http://i.imgur.com/vlglVnu.png">

###manage service

- start service

eg: `ansible www -m service -a "name=nginx state=started"`

- restart service

eg: `ansible www -m service -a "name=nginx state=restarted"`

- stop service

eg: `ansible www -m service -a "name=nginx state=stopped"`
