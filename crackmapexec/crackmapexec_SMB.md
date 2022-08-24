# SMB
Get password policy:

```shell
crackmapexec smb 10.129.95.210 --pass-pol
```

Test for anonymous users, present in, or if updated from, Windows Server 2003:

```shell
crackmapexec smb 10.129.95.210 --pass-pol -u '' -p ''
```

Login as user

```shell
crackmapexec smb 10.129.95.210 -u [username] -p [password]
```

List SMB shares
```shell
crackmapexec smb 10.129.124.112 --shares -u '' -p ''
```

```shell
crackmapexec smb 10.129.95.210 -u [username] -p [password] --shares
```
