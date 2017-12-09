---
title: "組織專案以支援 .NET Framework 及 .NET Core"
description: "協助想要同時針對 .NET Framework 及 .NET Core 編譯解決方案的專案擁有者。"
keywords: ".NET, .NET Core, .NET Framework, 專案配置, 多個架構"
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
ms.openlocfilehash: 93bec65e3bbee93855d6f5bce5e2d6cea8bb9f3d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a><span data-ttu-id="685c8-104">組織專案以支援 .NET Framework 及 .NET Core</span><span class="sxs-lookup"><span data-stu-id="685c8-104">Organizing your project to support .NET Framework and .NET Core</span></span>

<span data-ttu-id="685c8-105">本文可協助想要同時針對 .NET Framework 及 .NET Core 編譯解決方案的專案擁有者。</span><span class="sxs-lookup"><span data-stu-id="685c8-105">This article helps project owners who want to compile their solution against .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="685c8-106">它提供數個選項，組織專案以協助開發人員達成此目標。</span><span class="sxs-lookup"><span data-stu-id="685c8-106">It provides several options to organize projects to help developers achieve this goal.</span></span> <span data-ttu-id="685c8-107">下列清單提供當您決定如何使用 .NET Core 設定專案配置時，要考量的一些典型案例。</span><span class="sxs-lookup"><span data-stu-id="685c8-107">The following list provides some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="685c8-108">此清單不一定涵蓋您想要的所有項目，根據專案需求決定優先順序。</span><span class="sxs-lookup"><span data-stu-id="685c8-108">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* <span data-ttu-id="685c8-109">[**將現有的專案和 .NET Core 專案合併成單一專案**][option-csproj]</span><span class="sxs-lookup"><span data-stu-id="685c8-109">[**Combine existing projects and .NET Core projects into single projects**][option-csproj]</span></span>

  <span data-ttu-id="685c8-110">*適用於︰*</span><span class="sxs-lookup"><span data-stu-id="685c8-110">*What this is good for:*</span></span>
  * <span data-ttu-id="685c8-111">藉由編譯單一專案而非編譯多個專案，每個都會以不同的 .NET Framework 版本或平台為目標，以簡化建置流程。</span><span class="sxs-lookup"><span data-stu-id="685c8-111">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="685c8-112">因為您必須管理單一專案檔，所以簡化多目標專案的來源檔案管理。</span><span class="sxs-lookup"><span data-stu-id="685c8-112">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="685c8-113">新增/移除來源檔案時，替代方案需要您手動同步處理這些專案與其他專案。</span><span class="sxs-lookup"><span data-stu-id="685c8-113">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="685c8-114">輕鬆產生 NuGet 封裝以供耗用。</span><span class="sxs-lookup"><span data-stu-id="685c8-114">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="685c8-115">讓您使用編譯器指示詞，在程式庫中針對特定的 .NET Framework 版本撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="685c8-115">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="685c8-116">*不支援的情節：*</span><span class="sxs-lookup"><span data-stu-id="685c8-116">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="685c8-117">需要開發人員使用 Visual Studio 2017 開啟現有的專案。</span><span class="sxs-lookup"><span data-stu-id="685c8-117">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="685c8-118">若要支援舊版的 Visual Studio，[將專案檔放在不同的資料夾](#support-vs)是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="685c8-118">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="685c8-119">[**將現有的專案和新的 .NET Core 專案分開**][option-csproj-folder]</span><span class="sxs-lookup"><span data-stu-id="685c8-119">[**Keep existing projects and new .NET Core projects separate**][option-csproj-folder]</span></span>

  <span data-ttu-id="685c8-120">*適用於︰*</span><span class="sxs-lookup"><span data-stu-id="685c8-120">*What this is good for:*</span></span>
  * <span data-ttu-id="685c8-121">繼續支援現有專案的開發，但不必升級可能沒有 Visual Studio 2017 的開發人員/參與者。</span><span class="sxs-lookup"><span data-stu-id="685c8-121">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="685c8-122">減少現有專案中製造新Bug 的可能性，因為這些專案不需要任何程式碼變換。</span><span class="sxs-lookup"><span data-stu-id="685c8-122">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="685c8-123">範例</span><span class="sxs-lookup"><span data-stu-id="685c8-123">Example</span></span>

<span data-ttu-id="685c8-124">請考慮以下的儲存機制︰</span><span class="sxs-lookup"><span data-stu-id="685c8-124">Consider the repository below:</span></span>

<span data-ttu-id="685c8-125">![現有專案][example-initial-project]</span><span class="sxs-lookup"><span data-stu-id="685c8-125">![Existing project][example-initial-project]</span></span>

<span data-ttu-id="685c8-126">[**原始程式碼**][example-initial-project-code]</span><span class="sxs-lookup"><span data-stu-id="685c8-126">[**Source Code**][example-initial-project-code]</span></span>

<span data-ttu-id="685c8-127">下列描述幾種方式以新增這個存放庫的 .NET Core 支援，視現有專案的條件約束和複雜性而定。</span><span class="sxs-lookup"><span data-stu-id="685c8-127">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="685c8-128">使用多目標 .NET Core 專案取代現有的專案</span><span class="sxs-lookup"><span data-stu-id="685c8-128">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="685c8-129">重新組織存放庫，以便移除任何現有的 *\*.csproj* 檔案，並建立以多個架構為目標的單一 *\*.csproj* 檔案。</span><span class="sxs-lookup"><span data-stu-id="685c8-129">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="685c8-130">這是很不錯的選擇，因為單一專案能夠編譯不同的架構。</span><span class="sxs-lookup"><span data-stu-id="685c8-130">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="685c8-131">它也可以處理個別目標架構的不同編譯選項及相依性。</span><span class="sxs-lookup"><span data-stu-id="685c8-131">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

<span data-ttu-id="685c8-132">![建立以多個架構為目標的 csproj][example-csproj]</span><span class="sxs-lookup"><span data-stu-id="685c8-132">![Create an csproj that targets multiple frameworks][example-csproj]</span></span>

<span data-ttu-id="685c8-133">[**原始程式碼**][example-csproj-code]</span><span class="sxs-lookup"><span data-stu-id="685c8-133">[**Source Code**][example-csproj-code]</span></span>

<span data-ttu-id="685c8-134">要注意的變更如下︰</span><span class="sxs-lookup"><span data-stu-id="685c8-134">Changes to note are:</span></span>
* <span data-ttu-id="685c8-135">將 *packages.config* 和 *\*.csproj* 取代為新的 [.NET Core *\*.csproj*][example-csproj-netcore]。</span><span class="sxs-lookup"><span data-stu-id="685c8-135">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*][example-csproj-netcore].</span></span> <span data-ttu-id="685c8-136">NuGet 套件是使用 `<PackageReference> ItemGroup` 所指定。</span><span class="sxs-lookup"><span data-stu-id="685c8-136">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="685c8-137">保留現有的專案並建立 .NET Core 專案</span><span class="sxs-lookup"><span data-stu-id="685c8-137">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="685c8-138">如果現有的專案以較舊的架構為目標，您可能想要保持這些專案不變，使用 .NET Core 專案以未來的架構為目標。</span><span class="sxs-lookup"><span data-stu-id="685c8-138">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

