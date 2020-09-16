---
ms.openlocfilehash: 7c4b9faf25853c1c7a546f06c329f6f153eef904
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606943"
---
### <a name="changes-in-path-normalization"></a>路徑正規化的變更

#### <a name="details"></a>詳細資料

從以 .NET Framework 4.6.2 為目標的應用程式開始，執行階段正規化路徑的方式已變更。正規化路徑涉及修改識別路徑或檔案的字串，使它符合目標作業系統上的有效路徑。 正規化通常牽涉到︰

- 規範化元件和目錄分隔符號。
- 將目前的目錄套用到相對路徑。
- 評估路徑中的相對目錄 (.) 或上層目錄 (..)。
- 修剪指定的字元。
從以 .NET Framework 4.6.2 為目標的應用程式開始，預設會啟用路徑正規化的下列變更：
  - 執行階段會延後至作業系統的 [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) 函式再進行路徑正規化。
- 正規化不再涉及修剪目錄區段的結尾 (例如目錄名稱結尾的空格)。
- 支援完全信任的裝置路徑語法，包括 `\\.\` 以及適用於 mscorlib.dll 中之檔案 I/O API 的 `\\?\`。
- 執行階段不會驗證裝置語法路徑。
- 支援使用裝置語法存取替代資料流。
這些變更可改善效能，同時允許方法存取先前無法存取的路徑。 此變更不會影響以 .NET Framework 4.6.1 和舊版為目標但執行於 .NET Framework 4.6.2 或更新版本下的應用程式。

#### <a name="suggestion"></a>建議

以 .NET Framework 4.6.2 或更新版本為目標的應用程式可透過在應用程式設定檔的 `<runtime>` 區段中新增下列內容來選擇退出此變更，並使用舊版行為：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>
```

以 .NET Framework 4.6.1 或更早版本為目標，但在 .NET Framework 4.6.2 或更新版本上執行的應用程式，可以藉由在應用程式設定檔的 `<runtime>` 區段新增下行，就能啟用路徑正規化的變更：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 範圍   | Minor       |
| 版本 | 4.6.2       |
| 類型    | 正在重定目標 |
