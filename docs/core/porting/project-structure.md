---
title: 組織適用於.NET Framework 和.NET Core 的專案
description: 協助想要同時針對 .NET Framework 及 .NET Core 編譯解決方案的專案擁有者。
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75777338"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="3ce5c-103">組織專案以同時支援 .NET Framework 及 .NET Core</span><span class="sxs-lookup"><span data-stu-id="3ce5c-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="3ce5c-104">您可以創建一個解決方案，用於並行為 .NET 框架和 .NET Core 進行編譯。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-104">You can create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="3ce5c-105">本文介紹幾個專案組織選項，以説明您實現這一目標。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-105">This article covers several project-organization options to help you achieve this goal.</span></span> <span data-ttu-id="3ce5c-106">在決定如何使用 .NET Core 設置專案佈局時，需要考慮以下一些典型方案。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-106">Here are some typical scenarios to consider when you're deciding how to set up your project layout with .NET Core.</span></span> <span data-ttu-id="3ce5c-107">此清單不一定涵蓋您想要的所有項目，根據專案需求決定優先順序。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="3ce5c-108">**將現有的專案和 .NET Core 專案合併成單一專案**</span><span class="sxs-lookup"><span data-stu-id="3ce5c-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="3ce5c-109">*適用於︰*</span><span class="sxs-lookup"><span data-stu-id="3ce5c-109">*What this is good for:*</span></span>
  - <span data-ttu-id="3ce5c-110">通過編譯單個專案而不是多個專案來簡化生成過程，每個專案都針對不同的 .NET Framework 版本或平臺。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-110">Simplifies your build process by compiling a single project rather than multiple projects that each target a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="3ce5c-111">簡化多目標專案的原始檔案管理，因為必須管理單個專案檔案。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-111">Simplifies source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="3ce5c-112">添加或刪除原始檔案時，替代方法要求您手動將這些檔與其他專案同步。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-112">When adding or removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="3ce5c-113">輕鬆生成用於消費的 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-113">Easily generate a NuGet package for consumption.</span></span>
  - <span data-ttu-id="3ce5c-114">讓您使用編譯器指示詞，在程式庫中針對特定的 .NET Framework 版本撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="3ce5c-115">*不支援的方案：*</span><span class="sxs-lookup"><span data-stu-id="3ce5c-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="3ce5c-116">要求開發人員使用 Visual Studio 2017 或更高版本打開現有專案。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-116">Requires developers to use Visual Studio 2017 or a later version to open existing projects.</span></span> <span data-ttu-id="3ce5c-117">若要支援舊版的 Visual Studio，[將專案檔放在不同的資料夾](#support-vs)是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="3ce5c-118">[**將現有的專案和新的 .NET Core 專案分開**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="3ce5c-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="3ce5c-119">*適用於︰*</span><span class="sxs-lookup"><span data-stu-id="3ce5c-119">*What this is good for:*</span></span>
  - <span data-ttu-id="3ce5c-120">支援開發現有專案，供可能沒有 Visual Studio 2017 或更高版本的開發人員和貢獻者開發。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-120">Supports development on existing projects for developers and contributors who may not have Visual Studio 2017 or a later version.</span></span>
  - <span data-ttu-id="3ce5c-121">減少在現有專案中創建新 Bug 的可能性，因為這些專案中不需要代碼改動。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-121">Decreases the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="3ce5c-122">範例</span><span class="sxs-lookup"><span data-stu-id="3ce5c-122">Example</span></span>

<span data-ttu-id="3ce5c-123">請考慮以下的儲存機制︰</span><span class="sxs-lookup"><span data-stu-id="3ce5c-123">Consider the repository below:</span></span>

![現有專案](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="3ce5c-125">**原始程式碼**</span><span class="sxs-lookup"><span data-stu-id="3ce5c-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="3ce5c-126">下列描述幾種方式以新增這個存放庫的 .NET Core 支援，視現有專案的條件約束和複雜性而定。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="3ce5c-127">使用多目標 .NET Core 專案取代現有的專案</span><span class="sxs-lookup"><span data-stu-id="3ce5c-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="3ce5c-128">重新組織存儲庫，以便刪除任何現有的*\*.csproj*檔，並創建針對多個框架的單個*\*.csproj*檔。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="3ce5c-129">這是一個不錯的選擇，因為單個專案能夠為不同的框架進行編譯。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-129">This is a great option, because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="3ce5c-130">它也可以處理個別目標架構的不同編譯選項及相依性。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![建立以多個架構為目標的 csproj](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="3ce5c-132">**原始程式碼**</span><span class="sxs-lookup"><span data-stu-id="3ce5c-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="3ce5c-133">要注意的變更如下︰</span><span class="sxs-lookup"><span data-stu-id="3ce5c-133">Changes to note are:</span></span>

- <span data-ttu-id="3ce5c-134">以新的 [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj) 取代 *packages.config* 和 *\*.csproj*。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="3ce5c-135">NuGet 套件是使用 `<PackageReference> ItemGroup` 所指定。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="3ce5c-136">保留現有的專案並建立 .NET Core 專案</span><span class="sxs-lookup"><span data-stu-id="3ce5c-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="3ce5c-137">如果現有的專案以較舊的架構為目標，您可能想要保持這些專案不變，使用 .NET Core 專案以未來的架構為目標。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![.NET Core 專案與現有專案位在不同的資料夾](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="3ce5c-139">**原始程式碼**</span><span class="sxs-lookup"><span data-stu-id="3ce5c-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="3ce5c-140">.NET Core 和現有的專案保存在不同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-140">The .NET Core and existing projects are kept in separate folders.</span></span> <span data-ttu-id="3ce5c-141">將專案保留在單獨的資料夾中可以避免強制您擁有 Visual Studio 2017 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-141">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="3ce5c-142">您可以建立不同的解決方案只開啟舊的專案。</span><span class="sxs-lookup"><span data-stu-id="3ce5c-142">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ce5c-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ce5c-143">See also</span></span>

- [<span data-ttu-id="3ce5c-144">.NET 核心移植文檔</span><span class="sxs-lookup"><span data-stu-id="3ce5c-144">.NET Core porting documentation</span></span>](index.md)
