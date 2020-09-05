---
ms.openlocfilehash: 904a6abee2b4b2cf2f5727fb70e286c8a1a592c4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496745"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>使用自訂 DataAnnotations.ValidationAttribute 時 ASP.NET ValidationContext.MemberName 不是 NULL

#### <a name="details"></a>詳細資料

在 .NET Framework 4.7.2 和更早版本中使用自訂 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> 時，<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> 屬性會傳回 `null`。 在2019年10月更新之前 .NET Framework 4.8 版中，它會傳回成員名稱。 從 [2019 年10月 .NET Framework .NET Framework 4.8 的品質匯總預覽版](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) 開始，預設會傳回 `null` ，但您可以改為選擇改回傳回成員名稱。

#### <a name="suggestion"></a>建議

將下列設定新增至您的 *web.config* 檔案，以在 [2019 年10月 .NET Framework](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) .NET Framework 4.8 和更新版本的品質匯總預覽版本中傳回成員名稱：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>在2019年10月更新之前的 .NET Framework 4.8 版本中，將其新增至您的 *web.config* 檔會還原先前的行為，而屬性會傳回 `null` 。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |未知|
|版本|4.8|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.ComponentModel.DataAnnotations.ValidationContext.MemberName`

-->
