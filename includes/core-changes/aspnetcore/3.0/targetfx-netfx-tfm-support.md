---
ms.openlocfilehash: 4c676a185ff4a7a825acb059bf0a5842ca3922fc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394481"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="ac0c2-101">目標 framework： .NET Framework 支援捨棄</span><span class="sxs-lookup"><span data-stu-id="ac0c2-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="ac0c2-102">從 ASP.NET Core 3.0 開始，.NET Framework 是不支援的目標架構。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ac0c2-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="ac0c2-103">Change description</span></span>

<span data-ttu-id="ac0c2-104">.NET Framework 4.8 是 .NET Framework 的最後一個主要版本。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="ac0c2-105">新的 ASP.NET Core 應用程式應該以 .NET Core 為基礎。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="ac0c2-106">從 .NET Core 3.0 版本開始，您可以將 ASP.NET Core 3.0 視為 .NET Core 的一部分。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="ac0c2-107">使用 ASP.NET Core 搭配 .NET Framework 的客戶可以使用[2.1 LTS 版本](https://www.microsoft.com/net/download/dotnet-core/2.1)，以完全支援的方式繼續進行。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="ac0c2-108">2\.1 的支援和服務會持續到至少2021年8月21日為止。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="ac0c2-109">此日期是每個[.Net 支援原則](https://www.microsoft.com/net/platform/support-policy)宣告 LTS 版本後的三年。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="ac0c2-110">**.NET Framework 上**的 ASP.NET Core 2.1 套件支援將會無限期延伸，類似于[其他以套件為基礎的 ASP.NET 架構的服務原則](https://dotnet.microsoft.com/platform/support/policy/aspnet)。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="ac0c2-111">如需從 .NET Framework 移植至 .NET Core 的詳細資訊，請參閱[移植至 .Net core](~/docs/core/porting/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="ac0c2-112">`Microsoft.Extensions` 的封裝（例如記錄、相依性插入和設定）和 Entity Framework Core 不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="ac0c2-113">它們會繼續支援 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="ac0c2-114">如需這種變更動機的詳細資訊，請參閱[原始的 blog 文章](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0)。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-114">For more information on the motivation for this change, see [the original blog post](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ac0c2-115">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ac0c2-115">Version introduced</span></span>

<span data-ttu-id="ac0c2-116">3.0</span><span class="sxs-lookup"><span data-stu-id="ac0c2-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ac0c2-117">舊的行為</span><span class="sxs-lookup"><span data-stu-id="ac0c2-117">Old behavior</span></span>

<span data-ttu-id="ac0c2-118">ASP.NET Core 的應用程式可以在 .NET Core 或 .NET Framework 上執行。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ac0c2-119">新的行為</span><span class="sxs-lookup"><span data-stu-id="ac0c2-119">New behavior</span></span>

<span data-ttu-id="ac0c2-120">ASP.NET Core 應用程式只能在 .NET Core 上執行。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ac0c2-121">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ac0c2-121">Recommended action</span></span>

<span data-ttu-id="ac0c2-122">採取下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="ac0c2-122">Take one of the following actions:</span></span>

- <span data-ttu-id="ac0c2-123">將您的應用程式保留在 ASP.NET Core 2.1。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="ac0c2-124">將您的應用程式和相依性遷移至 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="ac0c2-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="ac0c2-125">分類</span><span class="sxs-lookup"><span data-stu-id="ac0c2-125">Category</span></span>

<span data-ttu-id="ac0c2-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ac0c2-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ac0c2-127">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ac0c2-127">Affected APIs</span></span>

<span data-ttu-id="ac0c2-128">無</span><span class="sxs-lookup"><span data-stu-id="ac0c2-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