<span data-ttu-id="685c8-139">![在不同資料夾中有現有專案的 .NET Core 專案][example-csproj-different-folder]</span><span class="sxs-lookup"><span data-stu-id="685c8-139">![.NET Core project with existing project in different folder][example-csproj-different-folder]</span></span>

<span data-ttu-id="685c8-140">[**原始程式碼**][example-csproj-different-code]</span><span class="sxs-lookup"><span data-stu-id="685c8-140">[**Source Code**][example-csproj-different-code]</span></span>

<span data-ttu-id="685c8-141">要注意的變更如下︰</span><span class="sxs-lookup"><span data-stu-id="685c8-141">Changes to note are:</span></span>
* <span data-ttu-id="685c8-142">.NET Core 和現有的專案保存在不同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="685c8-142">The .NET Core and existing projects are kept in separate folders.</span></span>
    * <span data-ttu-id="685c8-143">將專案放在不同的資料夾中，可避免強迫使用 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="685c8-143">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="685c8-144">您可以建立不同的解決方案只開啟舊的專案。</span><span class="sxs-lookup"><span data-stu-id="685c8-144">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="685c8-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="685c8-145">See Also</span></span>

<span data-ttu-id="685c8-146">如需移轉至 .NET Core 的詳細指引，請參閱 [.NET Core 移植文件][porting-doc]。</span><span class="sxs-lookup"><span data-stu-id="685c8-146">Please see the [.NET Core porting documentation][porting-doc] for more guidance on migrating to .NET Core.</span></span>

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "現有專案"
[example-initial-project-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "建立以多個架構為目標的 csproj"
[example-csproj-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "在不同資料夾中有現有 PCL 的 .NET Core 專案"
[example-csproj-different-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
