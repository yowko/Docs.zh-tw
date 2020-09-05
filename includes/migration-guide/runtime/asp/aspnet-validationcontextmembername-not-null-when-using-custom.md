---
ms.openlocfilehash: 904a6abee2b4b2cf2f5727fb70e286c8a1a592c4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496745"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a><span data-ttu-id="ac8e4-101">使用自訂 DataAnnotations.ValidationAttribute 時 ASP.NET ValidationContext.MemberName 不是 NULL</span><span class="sxs-lookup"><span data-stu-id="ac8e4-101">ASP.NET ValidationContext.MemberName is not NULL when using custom DataAnnotations.ValidationAttribute</span></span>

#### <a name="details"></a><span data-ttu-id="ac8e4-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ac8e4-102">Details</span></span>

<span data-ttu-id="ac8e4-103">在 .NET Framework 4.7.2 和更早版本中使用自訂 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> 時，<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> 屬性會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="ac8e4-103">In .NET Framework 4.7.2 and earlier versions, when using a custom <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, the <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> property returns `null`.</span></span> <span data-ttu-id="ac8e4-104">在2019年10月更新之前 .NET Framework 4.8 版中，它會傳回成員名稱。</span><span class="sxs-lookup"><span data-stu-id="ac8e4-104">In .NET Framework 4.8 version prior to the October 2019 update, it returns the member name.</span></span> <span data-ttu-id="ac8e4-105">從 [2019 年10月 .NET Framework .NET Framework 4.8 的品質匯總預覽版](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) 開始，預設會傳回 `null` ，但您可以改為選擇改回傳回成員名稱。</span><span class="sxs-lookup"><span data-stu-id="ac8e4-105">Starting with [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8, it returns `null` by default, but you can opt in to return the member name instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ac8e4-106">建議</span><span class="sxs-lookup"><span data-stu-id="ac8e4-106">Suggestion</span></span>

<span data-ttu-id="ac8e4-107">將下列設定新增至您的 *web.config* 檔案，以在 [2019 年10月 .NET Framework](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) .NET Framework 4.8 和更新版本的品質匯總預覽版本中傳回成員名稱：</span><span class="sxs-lookup"><span data-stu-id="ac8e4-107">Add the following setting to your *web.config* file for the property to return the member name in [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8 and later versions:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="ac8e4-108">在2019年10月更新之前的 .NET Framework 4.8 版本中，將其新增至您的 *web.config* 檔會還原先前的行為，而屬性會傳回 `null` 。</span><span class="sxs-lookup"><span data-stu-id="ac8e4-108">In .NET Framework 4.8 version prior to the October 2019 update,  adding this to your *web.config* file restores the previous behavior and the property returns `null`.</span></span>

| <span data-ttu-id="ac8e4-109">名稱</span><span class="sxs-lookup"><span data-stu-id="ac8e4-109">Name</span></span>    | <span data-ttu-id="ac8e4-110">值</span><span class="sxs-lookup"><span data-stu-id="ac8e4-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ac8e4-111">範圍</span><span class="sxs-lookup"><span data-stu-id="ac8e4-111">Scope</span></span>   |<span data-ttu-id="ac8e4-112">未知</span><span class="sxs-lookup"><span data-stu-id="ac8e4-112">Unknown</span></span>|
|<span data-ttu-id="ac8e4-113">版本</span><span class="sxs-lookup"><span data-stu-id="ac8e4-113">Version</span></span>|<span data-ttu-id="ac8e4-114">4.8</span><span class="sxs-lookup"><span data-stu-id="ac8e4-114">4.8</span></span>|
|<span data-ttu-id="ac8e4-115">類型</span><span class="sxs-lookup"><span data-stu-id="ac8e4-115">Type</span></span>|<span data-ttu-id="ac8e4-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="ac8e4-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ac8e4-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ac8e4-117">Affected APIs</span></span>

- <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.ComponentModel.DataAnnotations.ValidationContext.MemberName`

-->
