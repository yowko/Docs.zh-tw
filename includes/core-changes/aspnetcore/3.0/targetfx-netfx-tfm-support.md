---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937256"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="83464-101">目標框架： .NET 框架支援已放棄</span><span class="sxs-lookup"><span data-stu-id="83464-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="83464-102">從ASP.NET核心 3.0 開始，.NET 框架是一個不受支援的目標框架。</span><span class="sxs-lookup"><span data-stu-id="83464-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="83464-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="83464-103">Change description</span></span>

<span data-ttu-id="83464-104">.NET 框架 4.8 是 .NET 框架的最後一個主要版本。</span><span class="sxs-lookup"><span data-stu-id="83464-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="83464-105">新的ASP.NET核心應用應建立在 .NET Core 上。</span><span class="sxs-lookup"><span data-stu-id="83464-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="83464-106">從 .NET Core 3.0 版本開始，可以將 ASP.NET核心 3.0 視為 .NET Core 的一部分。</span><span class="sxs-lookup"><span data-stu-id="83464-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="83464-107">使用帶有 .NET 框架ASP.NET核心的客戶可以使用[2.1 LTS 版本](https://www.microsoft.com/net/download/dotnet-core/2.1)以完全支援的方式繼續。</span><span class="sxs-lookup"><span data-stu-id="83464-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="83464-108">2.1 的支援和服務至少持續到 2021 年 8 月 21 日。</span><span class="sxs-lookup"><span data-stu-id="83464-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="83464-109">此日期是根據[.NET 支援政策](https://www.microsoft.com/net/platform/support-policy)聲明 LTS 發佈後三年。</span><span class="sxs-lookup"><span data-stu-id="83464-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="83464-110">**對 .NET Framework 上的**ASP.NET Core 2.1 包的支援將無限期擴展，類似于[其他基於包ASP.NET框架的服務策略](https://dotnet.microsoft.com/platform/support/policy/aspnet)。</span><span class="sxs-lookup"><span data-stu-id="83464-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="83464-111">有關從 .NET 框架移植到 .NET 核心的詳細資訊，請參閱[移植到 .NET 核心](~/docs/core/porting/index.md)。</span><span class="sxs-lookup"><span data-stu-id="83464-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="83464-112">`Microsoft.Extensions`包（如日誌記錄、依賴項注入和配置）和實體框架核心不受影響。</span><span class="sxs-lookup"><span data-stu-id="83464-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="83464-113">他們將繼續支援 .NET 標準。</span><span class="sxs-lookup"><span data-stu-id="83464-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="83464-114">有關此更改的動機的詳細資訊，請參閱[原始博客文章](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)。</span><span class="sxs-lookup"><span data-stu-id="83464-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="83464-115">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="83464-115">Version introduced</span></span>

<span data-ttu-id="83464-116">3.0</span><span class="sxs-lookup"><span data-stu-id="83464-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="83464-117">舊的行為</span><span class="sxs-lookup"><span data-stu-id="83464-117">Old behavior</span></span>

<span data-ttu-id="83464-118">ASP.NET核心應用可以在 .NET 核心或 .NET 框架上運行。</span><span class="sxs-lookup"><span data-stu-id="83464-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="83464-119">新的行為</span><span class="sxs-lookup"><span data-stu-id="83464-119">New behavior</span></span>

<span data-ttu-id="83464-120">ASP.NET核心應用只能在 .NET Core 上運行。</span><span class="sxs-lookup"><span data-stu-id="83464-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="83464-121">建議的動作</span><span class="sxs-lookup"><span data-stu-id="83464-121">Recommended action</span></span>

<span data-ttu-id="83464-122">請採取下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="83464-122">Take one of the following actions:</span></span>

- <span data-ttu-id="83464-123">將應用保持在 ASP.NET 核心 2.1 上。</span><span class="sxs-lookup"><span data-stu-id="83464-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="83464-124">將應用和依賴項遷移到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="83464-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="83464-125">類別</span><span class="sxs-lookup"><span data-stu-id="83464-125">Category</span></span>

<span data-ttu-id="83464-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="83464-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="83464-127">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="83464-127">Affected APIs</span></span>

<span data-ttu-id="83464-128">None</span><span class="sxs-lookup"><span data-stu-id="83464-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
