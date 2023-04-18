# Filesystem Hierarchy Standard

`Filesystem Hierarchy Standard`(`FHS`): 檔案系統階層標準，定義 `UNIX` 系統的目錄結構。
一開始是在 1994-02-14 發布 `Filesystem Standard` (`FSSTND`)，並定為 `FSSTND 1.0`，後續持續發佈修正版本，在 1997-10-26 更名為成 `FHS`，發布 `FHS 2.0`。

| Path         | Definition                                                   |
|:-------------|:-------------------------------------------------------------|
| `/`          | 根目錄                                                       |
| `/bin`       | 基本系統工具和指令的路徑，像是 `ls`, `cp`, `mv` 等            |
| `/boot`      | Linux 核心和啟動時所需的相關檔案                             |
| `/dev`       | 裝置有關的檔案，像是印表機                                    |
| `/etc`       | 系統設定檔，原先是用 `etcetera` 表示，表示存放所有不屬於別處的所有東西，然而因為 `FHS` 限制只能放靜態檔案在 `/etc`。後來有些不同表示名稱出現，例如 `Editable Text Configuration` 或 `Extended Tool Chest` |
| `/etc/opt`   | 第三方軟體設定檔                                             |
| `/home`      | 使用者家目錄，包含儲存檔案、個人設定                           |
| `/mnt`       | 臨時掛載檔案系統                                             |
| `/opt`       | 第三方軟體                                                   |
| `/proc`      | 虛擬檔案系統，將核心與行程資訊用檔案表示                      |
| `/sbin`      | 系統管理工具和指令，像是 `fdisk`, `mount`                     |
| `/sys`       | 包含硬體、驅動和核心的資訊                                    |
| `/tmp`       | 暫時存放檔案的目錄，系統重新啟動時目錄中的檔案不會被保留      |
| `/usr`       | 存放使用者安裝的程式或工具，資料是 `read-only` 和 `shareable` |
| `/usr/bin`   | 所有使用者可執行的工具和指令                                 |
| `/usr/local` | 升級或額外安裝的程式擺放的目錄，以區分原始系統安裝的程式      |
| `/var`       | 系統、服務或程式執行時的資料和日誌                            |
| `/var/cache` | 系統、服務或程式的快取資料                                    |
| `/var/log`   | 日誌檔案存放路徑                                             |
| `/var/mail`  | 使用者電子信箱                                               |
| `/var/spool` | 等待處理的任務的離線檔案，像是列印佇列、未讀信件               |
| `/var/tmp`   | 暫時存放檔案的目錄，在系統重新啟動過程中目錄中的檔案會被保留  |

## 參考資源

[Filesystem Hierarchy Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
