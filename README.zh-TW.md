# 末地每週重置腳本

[English](README.md) | **繁體中文**

每週日中午 12:00 自動重置末地：事前廣播倒數、先把末地玩家傳送回主世界，再重新生成末地並宣布新一輪屠龍。附手動重置指令與時間格式測試工具。

> 本儲存庫包含同一個腳本的兩個版本：**繁體中文（zh-TW）** 是作者伺服器實際使用的原始版本；**English** 為完整英文翻譯版（指令、訊息與變數名稱皆為英文），功能相同。

<!-- BEGIN LIVE SCREENSHOTS -->

## 畫面預覽

![下次末地重置資訊](docs/images/end-reset-info.png)

*執行 `/末地下次重置時間` 查看排程。擷取時僅執行此唯讀查詢，並未執行具破壞性、僅限 OP 的重置指令。*

> 這些是實機擷取後重繪的畫面，不是原生客戶端截圖。流程為：無頭客戶端登入實機 Paper 26.2 伺服器觸發腳本，再以官方 Minecraft 26.2 客戶端素材忠實重繪伺服器回傳的方塊／介面資料。Mojang/Microsoft 的圖像資產不屬於本專案程式碼授權範圍。

<!-- END LIVE SCREENSHOTS -->

## 功能特色

- 每週日 11:30、11:50、11:55、11:59 廣播倒數
- 重置前把 `world_the_end` 內的玩家傳送到主世界出生點
- 使用 Multiverse-Core 重新生成末地（`mv regen world_the_end --seed`）
- 玩家可用 `/末地下次重置時間`，管理員可用 `/重置末地`
- 附選用的測試腳本 `/testtime`，可檢查排程所依賴的時間格式

## 需求

- [Paper](https://papermc.io/) 伺服器（開發環境 Paper 26.2 / Minecraft 26.2）
- [Skript](https://github.com/SkriptLang/Skript)（開發環境 2.16.2）
- [Multiverse-Core](https://modrinth.com/plugin/multiverse-core) 5.x，且 `config.yml` 設定 `confirm-mode: disable_console`

## 安裝

1. 先安裝[需求](#需求)中列出的插件。
2. 下載**其中一個**版本：

   | 版本 | 檔案 |
   |---|---|
   | 繁體中文（原始版本） | [`zh-TW/末地每週重置腳本.sk`](zh-TW/%E6%9C%AB%E5%9C%B0%E6%AF%8F%E9%80%B1%E9%87%8D%E7%BD%AE%E8%85%B3%E6%9C%AC.sk)<br>[`zh-TW/測試時間格式腳本.sk`](zh-TW/%E6%B8%AC%E8%A9%A6%E6%99%82%E9%96%93%E6%A0%BC%E5%BC%8F%E8%85%B3%E6%9C%AC.sk) (選用的測試工具) |
   | English（英文） | [`en/weekly-end-reset.sk`](en/weekly-end-reset.sk)<br>[`en/test-time-format.sk`](en/test-time-format.sk) (選用的測試工具) |

3. 把 `.sk` 檔案放進伺服器的 `plugins/Skript/scripts/`。
4. 執行 `/sk reload 末地每週重置腳本`（請換成你放入的檔名），或重新啟動伺服器。

> [!IMPORTANT]
> **只能安裝其中一個版本。** 兩個版本是同一個腳本的不同語言，同時載入會互相衝突或重複執行。

## 指令

| 指令（中文版） | 英文版 | 說明 | 權限 |
|---|---|---|---|
| `/重置末地` | `/resetend` | 立即重置末地 | OP |
| `/末地下次重置時間` | `/endresetinfo` | 查看末地重置資訊 | 所有人 |
| `/testtime` | `/testtime` | 顯示目前的時間與星期格式（測試腳本） | OP |

## 設定

- 世界名稱（`world_the_end`、`world`）、星期（`"Sunday"`）與時間都在 `every minute` 區塊與 `/重置末地` 指令中。

## 注意事項

- 排程是拿 `now formatted as "EEEE"` 與 `"Sunday"` 比對，結果取決於 JVM 語系。請先執行 `/testtime`：若星期不是顯示 `Sunday`（例如顯示 `星期日`），請把腳本中的字串改成 `/testtime` 顯示的內容。
- 時間以伺服器主機的時區為準。
- 測試腳本為選用，確認完畢即可刪除。

## 相關專案

- [skript-end-party-mode](https://github.com/Im-Tim-mI/skript-end-party-mode)－派對遊戲系統（末地派對模式）

## 授權

**MIT + Commons Clause**，完整條款請見 [LICENSE](LICENSE)。

- ✅ 可自由使用、複製、修改與分享本腳本。
- ✅ 本授權明確允許在收費或營利的 Minecraft 伺服器上安裝與運行本插件（含修改版）。
- ❌ 禁止的僅限於直接或間接販售本插件本體、修改版本，或以付費方式取得其檔案或原始碼。

Copyright (c) 2026 廷廷小教室、廷廷的家（Tim945）
