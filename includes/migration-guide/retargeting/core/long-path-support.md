---
ms.openlocfilehash: 67e3ff5000ebd38064ed8a57e4fe561afa31f8d8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614348"
---
### <a name="long-path-support"></a>長路徑支援

#### <a name="details"></a>詳細資料

從以 .NET Framework 4.6.2 為目標的應用程式開始，支援長路徑 (最多 32K 個字元)，且已移除對於路徑長度的 260 個字元 (或 `MAX_PATH`) 限制。若為重新編譯以 .NET Framework 4.6.2 為目標的應用程式，先前因為路徑超過 260 個字元而擲回 <xref:System.IO.PathTooLongException?displayProperty=fullName> 的程式碼路徑，現在將只有在下列情況下擲回 <xref:System.IO.PathTooLongException?displayProperty=fullName>：

- 路徑的長度大於 <xref:System.Int16.MaxValue> (32,767) 個字元。
- 作業系統傳回 `COR_E_PATHTOOLONG` 或其對應項。
若為以 .NET Framework 4.6.1 和更早版本為目標的應用程式，每當路徑超過 260 個字元時，執行階段就會自動擲回 <xref:System.IO.PathTooLongException?displayProperty=fullName>。

#### <a name="suggestion"></a>建議

若為以 .NET Framework 4.6.2 為目標的應用程式，如果不需要長路徑支援，您可以透過將下列內容新增至 `app.config` 檔案的 `<runtime>` 區段以選擇退出長路徑支援︰

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />
</runtime>
```

若為以舊版 .NET Framework 為目標但卻在 .NET Framework 4.6.2 或更新版本上執行的應用程式，則可將下列內容新增至 `app.config` 檔案的 `<runtime>` 區段，以選擇加入長路徑支援：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.6.2       |
| 類型    | 正在重定目標 |
