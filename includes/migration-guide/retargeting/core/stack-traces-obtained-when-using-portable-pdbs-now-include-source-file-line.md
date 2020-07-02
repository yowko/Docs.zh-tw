---
ms.openlocfilehash: c7500550cd9714a9788a7dea68af04823f000f7f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614376"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>使用可攜式 PDB 時取得的堆疊追蹤，現已包含來源檔案與程式碼資訊 (若要求)

#### <a name="details"></a>詳細資料

從 .NET Framework 4.7.2 開始，如果要求，使用可攜式 PDB 時取得的堆疊追蹤會包含來源檔案與程式碼資訊。 在 .NET Framework 4.7.2 之前的版本中，即使明確要求，使用可攜式 PDB 時也無法取得來源檔案和程式碼資訊。

#### <a name="suggestion"></a>建議

若為以 .NET Framework 4.7.2 為目標的應用程式，如果不需要，您可以透過將下列內容新增至 `app.config` 檔案的 `<runtime>` 區段，選擇使用可攜式 PDB 時不包含來源檔案和程式碼資訊︰

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true" />
</runtime>
```

若為以舊版 .NET Framework 為目標但卻在 .NET Framework 4.7.2 或更新版本上執行的應用程式，則可將下列內容新增至 `app.config` 檔案的 `<runtime>` 區段，選擇使用可攜式 PDB 時包含來源檔案和程式碼資訊︰

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false" />
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)>
