---
ms.openlocfilehash: 7002c74594993ac6bf28643ef3271da356190c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621945"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>使用自訂 DataAnnotations.ValidationAttribute 時 ASP.NET ValidationContext.MemberName 不是 NULL

#### <a name="details"></a>詳細資料

在 .NET Framework 4.7.2 和更早版本中使用自訂 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> 時，<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> 屬性會傳回 `null`。 在2019年10月更新之前的 .NET Framework 4.8 版本中，它會傳回成員名稱。 從 .NET Framework 4.8 的[品質匯總 .NET Framework 2019 年10月預覽](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/)版本開始， `null` 預設會傳回，但您可以選擇改為傳回成員名稱。

#### <a name="suggestion"></a>建議

將下列設定新增至您的*web.config*檔案，以讓屬性在[2019 年10月的品質匯總預覽](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/)中，傳回 .NET Framework 4.8 和更新版本的成員名稱 .NET Framework：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>在2019年10月更新之前的 .NET Framework 4.8 版本中，將此新增至您的*web.config*檔會還原先前的行為，而屬性會傳回 `null` 。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Unknown|
|版本|4.8|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
