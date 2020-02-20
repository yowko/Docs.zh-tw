---
ms.openlocfilehash: c0be08023f80bf0f96cc08f34b9ea8c5a73839e3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77466010"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>使用自訂 DataAnnotations.ValidationAttribute 時 ASP.NET ValidationContext.MemberName 不是 NULL

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7.2 和更早版本中使用自訂 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> 時，<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> 屬性會傳回 `null`。 在2019年10月更新之前的 .NET Framework 4.8 版本中，它會傳回成員名稱。 從 .NET Framework 4.8 的[品質匯總 .NET Framework 2019 年10月預覽](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/)版本開始，它預設會傳回 `null`，但是您可以改為選擇傳回成員名稱。 |
|建議|將下列設定新增至您的*web.config*檔案，以讓屬性在 .NET Framework 4.8 和更新版本的[品質匯總 .NET Framework 2019 年10月預覽](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/)中傳回成員名稱：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>在2019年10月更新之前的 .NET Framework 4.8 版本中，將此新增*至 web.config 檔案*會還原先前的行為，而屬性會傳回 `null`。|
|影響範圍|Unknown|
|版本|4.8|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
