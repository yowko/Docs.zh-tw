---
ms.openlocfilehash: acef6d7177ee5ad7e18dc8ba1e383d6f76263623
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394097"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="820f7-101">SignalR： JavaScript 用戶端封裝名稱已變更</span><span class="sxs-lookup"><span data-stu-id="820f7-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="820f7-102">在 ASP.NET Core 3.0 Preview 7 中，SignalR JavaScript 用戶端封裝名稱從 `@aspnet/signalr` 變更為 `@microsoft/signalr`。</span><span class="sxs-lookup"><span data-stu-id="820f7-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="820f7-103">名稱變更反映出 SignalR 在不只是 ASP.NET Core 的應用程式中很有用的事實，因為 Azure SignalR Service。</span><span class="sxs-lookup"><span data-stu-id="820f7-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="820f7-104">若要回應這項變更，請變更封裝中的*json*檔案、@no__t 1 語句和 ECMAScript @no__t 2 語句中的參考。</span><span class="sxs-lookup"><span data-stu-id="820f7-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="820f7-105">在此重新命名過程中，不會變更任何 API。</span><span class="sxs-lookup"><span data-stu-id="820f7-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="820f7-106">如需討論，請參閱[aspnet/AspNetCore # 11637](https://github.com/aspnet/AspNetCore/issues/11637)。</span><span class="sxs-lookup"><span data-stu-id="820f7-106">For discussion, see [aspnet/AspNetCore#11637](https://github.com/aspnet/AspNetCore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="820f7-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="820f7-107">Version introduced</span></span>

<span data-ttu-id="820f7-108">3.0</span><span class="sxs-lookup"><span data-stu-id="820f7-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="820f7-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="820f7-109">Old behavior</span></span>

<span data-ttu-id="820f7-110">用戶端套件的名稱為 `@aspnet/signalr`。</span><span class="sxs-lookup"><span data-stu-id="820f7-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="820f7-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="820f7-111">New behavior</span></span>

<span data-ttu-id="820f7-112">用戶端套件的名稱為 `@microsoft/signalr`。</span><span class="sxs-lookup"><span data-stu-id="820f7-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="820f7-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="820f7-113">Reason for change</span></span>

<span data-ttu-id="820f7-114">[名稱] 變更清楚說明 SignalR 在 ASP.NET Core 應用程式之外很有用，因為 Azure SignalR Service。</span><span class="sxs-lookup"><span data-stu-id="820f7-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="820f7-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="820f7-115">Recommended action</span></span>

<span data-ttu-id="820f7-116">切換至新的封裝 `@microsoft/signalr`。</span><span class="sxs-lookup"><span data-stu-id="820f7-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="820f7-117">分類</span><span class="sxs-lookup"><span data-stu-id="820f7-117">Category</span></span>

<span data-ttu-id="820f7-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="820f7-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="820f7-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="820f7-119">Affected APIs</span></span>

<span data-ttu-id="820f7-120">無</span><span class="sxs-lookup"><span data-stu-id="820f7-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
