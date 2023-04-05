# LDAP 常見配置與使用情境

- 一種網路協議，用來存取和維護分散式目錄資訊服務。
- 樹狀結構，每個條目都有唯一的識別符 (DN)，包含屬性和值。
- 通常用於身份驗證、授權、存取控制等等。廣泛應用在企業內部的帳號管理、電子郵件等系統。

## 查詢 LDAP 記錄

```sh
# -x: simple authentication
# -h: ldaphost
# -D: username
# -w: password
# -b: search base
ldapsearch -x -h {host} -D "{username}" -w {password} -b "{base-dn}" {attribute}
```

## 刪除 LDAP 記錄

```sh
# -x: simple authentication
# -h: ldaphost
# -D: username
# -w: password
ldapdelete -x -h {host} -D "{username}" -w {password} "{want-to-delete-dn}"
```

## 更新 LDAP 記錄

```sh
# -x: simple authentication
# -h: ldaphost
# -D: username
# -w: password
# -f: entry modification information from file
ldapmodify -x -h {host} -D "{username}" -w {password} -f {modify.ldif}
```

