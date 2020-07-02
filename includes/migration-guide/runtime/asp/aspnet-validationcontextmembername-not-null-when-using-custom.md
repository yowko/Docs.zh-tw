---
ms.openlocfilehash: 7002c74594993ac6bf28643ef3271da356190c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621945"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a><span data-ttu-id="8c4b9-101">使用自訂 DataAnnotations.ValidationAttribute 時 ASP.NET ValidationContext.MemberName 不是 NULL</span><span class="sxs-lookup"><span data-stu-id="8c4b9-101">ASP.NET ValidationContext.MemberName is not NULL when using custom DataAnnotations.ValidationAttribute</span></span>

#### <a name="details"></a><span data-ttu-id="8c4b9-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8c4b9-102">Details</span></span>

<span data-ttu-id="8c4b9-103">在 .NET Framework 4.7.2 和更早版本中使用自訂 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> 時，<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> 屬性會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-103">In .NET Framework 4.7.2 and earlier versions, when using a custom <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, the <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> property returns `null`.</span></span> <span data-ttu-id="8c4b9-104">在2019年10月更新之前的 .NET Framework 4.8 版本中，它會傳回成員名稱。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-104">In .NET Framework 4.8 version prior to the October 2019 update, it returns the member name.</span></span> <span data-ttu-id="8c4b9-105">從 .NET Framework 4.8 的[品質匯總 .NET Framework 2019 年10月預覽](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/)版本開始， `null` 預設會傳回，但您可以選擇改為傳回成員名稱。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-105">Starting with [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8, it returns `null` by default, but you can opt in to return the member name instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8c4b9-106">建議</span><span class="sxs-lookup"><span data-stu-id="8c4b9-106">Suggestion</span></span>

<span data-ttu-id="8c4b9-107">將下列設定新增至您的*web.config*檔案，以讓屬性在[2019 年10月的品質匯總預覽](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/)中，傳回 .NET Framework 4.8 和更新版本的成員名稱 .NET Framework：</span><span class="sxs-lookup"><span data-stu-id="8c4b9-107">Add the following setting to your *web.config* file for the property to return the member name in [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8 and later versions:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="8c4b9-108">在2019年10月更新之前的 .NET Framework 4.8 版本中，將此新增至您的*web.config*檔會還原先前的行為，而屬性會傳回 `null` 。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-108">In .NET Framework 4.8 version prior to the October 2019 update,  adding this to your *web.config* file restores the previous behavior and the property returns `null`.</span></span>

| <span data-ttu-id="8c4b9-109">名稱</span><span class="sxs-lookup"><span data-stu-id="8c4b9-109">Name</span></span>    | <span data-ttu-id="8c4b9-110">值</span><span class="sxs-lookup"><span data-stu-id="8c4b9-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8c4b9-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="8c4b9-111">Scope</span></span>   |<span data-ttu-id="8c4b9-112">Unknown</span><span class="sxs-lookup"><span data-stu-id="8c4b9-112">Unknown</span></span>|
|<span data-ttu-id="8c4b9-113">版本</span><span class="sxs-lookup"><span data-stu-id="8c4b9-113">Version</span></span>|<span data-ttu-id="8c4b9-114">4.8</span><span class="sxs-lookup"><span data-stu-id="8c4b9-114">4.8</span></span>|
|<span data-ttu-id="8c4b9-115">類型</span><span class="sxs-lookup"><span data-stu-id="8c4b9-115">Type</span></span>|<span data-ttu-id="8c4b9-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="8c4b9-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8c4b9-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8c4b9-117">Affected APIs</span></span>

-<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
