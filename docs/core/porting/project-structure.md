---
title: 組織適用於.NET Framework 和.NET Core 的專案
description: 協助想要同時針對 .NET Framework 及 .NET Core 編譯解決方案的專案擁有者。
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 57bb766f1d91c502a508b6362dc642310009c8c4
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904016"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="e080b-103">組織專案以同時支援 .NET Framework 及 .NET Core</span><span class="sxs-lookup"><span data-stu-id="e080b-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="e080b-104">了解如何建立一個並行編譯 .NET Framework 和 .NET Core 的解決方案。</span><span class="sxs-lookup"><span data-stu-id="e080b-104">Learn how to create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="e080b-105">請參閱數個選項，以組織專案來協助開發人員達成此目標。</span><span class="sxs-lookup"><span data-stu-id="e080b-105">See several options to organize projects to help you achieve this goal.</span></span> <span data-ttu-id="e080b-106">以下是當您決定如何使用 .NET Core 設定專案配置時，要考量的一些典型案例。</span><span class="sxs-lookup"><span data-stu-id="e080b-106">Here are some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="e080b-107">此清單不一定涵蓋您想要的所有項目，根據專案需求決定優先順序。</span><span class="sxs-lookup"><span data-stu-id="e080b-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* [<span data-ttu-id="e080b-108">**將現有的專案和 .NET Core 專案合併成單一專案**</span><span class="sxs-lookup"><span data-stu-id="e080b-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="e080b-109">*適用於︰*</span><span class="sxs-lookup"><span data-stu-id="e080b-109">*What this is good for:*</span></span>
  * <span data-ttu-id="e080b-110">藉由編譯單一專案而非編譯多個專案，每個都會以不同的 .NET Framework 版本或平台為目標，以簡化建置流程。</span><span class="sxs-lookup"><span data-stu-id="e080b-110">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="e080b-111">因為您必須管理單一專案檔，所以簡化多目標專案的來源檔案管理。</span><span class="sxs-lookup"><span data-stu-id="e080b-111">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="e080b-112">新增/移除來源檔案時，替代方案需要您手動同步處理這些專案與其他專案。</span><span class="sxs-lookup"><span data-stu-id="e080b-112">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="e080b-113">輕鬆產生 NuGet 封裝以供耗用。</span><span class="sxs-lookup"><span data-stu-id="e080b-113">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="e080b-114">讓您使用編譯器指示詞，在程式庫中針對特定的 .NET Framework 版本撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="e080b-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="e080b-115">*不支援的情節：*</span><span class="sxs-lookup"><span data-stu-id="e080b-115">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="e080b-116">需要開發人員使用 Visual Studio 2017 開啟現有的專案。</span><span class="sxs-lookup"><span data-stu-id="e080b-116">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="e080b-117">若要支援舊版的 Visual Studio，[將專案檔放在不同的資料夾](#support-vs)是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="e080b-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="e080b-118">[**將現有的專案和新的 .NET Core 專案分開**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="e080b-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="e080b-119">*適用於︰*</span><span class="sxs-lookup"><span data-stu-id="e080b-119">*What this is good for:*</span></span>
  * <span data-ttu-id="e080b-120">繼續支援現有專案的開發，但不必升級可能沒有 Visual Studio 2017 的開發人員/參與者。</span><span class="sxs-lookup"><span data-stu-id="e080b-120">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="e080b-121">減少現有專案中製造新Bug 的可能性，因為這些專案不需要任何程式碼變換。</span><span class="sxs-lookup"><span data-stu-id="e080b-121">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="e080b-122">範例</span><span class="sxs-lookup"><span data-stu-id="e080b-122">Example</span></span>

<span data-ttu-id="e080b-123">請考慮以下的儲存機制︰</span><span class="sxs-lookup"><span data-stu-id="e080b-123">Consider the repository below:</span></span>

![現有專案](media/project-structure/project.png)

<span data-ttu-id="e080b-125">[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/) (原始程式碼)</span><span class="sxs-lookup"><span data-stu-id="e080b-125">[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)</span></span>

<span data-ttu-id="e080b-126">下列描述幾種方式以新增這個存放庫的 .NET Core 支援，視現有專案的條件約束和複雜性而定。</span><span class="sxs-lookup"><span data-stu-id="e080b-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="e080b-127">使用多目標 .NET Core 專案取代現有的專案</span><span class="sxs-lookup"><span data-stu-id="e080b-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="e080b-128">重新組織存放庫，以便移除任何現有的 *\*.csproj* 檔案，並建立以多個架構為目標的單一 *\*.csproj* 檔案。</span><span class="sxs-lookup"><span data-stu-id="e080b-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="e080b-129">這是很不錯的選擇，因為單一專案能夠編譯不同的架構。</span><span class="sxs-lookup"><span data-stu-id="e080b-129">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="e080b-130">它也可以處理個別目標架構的不同編譯選項及相依性。</span><span class="sxs-lookup"><span data-stu-id="e080b-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![建立以多個架構為目標的 csproj](media/project-structure/project.csproj.png)

<span data-ttu-id="e080b-132">[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/) (原始程式碼)</span><span class="sxs-lookup"><span data-stu-id="e080b-132">[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)</span></span>

<span data-ttu-id="e080b-133">要注意的變更如下︰</span><span class="sxs-lookup"><span data-stu-id="e080b-133">Changes to note are:</span></span>

* <span data-ttu-id="e080b-134">以新的 [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj) 取代 *packages.config* 和 *\*.csproj*。</span><span class="sxs-lookup"><span data-stu-id="e080b-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="e080b-135">NuGet 套件是使用 `<PackageReference> ItemGroup` 所指定。</span><span class="sxs-lookup"><span data-stu-id="e080b-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="e080b-136">保留現有的專案並建立 .NET Core 專案</span><span class="sxs-lookup"><span data-stu-id="e080b-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="e080b-137">如果現有的專案以較舊的架構為目標，您可能想要保持這些專案不變，使用 .NET Core 專案以未來的架構為目標。</span><span class="sxs-lookup"><span data-stu-id="e080b-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![.NET Core 專案與現有專案位在不同的資料夾](media/project-structure/project.csproj.different.png)

<span data-ttu-id="e080b-139">[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/) (原始程式碼)</span><span class="sxs-lookup"><span data-stu-id="e080b-139">[**Source Code**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)</span></span>

<span data-ttu-id="e080b-140">要注意的變更如下︰</span><span class="sxs-lookup"><span data-stu-id="e080b-140">Changes to note are:</span></span>

* <span data-ttu-id="e080b-141">.NET Core 和現有的專案保存在不同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="e080b-141">The .NET Core and existing projects are kept in separate folders.</span></span>
  * <span data-ttu-id="e080b-142">將專案放在不同的資料夾中，可避免強迫使用 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="e080b-142">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="e080b-143">您可以建立不同的解決方案只開啟舊的專案。</span><span class="sxs-lookup"><span data-stu-id="e080b-143">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="e080b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e080b-144">See also</span></span>

<span data-ttu-id="e080b-145">如需移轉至 .NET Core 的詳細指導，請參閱 [.NET Core 移植文件](index.md)。</span><span class="sxs-lookup"><span data-stu-id="e080b-145">Please see the [.NET Core porting documentation](index.md) for more guidance on migrating to .NET Core.</span></span>
