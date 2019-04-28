# backstage_access_control
---
## Vulnerabilities is exist \Include\contorl.php 128 line
![f](https://github.com/cve-vul/vul/blob/master/SEMCMS/f.png)
**Function checkuser is Determine whether the user is logged in or not**

**In line 187**
```
$query=$db_conn->query("select * from sc_user where user_admin='$cookieuseradmin' and user_ps='$cookieuserpass'");
```
**Variables $cookieuseradmin and $cookieuserpass are obtained from cookies**

**And through test_input() and verify_str() two detection functions**
![b](https://github.com/cve-vul/vul/blob/master/SEMCMS/b.png)
![c](https://github.com/cve-vul/vul/blob/master/SEMCMS/c.png)

**So,Universal password "or 1 = 1" is not feasible. The equality sign is filtered in the verify_str function.**
**But! Password "or-1" is OK,So the final payload is:**
```
Payload:
select * from sc_user where user_admin='\' and user_ps=' or -1 #'
```
![g](https://github.com/cve-vul/vul/blob/master/SEMCMS/g.png)
