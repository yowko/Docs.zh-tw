---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901915"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="6e428-101">Kestrel：連接配接器已移除</span><span class="sxs-lookup"><span data-stu-id="6e428-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="6e428-102">作為將"公共"API 移動到移動的一部分`public`，從 Kestrel 中刪除`IConnectionAdapter`了 a 的概念。</span><span class="sxs-lookup"><span data-stu-id="6e428-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="6e428-103">連接配接器正在被連接中介軟體替換（類似于 ASP.NET核心管道中的 HTTP 中介軟體，但對於較低級別的連接）。</span><span class="sxs-lookup"><span data-stu-id="6e428-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="6e428-104">HTTPS 和連接日誌記錄已經從連接配接器移動到連接中介軟體。</span><span class="sxs-lookup"><span data-stu-id="6e428-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="6e428-105">這些擴充方法應繼續無縫工作，但實現細節已更改。</span><span class="sxs-lookup"><span data-stu-id="6e428-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="6e428-106">有關詳細資訊，請參閱[點網/阿斯平核心#11412](https://github.com/dotnet/aspnetcore/pull/11412)。</span><span class="sxs-lookup"><span data-stu-id="6e428-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="6e428-107">有關討論，請參閱[點網/阿斯平核心#11475](https://github.com/dotnet/aspnetcore/issues/11475)。</span><span class="sxs-lookup"><span data-stu-id="6e428-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6e428-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="6e428-108">Version introduced</span></span>

<span data-ttu-id="6e428-109">3.0</span><span class="sxs-lookup"><span data-stu-id="6e428-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6e428-110">舊的行為</span><span class="sxs-lookup"><span data-stu-id="6e428-110">Old behavior</span></span>

<span data-ttu-id="6e428-111">Kestrel 擴充性元件是使用`IConnectionAdapter`創建的。</span><span class="sxs-lookup"><span data-stu-id="6e428-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6e428-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="6e428-112">New behavior</span></span>

<span data-ttu-id="6e428-113">Kestrel 擴充性元件創建為[中介軟體](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)。</span><span class="sxs-lookup"><span data-stu-id="6e428-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6e428-114">更改原因</span><span class="sxs-lookup"><span data-stu-id="6e428-114">Reason for change</span></span>

<span data-ttu-id="6e428-115">此更改旨在提供更靈活的擴充性體系結構。</span><span class="sxs-lookup"><span data-stu-id="6e428-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6e428-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="6e428-116">Recommended action</span></span>

<span data-ttu-id="6e428-117">轉換的任何`IConnectionAdapter`實現，以使用新的中介軟體模式，[如下所示](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)。</span><span class="sxs-lookup"><span data-stu-id="6e428-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="6e428-118">類別</span><span class="sxs-lookup"><span data-stu-id="6e428-118">Category</span></span>

<span data-ttu-id="6e428-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6e428-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6e428-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6e428-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
