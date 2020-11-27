---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032424"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="9bcc6-101">SignalR： JavaScript 用戶端套件名稱已變更</span><span class="sxs-lookup"><span data-stu-id="9bcc6-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="9bcc6-102">在 ASP.NET Core 3.0 Preview 7 中，SignalR JavaScript 用戶端套件名稱已從變更 `@aspnet/signalr` 為 `@microsoft/signalr` 。</span><span class="sxs-lookup"><span data-stu-id="9bcc6-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="9bcc6-103">名稱變更反映了 Azure SignalR Service，而不只是 ASP.NET Core 的應用程式，SignalR 會很有用。</span><span class="sxs-lookup"><span data-stu-id="9bcc6-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="9bcc6-104">若要回應這項變更，請在檔案 *package.json* 、 `require` 語句和 ECMAScript 語句上變更package.js中的參考 `import` 。</span><span class="sxs-lookup"><span data-stu-id="9bcc6-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="9bcc6-105">此重新命名過程中不會變更任何 API。</span><span class="sxs-lookup"><span data-stu-id="9bcc6-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="9bcc6-106">如需討論，請參閱 [dotnet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637)。</span><span class="sxs-lookup"><span data-stu-id="9bcc6-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9bcc6-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9bcc6-107">Version introduced</span></span>

<span data-ttu-id="9bcc6-108">3.0</span><span class="sxs-lookup"><span data-stu-id="9bcc6-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9bcc6-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="9bcc6-109">Old behavior</span></span>

<span data-ttu-id="9bcc6-110">用戶端封裝的名稱為 `@aspnet/signalr` 。</span><span class="sxs-lookup"><span data-stu-id="9bcc6-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9bcc6-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="9bcc6-111">New behavior</span></span>

<span data-ttu-id="9bcc6-112">用戶端封裝的名稱為 `@microsoft/signalr` 。</span><span class="sxs-lookup"><span data-stu-id="9bcc6-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9bcc6-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="9bcc6-113">Reason for change</span></span>

<span data-ttu-id="9bcc6-114">名稱變更指出，SignalR 在 Azure SignalR Service 的情況下，對 ASP.NET Core 應用程式來說很有用。</span><span class="sxs-lookup"><span data-stu-id="9bcc6-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9bcc6-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="9bcc6-115">Recommended action</span></span>

<span data-ttu-id="9bcc6-116">切換至新的封裝 `@microsoft/signalr` 。</span><span class="sxs-lookup"><span data-stu-id="9bcc6-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="9bcc6-117">類別</span><span class="sxs-lookup"><span data-stu-id="9bcc6-117">Category</span></span>

<span data-ttu-id="9bcc6-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9bcc6-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9bcc6-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9bcc6-119">Affected APIs</span></span>

<span data-ttu-id="9bcc6-120">無</span><span class="sxs-lookup"><span data-stu-id="9bcc6-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
