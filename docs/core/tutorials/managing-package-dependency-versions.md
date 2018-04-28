---
title: 如何管理 .NET Core 1.0 的套件相依性版本
description: 了解您的 .NET Core 程式庫和應用程式的套件相依性版本管理。
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 7b508f3d83833361bd830bb232587df2ad090661
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a><span data-ttu-id="32928-103">如何管理 .NET Core 1.0 的套件相依性版本</span><span class="sxs-lookup"><span data-stu-id="32928-103">How to Manage Package Dependency Versions for .NET Core 1.0</span></span>

<span data-ttu-id="32928-104">本文章涵蓋您需要知道有關 .NET Core 程式庫和應用程式套件版本的資訊。</span><span class="sxs-lookup"><span data-stu-id="32928-104">This article covers what you need to know about package versions for your .NET Core libraries and apps.</span></span>

## <a name="glossary"></a><span data-ttu-id="32928-105">字彙表</span><span class="sxs-lookup"><span data-stu-id="32928-105">Glossary</span></span>

<span data-ttu-id="32928-106">**修正** - 修正相依性表示，您會使用在 NuGet 上發行、適用於 .NET Core 1.0 的相同系列套件。</span><span class="sxs-lookup"><span data-stu-id="32928-106">**Fix** - Fixing dependencies means you are using the same "family" of packages released on NuGet for .NET Core 1.0.</span></span>

<span data-ttu-id="32928-107">**中繼套件** - NuGet 套件，代表一組 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="32928-107">**Metapackage** - A NuGet package that represents a set of NuGet packages.</span></span>

