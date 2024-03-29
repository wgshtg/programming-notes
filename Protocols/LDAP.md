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

## 新增/更新/刪除符合條件的 DN 列表的 DN 屬性

1. 先查詢要異動的條目 (DN) 並輸出到檔案 modify.ldif

    ```sh
    ldapsearch -x -h localhost -D "cn=admin,dc=example,dc=org" -w admin -b "ou=users,dc=example,dc=org" dn > modify.ldif
    # output
    # fee63713-9a71-4c40-a50f-cb28200bc51e, users, example.org
    # dn: uid=fee63713-9a71-4c40-a50f-cb28200bc51e,ou=users,dc=example,dc=org
    # ...
    ```

2. 修改檔案內容，加入修改屬性內容

    ```txt
    # ffd954d5-0419-4e46-abaa-9600d14cb17d, users, example.org
    dn: uid=ffd954d5-0419-4e46-abaa-9600d14cb17d,ou=users,dc=example,dc=org
    # 修改 givenName 屬性，值為 John，sn 屬性，值為 Smith
    changetype: modify
    replace: givenName
    givenName: John
    -
    replace: sn
    sn: Smith
    -
    # 新增 mail 屬性，值為 john.smith@example.com
    add: mail
    mail: john.smith@example.com
    -
    # 刪除 email 屬性
    delete: email
    -
    # 刪除 cn 屬性值，只會刪除該指定值 (cn: Babs Morris 會被清除，cn: John Smith 不會被清除)
    delete: cn
    cn: Babs Morris
    ```

3. 使用 `ldapmodify` 指令來寫入異動

    ```sh
    ldapmodify -x -h localhost -D "cn=admin,dc=example,dc=org" -w admin -f {modify.ldif}
    ```

## 新增/刪除 DN

1. 準備包含異動內容的檔案 modify.ldif

    ```txt
    # 新增 DN
    dn: uid=aaaa54d5-0419-aaaa-abaa-9600d14cb17d,ou=users,dc=example,dc=org
    changetype: add
    objectClass: inetOrgPerson
    objectClass: extensibleObject
    cn: John Doe
    sn: Doe
    mail: john.doe@example.com

    # 刪除 DN
    dn: uid=bbbb54d5-0419-bbbb-abaa-9600d14cb17d,ou=users,dc=example,dc=org
    changetype: delete
    ```

2. 使用 `ldapmodify` 指令來寫入異動

    ```sh
    ldapmodify -x -h localhost -D "cn=admin,dc=example,dc=org" -w admin -f {modify.ldif}
    ```

## LDAP 查詢的條件表達式

(equals)： "="
(greater than or equal to)： ">="
(less than or equal to)： "<="
(approximate match)： "~="
(present)： "="，表示屬性存在
(substring match)： "=" 或 "="，表示屬性包含指定的子字符串

```txt
# 查詢所有名稱為 "John Doe" 的使用者
(&(objectClass=person)(cn=John Doe))
# 查詢所有電子郵件地址以 "example.com" 結尾的使用者
(&(objectClass=person)(mail=*@example.com))
# 查詢 uid 為任一值，carLicense 為任一值的 DN
"(&(uid=*)(carLicense=*))"
```
