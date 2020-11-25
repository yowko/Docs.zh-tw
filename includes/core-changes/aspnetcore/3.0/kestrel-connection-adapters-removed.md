---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032377"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="f4275-101">Kestrel：已移除連接配接器</span><span class="sxs-lookup"><span data-stu-id="f4275-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="f4275-102">在移動 "pubternal" Api 至的過程中 `public` ， `IConnectionAdapter` 已從 Kestrel 移除的概念。</span><span class="sxs-lookup"><span data-stu-id="f4275-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="f4275-103">連接卡將取代為連接中介軟體 (類似 ASP.NET Core 管線中的 HTTP 中介軟體，但較低層級的連線) 。</span><span class="sxs-lookup"><span data-stu-id="f4275-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="f4275-104">HTTPS 和連線記錄已從連接配接器移至連接中介軟體。</span><span class="sxs-lookup"><span data-stu-id="f4275-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="f4275-105">這些擴充方法應該會繼續順暢地運作，但是執行的詳細資料已變更。</span><span class="sxs-lookup"><span data-stu-id="f4275-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="f4275-106">如需詳細資訊，請參閱 [dotnet/aspnetcore # 11412](https://github.com/dotnet/aspnetcore/pull/11412)。</span><span class="sxs-lookup"><span data-stu-id="f4275-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="f4275-107">如需討論，請參閱 [dotnet/aspnetcore # 11475](https://github.com/dotnet/aspnetcore/issues/11475)。</span><span class="sxs-lookup"><span data-stu-id="f4275-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f4275-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4275-108">Version introduced</span></span>

<span data-ttu-id="f4275-109">3.0</span><span class="sxs-lookup"><span data-stu-id="f4275-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f4275-110">舊的行為</span><span class="sxs-lookup"><span data-stu-id="f4275-110">Old behavior</span></span>

<span data-ttu-id="f4275-111">Kestrel 擴充性元件是使用建立 `IConnectionAdapter` 的。</span><span class="sxs-lookup"><span data-stu-id="f4275-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f4275-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="f4275-112">New behavior</span></span>

<span data-ttu-id="f4275-113">Kestrel 擴充性元件會建立為 [中介軟體](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)。</span><span class="sxs-lookup"><span data-stu-id="f4275-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f4275-114">變更的原因</span><span class="sxs-lookup"><span data-stu-id="f4275-114">Reason for change</span></span>

<span data-ttu-id="f4275-115">這項變更的目的是要提供更具彈性的擴充性架構。</span><span class="sxs-lookup"><span data-stu-id="f4275-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f4275-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f4275-116">Recommended action</span></span>

<span data-ttu-id="f4275-117">將的任何執行轉換為 `IConnectionAdapter` 使用新的中介軟體模式[here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)，如下所示。</span><span class="sxs-lookup"><span data-stu-id="f4275-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="f4275-118">類別</span><span class="sxs-lookup"><span data-stu-id="f4275-118">Category</span></span>

<span data-ttu-id="f4275-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f4275-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f4275-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f4275-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