<span data-ttu-id="32928-108">**修剪** - 從中繼套件移除不依賴之套件的動作。</span><span class="sxs-lookup"><span data-stu-id="32928-108">**Trimming** - The act of removing the packages you do not depend on from a metapackage.</span></span>  <span data-ttu-id="32928-109">這與 NuGet 套件作者有關。</span><span class="sxs-lookup"><span data-stu-id="32928-109">This is something relevant for NuGet package authors.</span></span>  <span data-ttu-id="32928-110">如需詳細資訊，請參閱[減少與 project.json 的套件相依性](../deploying/reducing-dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="32928-110">See [Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md) for more information.</span></span> 

## <a name="fix-your-dependencies-to-net-core-10"></a><span data-ttu-id="32928-111">將相依性固定為 .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="32928-111">Fix your dependencies to .NET Core 1.0</span></span>

<span data-ttu-id="32928-112">若要可靠地還原套件，並撰寫可靠的程式碼，很重要的一點是將相依性固定為與 .NET Core 1.0 一起出貨的套件版本。</span><span class="sxs-lookup"><span data-stu-id="32928-112">To reliably restore packages and write reliable code, it's important that you fix your dependencies to the versions of packages shipping alongside .NET Core 1.0.</span></span>  <span data-ttu-id="32928-113">這表示每個套件應該有單一版本，而且不含任何額外的限定詞。</span><span class="sxs-lookup"><span data-stu-id="32928-113">This means every package should have a single version with no additional qualifiers.</span></span>

<span data-ttu-id="32928-114">**固定為 1.0 的套件範例**</span><span class="sxs-lookup"><span data-stu-id="32928-114">**Examples of packages fixed to 1.0**</span></span>

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

<span data-ttu-id="32928-115">**未固定為 1.0 的套件範例**</span><span class="sxs-lookup"><span data-stu-id="32928-115">**Examples of packages that are NOT fixed to 1.0**</span></span>

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a><span data-ttu-id="32928-116">這為什麼重要？</span><span class="sxs-lookup"><span data-stu-id="32928-116">Why does this matter?</span></span>

<span data-ttu-id="32928-117">我們保證，如果您將相依性固定為與 .NET Core 1.0 一起出貨的項目時，那些套件將一起運作。</span><span class="sxs-lookup"><span data-stu-id="32928-117">We guarantee that if you fix your dependencies to what ships alongside .NET Core 1.0, those packages will all work together.</span></span> <span data-ttu-id="32928-118">如果您使用未以此方式固定的套件，則沒有這種保證。</span><span class="sxs-lookup"><span data-stu-id="32928-118">There is no such guarantee if you use packages which aren't fixed in this way.</span></span>

### <a name="scenarios"></a><span data-ttu-id="32928-119">案例</span><span class="sxs-lookup"><span data-stu-id="32928-119">Scenarios</span></span>

<span data-ttu-id="32928-120">雖然與 .NET Core 1.0 一起發行的所有套件和其版本清單冗長，但如果您的程式碼落在特定狀況下，可能不必看完整份清單。</span><span class="sxs-lookup"><span data-stu-id="32928-120">Although there is a big list of all packages and their versions released with .NET Core 1.0, you may not have to look through it if your code falls under certain scenarios.</span></span>

<span data-ttu-id="32928-121">**您是否只依賴** `NETStandard.Library`**？**</span><span class="sxs-lookup"><span data-stu-id="32928-121">**Are you depending only on** `NETStandard.Library`**?**</span></span>

<span data-ttu-id="32928-122">如果是，您應該將 `NETStandard.Library` 套件固定為 `1.6` 版。</span><span class="sxs-lookup"><span data-stu-id="32928-122">If so, you should fix your `NETStandard.Library` package to version `1.6`.</span></span>  <span data-ttu-id="32928-123">因為這是策劃的中繼套件，其套件終止也會固定為 1.0。</span><span class="sxs-lookup"><span data-stu-id="32928-123">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="32928-124">**您是否只依賴** `Microsoft.NETCore.App`**？**</span><span class="sxs-lookup"><span data-stu-id="32928-124">**Are you depending only on** `Microsoft.NETCore.App`**?**</span></span>

<span data-ttu-id="32928-125">如果是，您應該將 `Microsoft.NETCore.App` 套件固定為 `1.0.0` 版。</span><span class="sxs-lookup"><span data-stu-id="32928-125">If so, you should fix your `Microsoft.NETCore.App` package to version `1.0.0`.</span></span>  <span data-ttu-id="32928-126">因為這是策劃的中繼套件，其套件終止也會固定為 1.0。</span><span class="sxs-lookup"><span data-stu-id="32928-126">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="32928-127">**您是否[修剪](../deploying/reducing-dependencies.md)您的** `NETStandard.Library` **或** `Microsoft.NETCore.App` **中繼套件相依性？**</span><span class="sxs-lookup"><span data-stu-id="32928-127">**Are you [trimming](../deploying/reducing-dependencies.md) your** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackage dependencies?**</span></span>

<span data-ttu-id="32928-128">如果是，您應該確定您啟動用的中繼套件固定為 1.0。</span><span class="sxs-lookup"><span data-stu-id="32928-128">If so, you should ensure that the metapackage you start with is fixed to 1.0.</span></span>  <span data-ttu-id="32928-129">修剪之後依賴的個別套件也會固定為 1.0。</span><span class="sxs-lookup"><span data-stu-id="32928-129">The individual packages you depend on after trimming are also fixed to 1.0.</span></span>

<span data-ttu-id="32928-130">**您是否依賴** `NETStandard.Library` **或** `Microsoft.NETCore.App` **中繼套件之外的套件？**</span><span class="sxs-lookup"><span data-stu-id="32928-130">**Are you depending on packages outside the** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackages?**</span></span>

<span data-ttu-id="32928-131">如果是，您需要將其他相依性固定為 1.0。</span><span class="sxs-lookup"><span data-stu-id="32928-131">If so, you need to fix your other dependencies to 1.0.</span></span>  <span data-ttu-id="32928-132">如需正確的套件版本和組建號碼，請參閱在本文結尾。</span><span class="sxs-lookup"><span data-stu-id="32928-132">See the correct package versions and build numbers at the end of this article.</span></span>

### <a name="a-note-on-using-a-splat-string--when-versioning"></a><span data-ttu-id="32928-133">版本控制時，使用 splat 字串 (\*) 的注意事項</span><span class="sxs-lookup"><span data-stu-id="32928-133">A note on using a splat string (\*) when versioning</span></span>

<span data-ttu-id="32928-134">您採用的版本控制模式可能是使用 splat (\*) 字串，就像這樣︰`"System.Collections":"4.0.11-*"`。</span><span class="sxs-lookup"><span data-stu-id="32928-134">You may have adopted a versioning pattern which uses a splat (\*) string like this: `"System.Collections":"4.0.11-*"`.</span></span>

<span data-ttu-id="32928-135">**您不應該這麼做**。</span><span class="sxs-lookup"><span data-stu-id="32928-135">**You should not do this**.</span></span>  <span data-ttu-id="32928-136">使用 splat 字串可能會導致從不同的組建還原套件，這些組建有些可能比 .NET Core 1.0 更遠。</span><span class="sxs-lookup"><span data-stu-id="32928-136">Using the splat string could result in restoring packages from different builds, some of which may be further along than .NET Core 1.0.</span></span>  <span data-ttu-id="32928-137">這可能導致某些套件不相容。</span><span class="sxs-lookup"><span data-stu-id="32928-137">This could then result in some packages being incompatible.</span></span>

## <a name="packages-and-version-numbers-organized-by-metapackage"></a><span data-ttu-id="32928-138">依中繼套件組織的套件和版本號碼</span><span class="sxs-lookup"><span data-stu-id="32928-138">Packages and Version Numbers organized by Metapackage</span></span>

<span data-ttu-id="32928-139">[所有 .NET Standard 套件和其適用於 1.0 的版本清單](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt)。</span><span class="sxs-lookup"><span data-stu-id="32928-139">[List of all .NET Standard packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span></span>

<span data-ttu-id="32928-140">[所有執行階段套件和其適用於 1.0 的版本清單](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt)。</span><span class="sxs-lookup"><span data-stu-id="32928-140">[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span></span>

<span data-ttu-id="32928-141">[所有 .NET Core 應用程式套件和其適用於 1.0 的版本清單](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt)。</span><span class="sxs-lookup"><span data-stu-id="32928-141">[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span></span>
