---
ms.openlocfilehash: f221f923381d874e1d9e8b420811a770d86f7578
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858415"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a><span data-ttu-id="ce116-101">預設應用程式定義域的 TargetFrameworkName 若未設定，不會再預設為 Null</span><span class="sxs-lookup"><span data-stu-id="ce116-101">TargetFrameworkName for default app domain no longer defaults to null if not set</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ce116-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ce116-102">Details</span></span>|<span data-ttu-id="ce116-103">除非明確設定，否則 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> 之前在預設應用程式定義域中為 Null。</span><span class="sxs-lookup"><span data-stu-id="ce116-103">The <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> was previously null in the default app domain, unless it was explicitly set.</span></span> <span data-ttu-id="ce116-104">從 4.6 開始，預設應用程式定義域的 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> 屬性會有衍生自 TargetFrameworkAttribute 的預設值 (如果有一個預設值的話)。</span><span class="sxs-lookup"><span data-stu-id="ce116-104">Beginning in 4.6, the <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> property for the default app domain will have a default value derived from the TargetFrameworkAttribute (if one is present).</span></span> <span data-ttu-id="ce116-105">除非明確遭到覆寫，否則非預設應用程式定義域會繼續從預設應用程式定義域繼承其 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> (在 4.6 中不會預設為 Null)。</span><span class="sxs-lookup"><span data-stu-id="ce116-105">Non-default app domains will continue to inherit their <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> from the default app domain (which will not default to null in 4.6) unless it is explicitly overridden.</span></span>|
|<span data-ttu-id="ce116-106">建議</span><span class="sxs-lookup"><span data-stu-id="ce116-106">Suggestion</span></span>|<span data-ttu-id="ce116-107">您應該更新程式碼，讓 <xref:System.AppDomainSetup.TargetFrameworkName> 不會預設為 Null。</span><span class="sxs-lookup"><span data-stu-id="ce116-107">Code should be updated to not depend on <xref:System.AppDomainSetup.TargetFrameworkName> defaulting to null.</span></span> <span data-ttu-id="ce116-108">如果此屬性必須繼續評估為 Null，則可以將它明確設定為該值。</span><span class="sxs-lookup"><span data-stu-id="ce116-108">If it is required that this property continue to evaluate to null, it can be explicitly set to that value.</span></span>|
|<span data-ttu-id="ce116-109">範圍</span><span class="sxs-lookup"><span data-stu-id="ce116-109">Scope</span></span>|<span data-ttu-id="ce116-110">Edge</span><span class="sxs-lookup"><span data-stu-id="ce116-110">Edge</span></span>|
|<span data-ttu-id="ce116-111">版本</span><span class="sxs-lookup"><span data-stu-id="ce116-111">Version</span></span>|<span data-ttu-id="ce116-112">4.6</span><span class="sxs-lookup"><span data-stu-id="ce116-112">4.6</span></span>|
|<span data-ttu-id="ce116-113">類型</span><span class="sxs-lookup"><span data-stu-id="ce116-113">Type</span></span>|<span data-ttu-id="ce116-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="ce116-114">Runtime</span></span>|
|<span data-ttu-id="ce116-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ce116-115">Affected APIs</span></span>|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|

