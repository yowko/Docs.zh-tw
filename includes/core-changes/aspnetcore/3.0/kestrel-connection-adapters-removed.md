---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901915"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="27954-101">Kestrel：已移除連接介面卡</span><span class="sxs-lookup"><span data-stu-id="27954-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="27954-102">在移至將 "pubternal" Api 移至 `public`的過程中，`IConnectionAdapter` 的概念已從 Kestrel 中移除。</span><span class="sxs-lookup"><span data-stu-id="27954-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="27954-103">連接介面卡會被連線中介軟體取代（類似于 ASP.NET Core 管線中的 HTTP 中介軟體，但適用于較低層級的連接）。</span><span class="sxs-lookup"><span data-stu-id="27954-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="27954-104">HTTPS 和連線記錄已從連接介面卡移至連線中介軟體。</span><span class="sxs-lookup"><span data-stu-id="27954-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="27954-105">這些擴充方法應該繼續順暢地工作，但執行詳細資料已變更。</span><span class="sxs-lookup"><span data-stu-id="27954-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="27954-106">如需詳細資訊，請參閱[dotnet/aspnetcore # 11412](https://github.com/dotnet/aspnetcore/pull/11412)。</span><span class="sxs-lookup"><span data-stu-id="27954-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="27954-107">如需討論，請參閱[dotnet/aspnetcore # 11475](https://github.com/dotnet/aspnetcore/issues/11475)。</span><span class="sxs-lookup"><span data-stu-id="27954-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="27954-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="27954-108">Version introduced</span></span>

<span data-ttu-id="27954-109">3.0</span><span class="sxs-lookup"><span data-stu-id="27954-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="27954-110">舊的行為</span><span class="sxs-lookup"><span data-stu-id="27954-110">Old behavior</span></span>

<span data-ttu-id="27954-111">Kestrel 擴充性元件是使用 `IConnectionAdapter`建立的。</span><span class="sxs-lookup"><span data-stu-id="27954-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="27954-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="27954-112">New behavior</span></span>

<span data-ttu-id="27954-113">Kestrel 擴充性元件會建立為[中介軟體](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)。</span><span class="sxs-lookup"><span data-stu-id="27954-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="27954-114">變更的原因</span><span class="sxs-lookup"><span data-stu-id="27954-114">Reason for change</span></span>

<span data-ttu-id="27954-115">這種變更的目的是要提供更具彈性的擴充性架構。</span><span class="sxs-lookup"><span data-stu-id="27954-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="27954-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="27954-116">Recommended action</span></span>

<span data-ttu-id="27954-117">轉換任何 `IConnectionAdapter` 的執行，以使用新的中介軟體模式[，如下所示。](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)</span><span class="sxs-lookup"><span data-stu-id="27954-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="27954-118">分類</span><span class="sxs-lookup"><span data-stu-id="27954-118">Category</span></span>

<span data-ttu-id="27954-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="27954-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="27954-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="27954-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
