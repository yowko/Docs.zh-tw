---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901762"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="987e0-101">SignalR： JavaScript 用戶端封裝名稱已變更</span><span class="sxs-lookup"><span data-stu-id="987e0-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="987e0-102">在 ASP.NET Core 3.0 Preview 7 中，SignalR JavaScript 用戶端封裝名稱從 `@aspnet/signalr` 變更為 `@microsoft/signalr`。</span><span class="sxs-lookup"><span data-stu-id="987e0-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="987e0-103">名稱變更反映出 SignalR 在不只是 ASP.NET Core 的應用程式中很有用的事實，因為 Azure SignalR Service。</span><span class="sxs-lookup"><span data-stu-id="987e0-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="987e0-104">若要回應這項變更，請變更您*封裝*中的參考、`require` 語句和 ECMAScript `import` 語句。</span><span class="sxs-lookup"><span data-stu-id="987e0-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="987e0-105">在此重新命名過程中，不會變更任何 API。</span><span class="sxs-lookup"><span data-stu-id="987e0-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="987e0-106">如需討論，請參閱[dotnet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637)。</span><span class="sxs-lookup"><span data-stu-id="987e0-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="987e0-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="987e0-107">Version introduced</span></span>

<span data-ttu-id="987e0-108">3.0</span><span class="sxs-lookup"><span data-stu-id="987e0-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="987e0-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="987e0-109">Old behavior</span></span>

<span data-ttu-id="987e0-110">用戶端套件的名稱為 `@aspnet/signalr`。</span><span class="sxs-lookup"><span data-stu-id="987e0-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="987e0-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="987e0-111">New behavior</span></span>

<span data-ttu-id="987e0-112">用戶端套件的名稱為 `@microsoft/signalr`。</span><span class="sxs-lookup"><span data-stu-id="987e0-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="987e0-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="987e0-113">Reason for change</span></span>

<span data-ttu-id="987e0-114">[名稱] 變更清楚說明 SignalR 在 ASP.NET Core 應用程式之外很有用，因為 Azure SignalR Service。</span><span class="sxs-lookup"><span data-stu-id="987e0-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="987e0-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="987e0-115">Recommended action</span></span>

<span data-ttu-id="987e0-116">切換至新的封裝 `@microsoft/signalr`。</span><span class="sxs-lookup"><span data-stu-id="987e0-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="987e0-117">分類</span><span class="sxs-lookup"><span data-stu-id="987e0-117">Category</span></span>

<span data-ttu-id="987e0-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="987e0-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="987e0-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="987e0-119">Affected APIs</span></span>

<span data-ttu-id="987e0-120">None</span><span class="sxs-lookup"><span data-stu-id="987e0-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
