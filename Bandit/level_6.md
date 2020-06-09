# Bandit Level 6 -> Level 7

The password for the next level is stored _somewhere on the server_ and has all of the following properties:

1. Owned by user `bandit7`
1. Owned by group `bandit6`
1. 33 bytes in size

## Find starting from root

```shell
find / ...
```

## Find files owned by user `bandit7`

```shell
find / -user bandit7
```

## Find files owned by group `bandit6`

```shell
find / -group bandit6
```

## Find files that are 33 bytes in size

```shell
find / -size 33c
```

## Final Command

```shell
find / -user bandit7 -group bandit6 -size 33c
```

_Result_

```shell
find: ‘/root’: Permission denied
...
/var/lib/dpkg/info/bandit7.password
```

`cat /var/lib/dpkg/info/bandit7.password`

# PASSWORD

HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
