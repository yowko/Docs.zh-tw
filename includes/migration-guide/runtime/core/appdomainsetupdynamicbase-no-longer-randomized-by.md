---
ms.openlocfilehash: 08ad6fd4ccb6d5ddbbb4fa7ef1b325ce30689748
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621125"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a><span data-ttu-id="4b532-101">AppDomainSetup.DynamicBase 不再由 UseRandomizedStringHashAlgorithm 隨機化</span><span class="sxs-lookup"><span data-stu-id="4b532-101">AppDomainSetup.DynamicBase is no longer randomized by UseRandomizedStringHashAlgorithm</span></span>

#### <a name="details"></a><span data-ttu-id="4b532-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4b532-102">Details</span></span>

<span data-ttu-id="4b532-103">在 .NET Framework 4.6 之前，如果已在應用程式組態檔中啟用 UseRandomizedStringHashAlgorithm，<xref:System.AppDomainSetup.DynamicBase> 的值就會在應用程式定義域或處理序之間隨機化。</span><span class="sxs-lookup"><span data-stu-id="4b532-103">Prior to the .NET Framework 4.6, the value of <xref:System.AppDomainSetup.DynamicBase> would be randomized between application domains, or between processes, if UseRandomizedStringHashAlgorithm was enabled in the app's config file.</span></span> <span data-ttu-id="4b532-104">從 .NET Framework 4.6 開始，<xref:System.AppDomainSetup.DynamicBase> 將會在執行之應用程式的不同執行個體之間以及不同的應用程式定義域之間，傳回穩定的結果。</span><span class="sxs-lookup"><span data-stu-id="4b532-104">Beginning in the .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> will return a stable result between different instances of an app running, and between different app domains.</span></span> <span data-ttu-id="4b532-105">動態基底仍會因不同的應用程式而異；這項變更只會移除相同應用程式之不同執行個體的隨機命名項目。</span><span class="sxs-lookup"><span data-stu-id="4b532-105">Dynamic bases will still differ for different apps; this change only removes the random naming element for different instances of the same app.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4b532-106">建議</span><span class="sxs-lookup"><span data-stu-id="4b532-106">Suggestion</span></span>

<span data-ttu-id="4b532-107">請注意，啟用 <code>UseRandomizedStringHashAlgorithm</code> 不會導致 <xref:System.AppDomainSetup.DynamicBase> 隨機化。</span><span class="sxs-lookup"><span data-stu-id="4b532-107">Be aware that enabling <code>UseRandomizedStringHashAlgorithm</code> will not result in <xref:System.AppDomainSetup.DynamicBase> being randomized.</span></span> <span data-ttu-id="4b532-108">如果需要隨機基底，必須在您的應用程式程式碼中產生它，而不是透過此 API 產生。</span><span class="sxs-lookup"><span data-stu-id="4b532-108">If a random base is needed, it must be produced in your app's code rather than via this API.</span></span>

| <span data-ttu-id="4b532-109">名稱</span><span class="sxs-lookup"><span data-stu-id="4b532-109">Name</span></span>    | <span data-ttu-id="4b532-110">值</span><span class="sxs-lookup"><span data-stu-id="4b532-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4b532-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="4b532-111">Scope</span></span>   |<span data-ttu-id="4b532-112">Edge</span><span class="sxs-lookup"><span data-stu-id="4b532-112">Edge</span></span>|
|<span data-ttu-id="4b532-113">版本</span><span class="sxs-lookup"><span data-stu-id="4b532-113">Version</span></span>|<span data-ttu-id="4b532-114">4.6</span><span class="sxs-lookup"><span data-stu-id="4b532-114">4.6</span></span>|
|<span data-ttu-id="4b532-115">類型</span><span class="sxs-lookup"><span data-stu-id="4b532-115">Type</span></span>|<span data-ttu-id="4b532-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="4b532-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4b532-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4b532-117">Affected APIs</span></span>

-<xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
