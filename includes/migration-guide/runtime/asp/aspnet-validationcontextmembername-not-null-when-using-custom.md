---
ms.openlocfilehash: 3b94c88809513e31a5f226bcfce39abbfa4de378
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017368"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>使用自訂 DataAnnotations.ValidationAttribute 時 ASP.NET ValidationContext.MemberName 不是 NULL

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7.2 和更早版本中使用自訂 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> 時，<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> 屬性會傳回 <code>null</code>。  在 .NET Framework 4.8 中，該屬性會傳回成員名稱。|
|建議|若要還原先前的行為，請將下列設定新增至應用程式組態檔：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>此行為會在即將推出的服務版本中變更，到時您必須明確加入到新行為。 如果 `aspnet:GetValidationMemberName` 參數設定為 `true`，則此屬性會傳回自訂 `ValidationAttribute` 的非 Null 值。|
|範圍|不明|
|版本|4.8|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
