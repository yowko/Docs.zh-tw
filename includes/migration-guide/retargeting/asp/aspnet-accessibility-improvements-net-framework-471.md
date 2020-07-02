---
ms.openlocfilehash: 418bcdca1e9a325894891d7b0e080ce035e2d1b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614337"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>.NET Framework 4.7.1 中的 ASP.NET 協助工具改進功能

#### <a name="details"></a>詳細資料

從 .NET Framework 4.7.1 開始，ASP.NET 已經改善 ASP.NET Web 控制項如何搭配 Visual Studio 中的協助工具技術，來更妥善支援 ASP.NET 客戶。  這些包括下列變更：

- 在控制項中，實作遺漏 UI 協助工具模式的變更，例如在 [詳細資料檢視精靈] 的 [新增欄位] 對話方塊或 ListView 精靈的 [設定 ListView] 對話方塊。
- 改善高對比模式顯示的變更，例如資料頁面巡覽區欄位編輯器。
- 改善控制項鍵盤瀏覽體驗的變更，例如 DataPager 控制項 [編輯頁面巡覽區欄位精靈] 的 [欄位] 對話方塊、[設定 ObjectContext] 對話方塊，或 [設定資料來源精靈] 的 [設定資料選取項目] 對話方塊。

#### <a name="suggestion"></a>建議

**如何選擇加入或退出這些變更**：為了讓 Visual Studio 設計工具可受益於這些變更，它必須在 .NET Framework 4.7.1 或更新版本上執行。 Web 應用程式可以由下列任一種方式受益於這些變更：

- 安裝 Visual Studio 2017 15.3 或更新版本中，依預設它會以下列 AppContext 參數支援新的協助工具功能。
- 藉由將 `Switch.UseLegacyAccessibilityFeatures` AppContext 參數新增到 devenv.exe.config 檔案中的 `<runtime>` 區段，並將它設定為 `false`，選擇退出舊版協助工具行為，如下列範例所示。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
<runtime>
...
<!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
...
</runtime>
</configuration>
```

以 .NET Framework 4.7.1 或更新版本為目標，並且想要保留舊版協助工具行為的應用程式，可以藉由明確將此 AppContext 參數設為 `true`，選擇加入舊版的協助工具功能。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.7.1       |
| 類型    | 正在重定目標 |
