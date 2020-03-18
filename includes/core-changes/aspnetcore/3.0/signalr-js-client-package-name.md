---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901762"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="26454-101">信號R：JavaScript用戶端包名稱已更改</span><span class="sxs-lookup"><span data-stu-id="26454-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="26454-102">在ASP.NET酷3.0預覽7中，SignalR JavaScript用戶端包名稱從`@aspnet/signalr`更改為`@microsoft/signalr`。</span><span class="sxs-lookup"><span data-stu-id="26454-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="26454-103">名稱更改反映了一個事實，即由於 Azure SignalR 服務，SignalR 不僅在 ASP.NET 核心應用中非常有用。</span><span class="sxs-lookup"><span data-stu-id="26454-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="26454-104">要對此更改做出反應，請更改*包.json*檔、`require`語句和 ECMAScript`import`語句中的引用。</span><span class="sxs-lookup"><span data-stu-id="26454-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="26454-105">作為此重命名的一部分，任何 API 都不會改變。</span><span class="sxs-lookup"><span data-stu-id="26454-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="26454-106">有關討論，請參閱[點網/阿斯平核心#11637](https://github.com/dotnet/aspnetcore/issues/11637)。</span><span class="sxs-lookup"><span data-stu-id="26454-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="26454-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="26454-107">Version introduced</span></span>

<span data-ttu-id="26454-108">3.0</span><span class="sxs-lookup"><span data-stu-id="26454-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="26454-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="26454-109">Old behavior</span></span>

<span data-ttu-id="26454-110">用戶端包已命名`@aspnet/signalr`。</span><span class="sxs-lookup"><span data-stu-id="26454-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="26454-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="26454-111">New behavior</span></span>

<span data-ttu-id="26454-112">用戶端包名為`@microsoft/signalr`。</span><span class="sxs-lookup"><span data-stu-id="26454-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="26454-113">更改原因</span><span class="sxs-lookup"><span data-stu-id="26454-113">Reason for change</span></span>

<span data-ttu-id="26454-114">名稱更改闡明，由於 Azure SignalR 服務，SignalR 在 ASP.NET 核心應用之外非常有用。</span><span class="sxs-lookup"><span data-stu-id="26454-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="26454-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="26454-115">Recommended action</span></span>

<span data-ttu-id="26454-116">切換到新包`@microsoft/signalr`。</span><span class="sxs-lookup"><span data-stu-id="26454-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="26454-117">類別</span><span class="sxs-lookup"><span data-stu-id="26454-117">Category</span></span>

<span data-ttu-id="26454-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="26454-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="26454-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="26454-119">Affected APIs</span></span>

<span data-ttu-id="26454-120">None</span><span class="sxs-lookup"><span data-stu-id="26454-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
