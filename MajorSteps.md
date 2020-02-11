# Main steps and prerequisite
* __Step 1__
  * configure static ip
* __Step 2__
  * stop and disable NetworkManager as it conflicts later with some services
* __Step 3__ configure yum or yum server and add your repos of openstack to it (iso)
  * mount your iso locally 
  * transfer all the rpms into another directory 
  * and make repodata of that folder to use it as main repo where you have all required rpms of openstack
  * _Interesting Fact_ 
    * _when you do this you must check free ram available by 'free -m' you might get free ram very low so where does that free ram go?
    Here is the thing that when you transfer something or do someting it runs on ram and then after the work is done it disappears from 
    the ram (as ram is volatile memory) but there are some processes that stuck on ram (this may happen in this case) (it creates caches of it)
    ...as we need ram to install openstack services ...so just reboot your system or you can do 'cat /proc/sys/vm/drop_caches' (it is 0) 
    change it to 3 by 'echo 3 > /proc/sys/vm/drop_caches' (don't open it by gedit or vim) then run 'free -m' your ram is free now
* __Step 4__
  * now install openstack-packstack _it is the installer for openstack_
* __Step 5__
  * Generate answer file by 'packstack --gen-answer-file=openstacksetup.txt' after this open it and select services you want by y and n
* __Step 6__
  * Run 'packstack --answer-file=openstacksetup.txt' to install the services of openstack
