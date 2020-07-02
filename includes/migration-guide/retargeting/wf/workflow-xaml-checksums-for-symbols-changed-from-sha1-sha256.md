---
ms.openlocfilehash: 946e71f2f466664c8f9fcf4811288ce693a872eb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617794"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>符號的工作流程 XAML 總和檢查碼從 SHA1 變更為 SHA256

#### <a name="details"></a>詳細資料

為了支援 Visual Studio 偵錯，工作流程執行階段會使用雜湊演算法為工作流程 XAML 檔案產生總和檢查碼。 在 .NET Framework 4.6.2 和更早版本中，工作流程總和檢查碼雜湊使用 MD5 演算法，它會在啟用 FIPS 的系統上造成問題。 從 .NET Framework 4.7 開始，預設的演算法已變更為 SHA1。 從 .NET Framework 4.8 開始，預設的演算法已變更為 SHA256。

#### <a name="suggestion"></a>建議

如果您的程式碼因為總和檢查碼失敗而無法載入工作流程實例或尋找適當的符號，請嘗試將參數設定為「 `AppContext` Switch.System。UseSHA1HashForDebuggerSymbols "to `true` 。 在程式碼中：

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseSHA1HashForDebuggerSymbols", true);
```

或者，在組態中：

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true" />
  </runtime>
</configuration>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.8         |
| 類型    | 正在重定目標 |
