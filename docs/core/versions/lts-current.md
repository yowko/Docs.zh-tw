---
title: ".NET Core 支援"
description: "了解適用於 .NET Core 的不同版本序列的支援 (LTS 和目前)"
keywords: ".NET, .NET Core, lts, 目前, fts, 支援, 支援train, 支援追蹤, 週期, release train"
author: kendrahavens
ms.author: mairaw
ms.date: 01/30/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: fedc7025-f320-4cba-957b-ef74885f66de
ms.workload: dotnetcore
ms.openlocfilehash: 2fcb33c7c5a4a3c31960a683865b0e5e29269a8b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-support"></a><span data-ttu-id="8e397-104">.NET Core 支援</span><span class="sxs-lookup"><span data-stu-id="8e397-104">.NET Core Support</span></span>

<span data-ttu-id="8e397-105">這是 .NET Core 支援的一般說明。</span><span class="sxs-lookup"><span data-stu-id="8e397-105">This is a general description of .NET Core support.</span></span>

## <a name="lts-and-current-release-trains"></a><span data-ttu-id="8e397-106">LTS 和目前的 Release Train</span><span class="sxs-lookup"><span data-stu-id="8e397-106">LTS and Current Release Trains</span></span>

<span data-ttu-id="8e397-107">支援兩個 Release Train 是整個軟體界常用的概念，特別是像 .NET Core 這類開放原始碼專案。</span><span class="sxs-lookup"><span data-stu-id="8e397-107">Having two support release trains is a common concept in use throughout the software world, specially for open-source projects like .NET Core.</span></span> <span data-ttu-id="8e397-108">.NET Core 支援下列版本序列︰[長期支援 (LTS) (英文)](https://en.wikipedia.org/wiki/Long-term_support) 和目前。</span><span class="sxs-lookup"><span data-stu-id="8e397-108">.NET Core has the following support release trains: [Long Term Support (LTS)](https://en.wikipedia.org/wiki/Long-term_support) and Current.</span></span> <span data-ttu-id="8e397-109">LTS 版本會受到維護，以在其週期內提供穩定性，可接收重要問題的修正和安全性問題修正。</span><span class="sxs-lookup"><span data-stu-id="8e397-109">LTS releases are maintained for stability over their lifecycle, receiving fixes for important issues and security fixes.</span></span> <span data-ttu-id="8e397-110">目前版本中會有新的功能工作和其他 Bug 修正。</span><span class="sxs-lookup"><span data-stu-id="8e397-110">New feature work and additional bug fixes take place in Current releases.</span></span> <span data-ttu-id="8e397-111">從支援的觀點來看，這些 Release Train 具有下列支援週期屬性。</span><span class="sxs-lookup"><span data-stu-id="8e397-111">From a support perspective, these release trains have the following support lifecycle attributes.</span></span>

<span data-ttu-id="8e397-112">LTS 版本</span><span class="sxs-lookup"><span data-stu-id="8e397-112">LTS releases are</span></span>
* <span data-ttu-id="8e397-113">可於 LTS 版本全面上市後，提供為期三年的支援</span><span class="sxs-lookup"><span data-stu-id="8e397-113">Supported for three years after the general availability date of a LTS release</span></span>
* <span data-ttu-id="8e397-114">或可於後續的 LTS 版本全面上市後，提供為期一年的支援</span><span class="sxs-lookup"><span data-stu-id="8e397-114">Or one year after the general availability of a subsequent LTS release</span></span>

<span data-ttu-id="8e397-115">目前版本</span><span class="sxs-lookup"><span data-stu-id="8e397-115">Current releases are</span></span>
* <span data-ttu-id="8e397-116">和父代 LTS 版本一樣，同樣提供為期三年的支援</span><span class="sxs-lookup"><span data-stu-id="8e397-116">Supported within the same three-year window as the parent LTS release</span></span>
* <span data-ttu-id="8e397-117">可於後續的目前版本全面上市後，提供為期三個月的支援</span><span class="sxs-lookup"><span data-stu-id="8e397-117">Supported for three months after the general availability of a subsequent Current release</span></span>
* <span data-ttu-id="8e397-118">並可於後續的 LTS 版本全面上市後，提供為期一年的支援</span><span class="sxs-lookup"><span data-stu-id="8e397-118">And one year after the general availability of a subsequent LTS release</span></span>

## <a name="versioning"></a><span data-ttu-id="8e397-119">版本控制</span><span class="sxs-lookup"><span data-stu-id="8e397-119">Versioning</span></span>
<span data-ttu-id="8e397-120">利用增加的主要版本號碼來標示新的 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="8e397-120">New LTS releases are marked by an increase in the Major version number.</span></span> <span data-ttu-id="8e397-121">目前版本的主要版本號碼會和對應的 LTS Train 相同，並會利用增加的主要版本號碼來標示版本。</span><span class="sxs-lookup"><span data-stu-id="8e397-121">Current releases have the same Major number as the corresponding LTS train and are marked by an increase in the Minor version number.</span></span> <span data-ttu-id="8e397-122">例如，1.0.3 為 LTS 版本，而 1.1.0 則為目前版本。</span><span class="sxs-lookup"><span data-stu-id="8e397-122">For example, 1.0.3 would be LTS and 1.1.0 would be Current.</span></span> <span data-ttu-id="8e397-123">對任一 Train 更新 Bug 修正，會讓修補檔案版本遞增。</span><span class="sxs-lookup"><span data-stu-id="8e397-123">Bug fix updates to either train increment the Patch version.</span></span> <span data-ttu-id="8e397-124">如需版本控制配置的詳細資訊，請參閱 [.NET Core 版本控制](index.md)。</span><span class="sxs-lookup"><span data-stu-id="8e397-124">For more information on the versioning scheme, see [.NET Core Versioning](index.md).</span></span>

## <a name="what-causes-updates-in-lts-and-current-trains"></a><span data-ttu-id="8e397-125">在 LTS 和目前的 Train 中造成更新的原因為何？</span><span class="sxs-lookup"><span data-stu-id="8e397-125">What causes updates in LTS and Current trains?</span></span>
<span data-ttu-id="8e397-126">若要了解哪些特定變更，例如 Bug 修正或加入 API，會導致更新版本號碼，請檢閱[版本控制說明文件](index.md)中的「決策樹」一節。</span><span class="sxs-lookup"><span data-stu-id="8e397-126">To understand what specific changes, such as bug fixes or the addition of APIs, cause updates to the version numbers review the Decision Tree section in the [Versioning Documentation](index.md).</span></span> <span data-ttu-id="8e397-127">要決定將哪些變更從目前版本提取到 LTS 分支中，並沒有黃金規則。</span><span class="sxs-lookup"><span data-stu-id="8e397-127">There is not a golden set of rules that decide what changes are pulled into the LTS branch from Current.</span></span> <span data-ttu-id="8e397-128">一般而言，可修正預期行為的必要安全性問題更新與修補檔案，都會造成更新 LTS 分支。</span><span class="sxs-lookup"><span data-stu-id="8e397-128">Typically, necessary security updates and patches that fix expected behaviour are reasons to update the LTS branch.</span></span> <span data-ttu-id="8e397-129">雖然這不一定可行，但我們也想要支援 LTS 分支上最近的桌面開發人員作業系統。</span><span class="sxs-lookup"><span data-stu-id="8e397-129">We also intend to support recent desktop developer operating systems on the LTS branch, though this may not always be possible.</span></span> <span data-ttu-id="8e397-130">想要掌握特定版本中支援哪些 API、修正及作業系統，最好瀏覽其在 GitHub 上的[版本資訊](https://github.com/dotnet/core/tree/master/release-notes)。</span><span class="sxs-lookup"><span data-stu-id="8e397-130">A good way to catch up on what APIs, fixes, and operating systems are supported in a certain release is to browse its [release notes](https://github.com/dotnet/core/tree/master/release-notes) on GitHub.</span></span>

### <a name="further-reading"></a><span data-ttu-id="8e397-131">進一步閱讀</span><span class="sxs-lookup"><span data-stu-id="8e397-131">Further Reading</span></span>
* [<span data-ttu-id="8e397-132">.NET Core 支援週期資料表</span><span class="sxs-lookup"><span data-stu-id="8e397-132">.NET Core Support Lifecycle Fact Sheet</span></span>](https://www.microsoft.com/net/core/support)
* [<span data-ttu-id="8e397-133">目前支援的作業系統和版本</span><span class="sxs-lookup"><span data-stu-id="8e397-133">Currently supported operating systems and versions</span></span>](https://github.com/dotnet/core/blob/master/roadmap.md)
