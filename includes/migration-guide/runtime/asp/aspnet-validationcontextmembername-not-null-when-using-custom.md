---
ms.openlocfilehash: c0be08023f80bf0f96cc08f34b9ea8c5a73839e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77466010"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>使用自訂 DataAnnotations.ValidationAttribute 時 ASP.NET ValidationContext.MemberName 不是 NULL

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7.2 和更早版本中使用自訂 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> 時，<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> 屬性會傳回 `null`。 在 2019 年 10 月更新前的 .NET Framework 4.8 版本中，它返回成員名稱。 從[.NET 框架 2019 年 10 月預覽](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/).NET Framework `null` 4.8 開始，預設情況下返回該預覽，但您可以選擇返回成員名稱。 |
|建議|將以下設置添加到*Web.config*檔中，以便屬性在[.NET Framework 2019 年 10 月為 .NET](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) Framework 4.8 和更高版本返回成員名稱：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>在 2019 年 10 月更新之前的 .NET Framework 4.8 版本中，將其添加到*Web.config* `null`檔將恢復以前的行為，屬性返回 。|
|影響範圍|Unknown|
|版本|4.8|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
