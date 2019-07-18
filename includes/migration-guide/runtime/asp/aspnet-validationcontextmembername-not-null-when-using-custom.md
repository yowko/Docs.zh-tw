---
ms.openlocfilehash: df13f6938ebaf8e96bb2825c1495044621f1c31b
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802690"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>使用自訂 DataAnnotations.ValidationAttribute 時 ASP.NET ValidationContext.MemberName 不是 NULL

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7.2 和更早版本中使用自訂 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> 時，<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> 屬性會傳回 <code>null</code>。  在 .NET Framework 4.8 中，該屬性會傳回成員名稱。|
|建議|<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> 屬性的預設行為維持不變。  若要從 <code>ValidationContext.MemberName</code> 屬性擷取有效的值，請將下列設定新增至應用程式組態檔：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|不明|
|版本|4.8|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|

