---
ms.openlocfilehash: df13f6938ebaf8e96bb2825c1495044621f1c31b
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802690"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a><span data-ttu-id="5a8f4-101">使用自訂 DataAnnotations.ValidationAttribute 時 ASP.NET ValidationContext.MemberName 不是 NULL</span><span class="sxs-lookup"><span data-stu-id="5a8f4-101">ASP.NET ValidationContext.MemberName is not NULL when using custom DataAnnotations.ValidationAttribute</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5a8f4-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5a8f4-102">Details</span></span>|<span data-ttu-id="5a8f4-103">在 .NET Framework 4.7.2 和更早版本中使用自訂 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> 時，<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> 屬性會傳回 <code>null</code>。</span><span class="sxs-lookup"><span data-stu-id="5a8f4-103">In .NET Framework 4.7.2 and earlier versions, when using a custom <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, the <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> property returns <code>null</code>.</span></span>  <span data-ttu-id="5a8f4-104">在 .NET Framework 4.8 中，該屬性會傳回成員名稱。</span><span class="sxs-lookup"><span data-stu-id="5a8f4-104">In .NET Framework 4.8, it returns the member name.</span></span>|
|<span data-ttu-id="5a8f4-105">建議</span><span class="sxs-lookup"><span data-stu-id="5a8f4-105">Suggestion</span></span>|<span data-ttu-id="5a8f4-106"><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> 屬性的預設行為維持不變。</span><span class="sxs-lookup"><span data-stu-id="5a8f4-106">The default behavior of the <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> property remains the same.</span></span>  <span data-ttu-id="5a8f4-107">若要從 <code>ValidationContext.MemberName</code> 屬性擷取有效的值，請將下列設定新增至應用程式組態檔：</span><span class="sxs-lookup"><span data-stu-id="5a8f4-107">To retrieve a valid value from the <code>ValidationContext.MemberName</code> property, add the following setting to your app config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="5a8f4-108">範圍</span><span class="sxs-lookup"><span data-stu-id="5a8f4-108">Scope</span></span>|<span data-ttu-id="5a8f4-109">不明</span><span class="sxs-lookup"><span data-stu-id="5a8f4-109">Unknown</span></span>|
|<span data-ttu-id="5a8f4-110">版本</span><span class="sxs-lookup"><span data-stu-id="5a8f4-110">Version</span></span>|<span data-ttu-id="5a8f4-111">4.8</span><span class="sxs-lookup"><span data-stu-id="5a8f4-111">4.8</span></span>|
|<span data-ttu-id="5a8f4-112">類型</span><span class="sxs-lookup"><span data-stu-id="5a8f4-112">Type</span></span>|<span data-ttu-id="5a8f4-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="5a8f4-113">Runtime</span></span>|
|<span data-ttu-id="5a8f4-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5a8f4-114">Affected APIs</span></span>|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|

