---
title: 組織適用於.NET Framework 和.NET Core 的專案
description: 協助想要同時針對 .NET Framework 及 .NET Core 編譯解決方案的專案擁有者。
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777338"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="91f9f-103">組織專案以同時支援 .NET Framework 及 .NET Core</span><span class="sxs-lookup"><span data-stu-id="91f9f-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="91f9f-104">您可以建立同時編譯 .NET Framework 和 .NET Core 的解決方案。</span><span class="sxs-lookup"><span data-stu-id="91f9f-104">You can create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="91f9f-105">本文涵蓋數個可協助您達成此目標的專案組織選項。</span><span class="sxs-lookup"><span data-stu-id="91f9f-105">This article covers several project-organization options to help you achieve this goal.</span></span> <span data-ttu-id="91f9f-106">以下是當您決定如何使用 .NET Core 設定專案配置時，要考慮的一些典型案例。</span><span class="sxs-lookup"><span data-stu-id="91f9f-106">Here are some typical scenarios to consider when you're deciding how to set up your project layout with .NET Core.</span></span> <span data-ttu-id="91f9f-107">此清單不一定涵蓋您想要的所有項目，根據專案需求決定優先順序。</span><span class="sxs-lookup"><span data-stu-id="91f9f-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="91f9f-108">**將現有的專案和 .NET Core 專案合併成單一專案**</span><span class="sxs-lookup"><span data-stu-id="91f9f-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="91f9f-109">*適用於︰*</span><span class="sxs-lookup"><span data-stu-id="91f9f-109">*What this is good for:*</span></span>
  - <span data-ttu-id="91f9f-110">藉由編譯單一專案，而不是每個以不同 .NET Framework 版本或平臺為目標的多個專案，來簡化您的組建程式。</span><span class="sxs-lookup"><span data-stu-id="91f9f-110">Simplifies your build process by compiling a single project rather than multiple projects that each target a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="91f9f-111">簡化多目標專案的來源檔案管理，因為您必須管理單一專案檔案。</span><span class="sxs-lookup"><span data-stu-id="91f9f-111">Simplifies source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="91f9f-112">新增或移除原始程式檔時，替代方案會要求您手動同步處理這些檔案與其他專案。</span><span class="sxs-lookup"><span data-stu-id="91f9f-112">When adding or removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="91f9f-113">輕鬆產生用於耗用量的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="91f9f-113">Easily generate a NuGet package for consumption.</span></span>
  - <span data-ttu-id="91f9f-114">讓您使用編譯器指示詞，在程式庫中針對特定的 .NET Framework 版本撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="91f9f-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="91f9f-115">*不支援的情節：*</span><span class="sxs-lookup"><span data-stu-id="91f9f-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="91f9f-116">需要開發人員使用 Visual Studio 2017 或更新版本來開啟現有的專案。</span><span class="sxs-lookup"><span data-stu-id="91f9f-116">Requires developers to use Visual Studio 2017 or a later version to open existing projects.</span></span> <span data-ttu-id="91f9f-117">若要支援舊版的 Visual Studio，[將專案檔放在不同的資料夾](#support-vs)是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="91f9f-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="91f9f-118">[**將現有的專案和新的 .NET Core 專案分開**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="91f9f-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="91f9f-119">*適用於︰*</span><span class="sxs-lookup"><span data-stu-id="91f9f-119">*What this is good for:*</span></span>
  - <span data-ttu-id="91f9f-120">針對可能沒有 Visual Studio 2017 或更新版本的開發人員和參與者，支援在現有專案上進行開發。</span><span class="sxs-lookup"><span data-stu-id="91f9f-120">Supports development on existing projects for developers and contributors who may not have Visual Studio 2017 or a later version.</span></span>
  - <span data-ttu-id="91f9f-121">降低在現有專案中建立新 bug 的可能性，因為這些專案不需要任何程式碼變換。</span><span class="sxs-lookup"><span data-stu-id="91f9f-121">Decreases the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="91f9f-122">範例</span><span class="sxs-lookup"><span data-stu-id="91f9f-122">Example</span></span>

<span data-ttu-id="91f9f-123">請考慮以下的儲存機制︰</span><span class="sxs-lookup"><span data-stu-id="91f9f-123">Consider the repository below:</span></span>

![現有專案](./media/project-structure/existing-project-structure.png)

<span data-ttu-id="91f9f-125">[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/) (原始程式碼)</span><span class="sxs-lookup"><span data-stu-id="91f9f-125">[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)</span></span>

<span data-ttu-id="91f9f-126">下列描述幾種方式以新增這個存放庫的 .NET Core 支援，視現有專案的條件約束和複雜性而定。</span><span class="sxs-lookup"><span data-stu-id="91f9f-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="91f9f-127">使用多目標 .NET Core 專案取代現有的專案</span><span class="sxs-lookup"><span data-stu-id="91f9f-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="91f9f-128">重新組織存放庫，以便移除任何現有的 *\*.csproj* 檔案，並建立以多個架構為目標的單一 *\*.csproj* 檔案。</span><span class="sxs-lookup"><span data-stu-id="91f9f-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="91f9f-129">這是很好的選擇，因為單一專案可以針對不同的架構進行編譯。</span><span class="sxs-lookup"><span data-stu-id="91f9f-129">This is a great option, because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="91f9f-130">它也可以處理個別目標架構的不同編譯選項及相依性。</span><span class="sxs-lookup"><span data-stu-id="91f9f-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![建立以多個架構為目標的 .csproj](./media/project-structure/multi-targeted-project.png)

<span data-ttu-id="91f9f-132">[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/) (原始程式碼)</span><span class="sxs-lookup"><span data-stu-id="91f9f-132">[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)</span></span>

<span data-ttu-id="91f9f-133">要注意的變更如下︰</span><span class="sxs-lookup"><span data-stu-id="91f9f-133">Changes to note are:</span></span>

- <span data-ttu-id="91f9f-134">以新的 [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj) 取代 *packages.config* 和 *\*.csproj*。</span><span class="sxs-lookup"><span data-stu-id="91f9f-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="91f9f-135">NuGet 套件是使用 `<PackageReference> ItemGroup` 所指定。</span><span class="sxs-lookup"><span data-stu-id="91f9f-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="91f9f-136">保留現有的專案並建立 .NET Core 專案</span><span class="sxs-lookup"><span data-stu-id="91f9f-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="91f9f-137">如果現有的專案以較舊的架構為目標，您可能想要保持這些專案不變，使用 .NET Core 專案以未來的架構為目標。</span><span class="sxs-lookup"><span data-stu-id="91f9f-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![.NET Core 專案與現有專案位在不同的資料夾](./media/project-structure/separate-projects-same-source.png)

<span data-ttu-id="91f9f-139">[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/) (原始程式碼)</span><span class="sxs-lookup"><span data-stu-id="91f9f-139">[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)</span></span>

<span data-ttu-id="91f9f-140">.NET Core 和現有的專案保存在不同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="91f9f-140">The .NET Core and existing projects are kept in separate folders.</span></span> <span data-ttu-id="91f9f-141">將專案保留在不同的資料夾中，可避免強制您擁有 Visual Studio 2017 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="91f9f-141">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="91f9f-142">您可以建立不同的解決方案只開啟舊的專案。</span><span class="sxs-lookup"><span data-stu-id="91f9f-142">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="91f9f-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="91f9f-143">See also</span></span>

- [<span data-ttu-id="91f9f-144">.NET Core 移植檔</span><span class="sxs-lookup"><span data-stu-id="91f9f-144">.NET Core porting documentation</span></span>](index.md)
