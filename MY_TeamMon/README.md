# 茗伊插件自定義團隊監控數據

> 這是《劍網3》茗伊插件自定義團隊監控數據項目，通過該項目可在遊戲中快速加載自定義團隊監控數據項。

## 文件結構

 * 二級目錄對應遊戲語言如 `zhcn`、`zhtw`。
 * 三級目錄則包含一個 `meta.json` 描述文件存儲版本號和信息用於客戶端緩存，包含一個數據文件用於實際加載。

## 描述文件

> 描述文件 `meta.json` 要求

 * 編碼方式必須為 `UTF-8` 否則會出現亂碼問題。

> 描述文件 `meta.json` 包含字段

 * `name`： 數據標題，用於在列表中展示。
 * `author`： 作者名稱，用於在列表中展示。
 * `version`： 版本號，用於遊戲中下載緩存和更新提示。
 * `data_url`： 數據地址，留空則會自動搜索同目錄下 `data.jx3dat` 文件，注意文件必須是導出的加密格式並且後綴名為 `.jx3dat` 。
 * `about`： 詳細信息地址，用於在遊戲中超鏈接跳轉。

## 數據文件

> 數據文件 `data.jx3dat` 要求

 * 數據必須是導出的加密格式，否則可能出現編碼混亂問題。
 * 後綴名必須為 `.jx3dat` ，如使用其他後綴名則無法直接加載。

## 遊戲使用

依次點擊 `頭像菜單` - `茗伊插件` - `團隊監控` - `系統菜單` - `導入數據（聯網獲取文件）` - `添加訂閱`，然後在彈出輸入框中輸入描述文件地址即可。

其中，描述文件地址支持短鏈接，其格式為：

```
{USERNAME}@{PROVIDER}/{PROJECT}?{BRANCH}:{PATH}
```

> 如果你是普通用戶，只需要找數據作者索要短鏈接地址即可使用，如果你是數據作者，歡迎繼續往下閱讀各項參數的內容。

 * {USERNAME} 為數據作者倉庫賬號英文名稱
 * {PROVIDER} 為數據倉庫所在站點，可選值有 [`github`](https://github.com/tinymins/JX3_MY_DATA)、 [`aliyun`](https://code.aliyun.com/tinymins/JX3_MY_DATA)、 [`gitee`](https://gitee.com/tinymins/JX3_MY_DATA)，默認值為 `github`，各位數據作者可根據自身喜好選擇站點。
 * {PROJECT} 為數據倉庫項目名稱，默認值為 `JX3_MY_DATA`，用於作者有多個數據項目或自定義項目名稱時使用。
 * {BRANCH} 為數據倉庫分支名稱，默認值為 `master`，用於作者數據項目有多個開發進度（如測試服數據）時使用。
 * {PATH} 為數據倉庫描述文件地址，默認值為 `MY_TeamMon/{遊戲語言}/meta.json`，該字段一般不需做特殊修改。

> 示例

```
tinymins
tinymins?master
tinymins/JX3_MY_DATA
tinymins/JX3_MY_DATA?master
tinymins@github
tinymins@github?master
tinymins@github:/MY_TeamMon/zhcn/meta.json
tinymins@github/JX3_MY_DATA
tinymins@github/JX3_MY_DATA:/MY_TeamMon/zhcn/meta.json
tinymins@github/JX3_MY_DATA?master:/MY_TeamMon/zhcn/meta.json
```

在劍網3簡體客戶端中，輸入上述示例短鏈接，均等價於直接輸入如下描述文件地址

```
https://raw.githubusercontent.com/tinymins/JX3_MY_DATA/master/MY_TeamMon/zhcn/meta.json
```

## 自製雲數據

> 開始之前，先根據個人喜好選擇一個站點作為數據倉庫：

 * [`github`](https://github.com/tinymins/JX3_MY_DATA) 默認站點，限制較少，但在國內連接速度不穩，無中文界面。
 * [`aliyun`](https://code.aliyun.com/tinymins/JX3_MY_DATA) 阿里雲倉庫，國內速度較快，訪問倉庫要求用戶登錄，中文界面。
 * [`gitee`](https://gitee.com/tinymins/JX3_MY_DATA) 碼雲倉庫，國內速度較快，訪問倉庫不要求登錄訪問，界面有少許廣告。

> 開始創建自己的倉庫，這裡假設你已製作完成一份數據並從遊戲中導出完成。

1. 選擇上述任何一個倉庫點擊進入，註冊賬號並登錄。
2. 點擊 `Fork` 按鈕（阿里雲顯示為 `派生项目`），生成一個屬於你的派生項目，此時該項目地址為 `https://{站點地址}/{你的用户名}/JX3_MY_DATA`。
3. 進入派生項目，點擊進入對應語言文件夾，如繁體客戶端進入 `JX3_MY_DATA/MY_TeamMon/zhtw/` 目錄（注：阿里雲需先點擊左側 `文件` 標籤頁，進入目錄瀏覽模式）。
4. （使用非阿里雲）點擊 `data.jx3dat` 鏈接進入數據詳情，點擊刪除按鈕點擊提交移除舊版數據。
5. （使用非阿里雲）重複第3步，回到對應語言文件夾，點擊 `Upload files` 按鈕數據上傳界面。
6. （使用阿里雲）點擊 `data.jx3dat` 鏈接進入數據詳情，點擊替換按鈕進入數據替換界面。
7. 將你的數據文件重命名為 `data.jx3dat` 並拖拽到上傳框完成上傳，輸入提交日誌並提交改動。
8. 重複第3步，回到對應語言文件夾，點擊 `meta.json` 進入描述文件，並點擊 `Edit`（阿里雲顯示為 `編輯`） 按鈕開始編輯，修改數據名稱、作者、版本號等信息後，點擊 `Commit`（阿里雲顯示為 `提交修改`） 按鈕保存改動。

至此，你已完成創建並更新了你的自製雲數據，遊戲中可添加描述地址，其格式為 `{你的用户名}@{你選擇的倉庫站點}`，如 ①`tinymins@github`、 ②`tinymins@aliyun`。（注：由於 `github` 是默認站點，所以實際上示例①輸入 `tinymins` 即可）

> 更新數據

重複上述 3 - 8 步驟即可，注意 `步驟 8` 不可提前，因為遊戲內會根據描述文件 `meta.json` 中的版本號做本地數據緩存，如果提前 `步驟 8` 先更新了描述文件，那麼部分用戶在你還沒來及上傳數據時，會下載到錯誤的數據文件。
