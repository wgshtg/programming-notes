# pwd 指令說明與常見用法

`pwd`: print working directory，將當前工作目錄的完整路徑輸出到標準輸出

## 不同作業系統表示方式與變數使用

Windows

```cmd
# Windows cmd
%cd%
```

```powershell
# powershell
Get-Location
gl
pwd

# 使用變數
${pwd}
```

Unix/macOS

```sh
pwd
PWD

# 使用變數
$(pwd)
```
