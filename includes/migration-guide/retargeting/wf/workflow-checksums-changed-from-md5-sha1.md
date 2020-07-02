---
ms.openlocfilehash: 72d48d1daa85b6891c122f2fcc5279642253b926
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614388"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>工作流程總和檢查碼從 MD5 變更為 SHA1

#### <a name="details"></a>詳細資料

為了支援使用 Visual Studio 進行偵錯，工作流程執行階段會使用雜湊演算法為工作流程執行個體產生總和檢查碼。 在 .NET Framework 4.6.2 和更早版本中，工作流程總和檢查碼雜湊使用 MD5 演算法，它會在啟用 FIPS 的系統上造成問題。 從 .NET Framework 4.7 開始，演算法是 SHA1。 如果您的程式碼已保存這些總和檢查碼，就會不相容。

#### <a name="suggestion"></a>建議

如果您的程式碼因為總和檢查碼失敗而無法載入工作流程執行個體，請嘗試將 `AppContext` 參數 &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; 設為 true。在程式碼中：

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseMD5ForWFDebugger", true);
```

或者，在組態中：

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseMD5ForWFDebugger=true" />
  </runtime>
</configuration>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.7         |
| 類型    | 正在重定目標 |
