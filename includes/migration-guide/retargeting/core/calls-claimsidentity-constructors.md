---
ms.openlocfilehash: b88f7d4a17f885b687d99ab9410a56039e176080
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614324"
---
### <a name="calls-to-claimsidentity-constructors"></a>呼叫 ClaimsIdentity 建構函式

#### <a name="details"></a>詳細資料

從 .NET Framework 4.6.2 開始，具有 <xref:System.Security.Principal.IIdentity?displayProperty=fullName> 參數的 <xref:System.Security.Claims.ClaimsIdentity> 建構函式如何設定 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 屬性的方法有變更。 如果 <xref:System.Security.Principal.IIdentity?displayProperty=fullName> 引數是 <xref:System.Security.Claims.ClaimsIdentity> 物件，而且該 <xref:System.Security.Claims.ClaimsIdentity> 物件的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 屬性不是 `null`，則會使用 <xref:System.Security.Claims.ClaimsIdentity.Clone> 方法來附加 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 屬性。 在 Framework 4.6.1 和更早版本中，<xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 屬性會附加作為現有的參考。由於此項變更，從 .NET Framework 4.6.2 開始，新 <xref:System.Security.Claims.ClaimsIdentity> 物件的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 屬性便不等於建構函式之 <xref:System.Security.Principal.IIdentity?displayProperty=fullName> 引數的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> 屬性。 在 .NET Framework 4.6.1 和更早版本中，它是相等的。

#### <a name="suggestion"></a>建議

如果不想要這種行為，您可以將應用程式組態檔中的 `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` 參數設為 `true` 來還原舊版行為。 您會需要將下列內容新增至 web.config 檔案的 `<runtime>` 區段︰

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />
  </runtime>
</configuration>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.6.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)>
