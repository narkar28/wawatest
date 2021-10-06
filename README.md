# repo is about to check the system info using ansible with jinja2 template
- Render a template that outputs a role variable and information (cpu, kernel, memory) about your operating system
   result system-info.txt 

- The variable should have a default value in the role and be overridden by the playbook
     in the vars we defined as "karthik" and while running with playbook going with extra vars "wawa" (for example, -e "user=my_user")(always win precedence)
  
```
{
[haris_kartik@ansiblectrl ansible]$ ansible-playbook get_sys_info.yaml  -e user_name=wawa
PLAY [system info] *************************************************************************************************
TASK [Gathering Facts] *********************************************************************************************
ok: [10.128.0.25]
ok: [10.128.0.24]
TASK [system-info : show jinja template results] *******************************************************************
ok: [10.128.0.24] => {
    "msg": "No of CPUs for ansiblectrl is 2\nTotal memory on ansiblectrl in mb is 3786\ncurrent kernel on ansiblectr
l  is 3.10.0-1160.42.2.el7.x86_64\n"
}
ok: [10.128.0.25] => {
    "msg": "No of CPUs for ansnode1 is 2\nTotal memory on ansnode1 in mb is 3786\ncurrent kernel on ansnode1  is 3.1
0.0-1160.42.2.el7.x86_64\n"
}
TASK [system-info : display role variables] ************************************************************************
ok: [10.128.0.24] => {
    "msg": "wawa"
}
ok: [10.128.0.25] => {
    "msg": "wawa"
}
TASK [system-info : copying template results to /home/haris_kartik/ansible] ****************************************
ok: [10.128.0.25]
ok: [10.128.0.24]
PLAY RECAP *********************************************************************************************************
10.128.0.24                : ok=4    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0  
 
10.128.0.25                : ok=4    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0  
 
[haris_kartik@ansiblectrl ansible]$ 
```
}
