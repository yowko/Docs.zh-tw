---
ms.openlocfilehash: 203d75f5858c8ff039cf579c0539efda0c5c9f02
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474370"
---
### <a name="kestrel-libuv-transport-marked-as-obsolete"></a><span data-ttu-id="bc5f9-101">Kestrel： Libuv 傳輸標示為已淘汰</span><span class="sxs-lookup"><span data-stu-id="bc5f9-101">Kestrel: Libuv transport marked as obsolete</span></span>

<span data-ttu-id="bc5f9-102">舊版 ASP.NET Core 使用 Libuv 作為非同步輸入和輸出執行方式的執行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-102">Earlier versions of ASP.NET Core used Libuv as an implementation detail of how asynchronous input and output was performed.</span></span> <span data-ttu-id="bc5f9-103">在 ASP.NET Core 2.0 中，開發了替代的 <xref:System.Net.Sockets.Socket> 型傳輸。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-103">In ASP.NET Core 2.0, an alternative, <xref:System.Net.Sockets.Socket>-based transport was developed.</span></span> <span data-ttu-id="bc5f9-104">在 ASP.NET Core 2.1 中，Kestrel 預設會切換為使用以 `Socket` 傳輸為基礎的傳輸。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-104">In ASP.NET Core 2.1, Kestrel switched to using the `Socket`-based transport by default.</span></span> <span data-ttu-id="bc5f9-105">基於相容性考慮，已維持 Libuv 支援。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-105">Libuv support was maintained for compatibility reasons.</span></span>

<span data-ttu-id="bc5f9-106">到目前為止，使用以 `Socket` 傳輸為基礎的傳輸比 Libuv 傳輸更為普遍。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-106">At this point, use of the `Socket`-based transport is far more common than the Libuv transport.</span></span> <span data-ttu-id="bc5f9-107">因此，Libuv 支援在 .NET 5.0 中會標示為已淘汰，而且將完全在 .NET 6.0 中移除。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-107">Consequently, Libuv support is marked as obsolete in .NET 5.0 and will be removed entirely in .NET 6.0.</span></span>

<span data-ttu-id="bc5f9-108">作為這項變更的一部分，Libuv 支援新的作業系統平臺 (例如 Windows ARM64) 不會加入 .NET 5.0 時間範圍中。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-108">As part of this change, Libuv support for new operating system platforms (like Windows ARM64) won't be added in the .NET 5.0 timeframe.</span></span>

<span data-ttu-id="bc5f9-109">如需封鎖需要使用 Libuv 傳輸之問題的討論，請參閱 GitHub 在 [dotnet/aspnetcore # 23409](https://github.com/dotnet/aspnetcore/issues/23409)的問題。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-109">For discussion on blocking issues that require the use of the Libuv transport, see the GitHub issue at [dotnet/aspnetcore#23409](https://github.com/dotnet/aspnetcore/issues/23409).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bc5f9-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="bc5f9-110">Version introduced</span></span>

<span data-ttu-id="bc5f9-111">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="bc5f9-111">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="bc5f9-112">舊的行為</span><span class="sxs-lookup"><span data-stu-id="bc5f9-112">Old behavior</span></span>

<span data-ttu-id="bc5f9-113">Libuv Api 未標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-113">The Libuv APIs aren't marked as obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="bc5f9-114">新的行為</span><span class="sxs-lookup"><span data-stu-id="bc5f9-114">New behavior</span></span>

<span data-ttu-id="bc5f9-115">Libuv Api 會標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-115">The Libuv APIs are marked as obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bc5f9-116">變更的原因</span><span class="sxs-lookup"><span data-stu-id="bc5f9-116">Reason for change</span></span>

<span data-ttu-id="bc5f9-117">以 `Socket` 傳輸為基礎的預設值。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-117">The `Socket`-based transport is the default.</span></span> <span data-ttu-id="bc5f9-118">繼續使用 Libuv 傳輸沒有任何吸引人的理由。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-118">There aren't any compelling reasons to continue using the Libuv transport.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bc5f9-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bc5f9-119">Recommended action</span></span>

<span data-ttu-id="bc5f9-120">不再使用 [Libuv 封裝](https://www.nuget.org/packages/Libuv) 和擴充方法。</span><span class="sxs-lookup"><span data-stu-id="bc5f9-120">Discontinue use of the [Libuv package](https://www.nuget.org/packages/Libuv) and extension methods.</span></span>

#### <a name="category"></a><span data-ttu-id="bc5f9-121">類別</span><span class="sxs-lookup"><span data-stu-id="bc5f9-121">Category</span></span>

<span data-ttu-id="bc5f9-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bc5f9-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bc5f9-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bc5f9-123">Affected APIs</span></span>

- [<span data-ttu-id="bc5f9-124">>webhostbuilderlibuvextensions.uselibuv</span><span class="sxs-lookup"><span data-stu-id="bc5f9-124">WebHostBuilderLibuvExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [<span data-ttu-id="bc5f9-125">>webhostbuilderlibuvextensions.uselibuv. >webhostbuilderlibuvextensions.uselibuv</span><span class="sxs-lookup"><span data-stu-id="bc5f9-125">WebHostBuilderLibuvExtensions.UseLibuv</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [<span data-ttu-id="bc5f9-126">AspNetCore. Kestrel. Libuv. LibuvTransportOptions</span><span class="sxs-lookup"><span data-stu-id="bc5f9-126">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [<span data-ttu-id="bc5f9-127">AspNetCore. Kestrel. Libuv. LibuvTransportOptions. ThreadCount</span><span class="sxs-lookup"><span data-stu-id="bc5f9-127">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [<span data-ttu-id="bc5f9-128">AspNetCore. Kestrel. Libuv. LibuvTransportOptions. NoDelay</span><span class="sxs-lookup"><span data-stu-id="bc5f9-128">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [<span data-ttu-id="bc5f9-129">AspNetCore. Kestrel. Libuv. LibuvTransportOptions. MaxWriteBufferSize</span><span class="sxs-lookup"><span data-stu-id="bc5f9-129">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [<span data-ttu-id="bc5f9-130">AspNetCore. Kestrel. Libuv. LibuvTransportOptions. MaxReadBufferSize</span><span class="sxs-lookup"><span data-stu-id="bc5f9-130">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
- `Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions`
- `Overload:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions.UseLibuv`
- `T:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

-->
