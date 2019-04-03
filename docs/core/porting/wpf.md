---
title: 將 WPF 應用程式移植到 .NET Core 3.0
description: 教導您如何將 .NET Framework Windows Presentation Foundation 應用程式移植到適用於 Windows 的 .NET Core 3.0。
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 29ea308ee5147cfb18df312887e933615e349803
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2019
ms.locfileid: "58677546"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a><span data-ttu-id="cc019-103">作法：將 WPF 傳統型應用程式移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="cc019-103">How to: Port a WPF desktop app to .NET Core</span></span>

<span data-ttu-id="cc019-104">本文說明如何將 Windows Presentation Foundation (WPF) 傳統型應用程式從 .NET Framework 移植到 .NET Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="cc019-104">This article describes how to port your Windows Presentation Foundation-based (WPF) desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="cc019-105">.NET Core 3.0 SDK 支援 WPF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cc019-105">The .NET Core 3.0 SDK includes support for WPF applications.</span></span> <span data-ttu-id="cc019-106">WPF 仍然是僅限 Windows 的架構，只能在 Windows 上執行。</span><span class="sxs-lookup"><span data-stu-id="cc019-106">WPF is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="cc019-107">本範例使用 .NET Core SDK CLI 來建立和管理您的專案。</span><span class="sxs-lookup"><span data-stu-id="cc019-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="cc019-108">在此文章中，各種不同的名稱會用來識別用於移轉的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="cc019-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="cc019-109">在移轉您的專案時，您的檔案會有不同的名稱，因此請在心裡將它們與下面所列的項目進行比對：</span><span class="sxs-lookup"><span data-stu-id="cc019-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="cc019-110">檔案</span><span class="sxs-lookup"><span data-stu-id="cc019-110">File</span></span> | <span data-ttu-id="cc019-111">說明</span><span class="sxs-lookup"><span data-stu-id="cc019-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="cc019-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="cc019-112">**MyApps.sln**</span></span> | <span data-ttu-id="cc019-113">方案檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="cc019-113">The name of the solution file.</span></span> |
| <span data-ttu-id="cc019-114">**MyWPF.csproj**</span><span class="sxs-lookup"><span data-stu-id="cc019-114">**MyWPF.csproj**</span></span> | <span data-ttu-id="cc019-115">要移植的 .NET Framework WPF 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="cc019-115">The name of the .NET Framework WPF project to port.</span></span> |
| <span data-ttu-id="cc019-116">**MyWPFCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="cc019-116">**MyWPFCore.csproj**</span></span> | <span data-ttu-id="cc019-117">您所建立的新 .NET Core 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="cc019-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="cc019-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="cc019-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="cc019-119">.NET Core WPF 應用程式可執行檔。</span><span class="sxs-lookup"><span data-stu-id="cc019-119">The .NET Core WPF app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="cc019-120">必要條件</span><span class="sxs-lookup"><span data-stu-id="cc019-120">Prerequisites</span></span>

- <span data-ttu-id="cc019-121">適用於您想要執行之任何設計工具工作的 [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=wpf+core) 。</span><span class="sxs-lookup"><span data-stu-id="cc019-121">[Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=wpf+core) for any designer work you want to do.</span></span>

  <span data-ttu-id="cc019-122">安裝下列 Visual Studio 工作負載：</span><span class="sxs-lookup"><span data-stu-id="cc019-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="cc019-123">.NET 桌面開發</span><span class="sxs-lookup"><span data-stu-id="cc019-123">.NET desktop development</span></span>
  - <span data-ttu-id="cc019-124">.NET 跨平台開發</span><span class="sxs-lookup"><span data-stu-id="cc019-124">.NET cross-platform development</span></span>

- <span data-ttu-id="cc019-125">在解決方案中運作的 WPF 專案，可以毫無問題地建置並執行。</span><span class="sxs-lookup"><span data-stu-id="cc019-125">A working WPF project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="cc019-126">您的專案必須以 C# 進行編碼。</span><span class="sxs-lookup"><span data-stu-id="cc019-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="cc019-127">安裝最新的 [.NET Core 3.0](https://aka.ms/netcore3download) 預覽。</span><span class="sxs-lookup"><span data-stu-id="cc019-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>


>[!NOTE]
><span data-ttu-id="cc019-128">**Visual Studio 2017** 不支援 .NET Core 3.0 專案。</span><span class="sxs-lookup"><span data-stu-id="cc019-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="cc019-129">**Visual Studio 2019 預覽/RC** 支援 .NET Core 3.0 專案，但尚不支援 .NET Core 3.0 WPF 專案的視覺化設計工具。</span><span class="sxs-lookup"><span data-stu-id="cc019-129">**Visual Studio 2019 Preview/RC** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 WPF projects.</span></span> <span data-ttu-id="cc019-130">若要使用視覺化設計工具，您的解決方案中必須具有 .NET WPF project 專案，該專案與 .NET Core 專案共用其檔案。</span><span class="sxs-lookup"><span data-stu-id="cc019-130">To use the visual designer, you must have a .NET WPF project in your solution that shares its files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="cc019-131">Consider</span><span class="sxs-lookup"><span data-stu-id="cc019-131">Consider</span></span>

<span data-ttu-id="cc019-132">移植 .NET Framework WPF 應用程式時，您必須考量幾件事。</span><span class="sxs-lookup"><span data-stu-id="cc019-132">When porting a .NET Framework WPF application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="cc019-133">請檢查您的應用程式是否適合移轉。</span><span class="sxs-lookup"><span data-stu-id="cc019-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="cc019-134">使用 [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) 確定您的專案是否將移轉至 .NET Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="cc019-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="cc019-135">如果您的專案有.NET Core 3.0 的問題，則分析器可協助您找出這些問題。</span><span class="sxs-lookup"><span data-stu-id="cc019-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="cc019-136">您正在使用不同版本的 WPF。</span><span class="sxs-lookup"><span data-stu-id="cc019-136">You're using a different version of WPF.</span></span>

    <span data-ttu-id="cc019-137">當 .NET Core 3.0 Preview 1 發佈時，WPF 在 GitHub 上會開放原始碼。</span><span class="sxs-lookup"><span data-stu-id="cc019-137">When .NET Core 3.0 Preview 1 was released, WPF went open-source on GitHub.</span></span> <span data-ttu-id="cc019-138">.NET Core WPF 的程式碼是 .NET Framework WPF 程式碼基底的分支。</span><span class="sxs-lookup"><span data-stu-id="cc019-138">The code for .NET Core WPF is a fork of the .NET Framework WPF code base.</span></span> <span data-ttu-id="cc019-139">很可能存在一些差異，而您的應用程式將無法移植。</span><span class="sxs-lookup"><span data-stu-id="cc019-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="cc019-140">[Windows 相容性套件][compat-pack]可能有助於您移轉。</span><span class="sxs-lookup"><span data-stu-id="cc019-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="cc019-141">.NET Core 3.0 中不提供 .NET Framework 中提供的某些 API。</span><span class="sxs-lookup"><span data-stu-id="cc019-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="cc019-142">[Windows 相容性套件][compat-pack]新增了許多這些 API，可能有助於您的 WPF 應用程式與 .NET Core 相容。</span><span class="sxs-lookup"><span data-stu-id="cc019-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your WPF app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="cc019-143">更新專案所使用的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="cc019-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="cc019-144">在任何移轉之前使用最新版本的 NuGet 套件永遠是最好的作法。</span><span class="sxs-lookup"><span data-stu-id="cc019-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="cc019-145">如果您的應用程式會參考任何 NuGet 套件，請將它們更新為最新版本。</span><span class="sxs-lookup"><span data-stu-id="cc019-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="cc019-146">請確定您的應用程式建置成功。</span><span class="sxs-lookup"><span data-stu-id="cc019-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="cc019-147">升級後，如果有任何套件錯誤，請將套件降級為不會中斷程式碼的最新版本。</span><span class="sxs-lookup"><span data-stu-id="cc019-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="cc019-148">Visual Studio 2019 預覽 / RC 尚不支援.NET Core 3.0 的 WPF 設計工具</span><span class="sxs-lookup"><span data-stu-id="cc019-148">Visual Studio 2019 Preview/RC doesn't yet support the WPF Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="cc019-149">目前，如果要使用 Visual Studio 中的 WPF 設計工具，則需要保留現有的 .NET Framework WPF 專案檔案。</span><span class="sxs-lookup"><span data-stu-id="cc019-149">Currently, you need to keep your existing .NET Framework WPF project file if you want to use the WPF Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="cc019-150">建立新的 SDK 專案</span><span class="sxs-lookup"><span data-stu-id="cc019-150">Create a new SDK project</span></span>

<span data-ttu-id="cc019-151">您所建立的新 .NET Core 3.0 專案必須與 .NET Framework 專案位於不同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="cc019-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="cc019-152">如果它們都在相同的目錄中，則可能會與 **obj** 目錄中產生的檔案發生衝突。</span><span class="sxs-lookup"><span data-stu-id="cc019-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="cc019-153">在此範例中，您將在 **SolutionFolder** 目錄中建立名為 **MyWPFAppCore** 的目錄：</span><span class="sxs-lookup"><span data-stu-id="cc019-153">In this example, you'll create a directory named **MyWPFAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

<span data-ttu-id="cc019-154">接下來，您需要在 **MyWPFAppCore** 目錄中建立 **MyWPFCore.csproj** 專案。</span><span class="sxs-lookup"><span data-stu-id="cc019-154">Next, you need to create the **MyWPFCore.csproj** project in the **MyWPFAppCore** directory.</span></span> <span data-ttu-id="cc019-155">您可以使用選擇的文字編輯器以手動方式建立此檔案。</span><span class="sxs-lookup"><span data-stu-id="cc019-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="cc019-156">貼上下列 XML：</span><span class="sxs-lookup"><span data-stu-id="cc019-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="cc019-157">如果您不想以手動方式建立專案檔案，則您可以使用 Visual Studio 或 .NET Core SDK 產生專案。</span><span class="sxs-lookup"><span data-stu-id="cc019-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="cc019-158">但是，您必須刪除專案範本所產生的所有其他檔案，專案檔除外。</span><span class="sxs-lookup"><span data-stu-id="cc019-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="cc019-159">若要使用 SDK，請從 **SolutionFolder** 目錄執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="cc019-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

<span data-ttu-id="cc019-160">建立 **MyWPFCore.csproj** 後，您的目錄結構應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="cc019-160">After you create the **MyWPFCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

<span data-ttu-id="cc019-161">您需要使用 Visual Studio 或 **SolutionFolder** 目錄中的 .NET Core CLI，將 **MyWPFCore.csproj** 專案新增到 **MyApps.sln**：</span><span class="sxs-lookup"><span data-stu-id="cc019-161">You'll want to add the **MyWPFCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="cc019-162">修正組件資訊產生</span><span class="sxs-lookup"><span data-stu-id="cc019-162">Fix assembly info generation</span></span>

<span data-ttu-id="cc019-163">使用 .NET Framework 所建立的 Windows Presentation Foundation 專案包含 `AssemblyInfo.cs` 檔案，該檔案包含組件屬性，例如要產生的組件版本。</span><span class="sxs-lookup"><span data-stu-id="cc019-163">Windows Presentation Foundation projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="cc019-164">SDK 樣式專案會根據 SDK 專案檔自動為您產生此資訊。</span><span class="sxs-lookup"><span data-stu-id="cc019-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="cc019-165">同時具有兩種類型的「組件資訊」會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="cc019-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="cc019-166">藉由停用自動產生來解決此問題，這會強制專案使用現有的 `AssemblyInfo.cs` 檔案。</span><span class="sxs-lookup"><span data-stu-id="cc019-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="cc019-167">加入至主要 `<PropertyGroup>` 節點有三個設定。</span><span class="sxs-lookup"><span data-stu-id="cc019-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="cc019-168">**GenerateAssemblyInfo**\\</span><span class="sxs-lookup"><span data-stu-id="cc019-168">**GenerateAssemblyInfo**\\</span></span>
<span data-ttu-id="cc019-169">當您將此屬性設定為 `false`，它就不會產生組件屬性。</span><span class="sxs-lookup"><span data-stu-id="cc019-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="cc019-170">這可以避免與 .NET Framework 專案中的現有 `AssemblyInfo.cs` 檔案衝突。</span><span class="sxs-lookup"><span data-stu-id="cc019-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="cc019-171">**AssemblyName**\\</span><span class="sxs-lookup"><span data-stu-id="cc019-171">**AssemblyName**\\</span></span>
<span data-ttu-id="cc019-172">這個屬性的值是您在編譯時所建立的二進位輸出。</span><span class="sxs-lookup"><span data-stu-id="cc019-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="cc019-173">該名稱不需要加入副檔名。</span><span class="sxs-lookup"><span data-stu-id="cc019-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="cc019-174">例如，使用 `MyCoreApp` 產生 `MyCoreApp.exe`。</span><span class="sxs-lookup"><span data-stu-id="cc019-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="cc019-175">**RootNamespace**\\</span><span class="sxs-lookup"><span data-stu-id="cc019-175">**RootNamespace**\\</span></span>
<span data-ttu-id="cc019-176">專案使用的預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="cc019-176">The default namespace used by your project.</span></span> <span data-ttu-id="cc019-177">這應該與 .NET Framework 專案的預設命名空間相符。</span><span class="sxs-lookup"><span data-stu-id="cc019-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="cc019-178">將這三個元素新增至 `MyWPFCore.csproj` 檔案中的 `<PropertyGroup>` 節點：</span><span class="sxs-lookup"><span data-stu-id="cc019-178">Add these three elements to the `<PropertyGroup>` node in the `MyWPFCore.csproj` file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a><span data-ttu-id="cc019-179">加入原始程式碼</span><span class="sxs-lookup"><span data-stu-id="cc019-179">Add source code</span></span>
<span data-ttu-id="cc019-180">現在，**MyWPFCore.csproj** 專案不會進行編譯任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="cc019-180">Right now, the **MyWPFCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="cc019-181">根據預設，.NET Core 專案會自動包含目前目錄和任何子目錄中的所有原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="cc019-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="cc019-182">您必須使用相對路徑，將專案設定為包含 .NET Framework 專案中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="cc019-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="cc019-183">如果您的 .NET Framework 專案使用 **.resx** 檔案作為視窗和控制項的圖示和資源，那麼您還需要包含這些檔案。</span><span class="sxs-lookup"><span data-stu-id="cc019-183">If your .NET Framework project used **.resx** files for icons and resources for your windows and controls, you'll need to include those too.</span></span> 

<span data-ttu-id="cc019-184">第一個新增至專案所需的 `<ItemGroup>` 節點包含代表應用程式使用之啟動組態和資源 **App.xaml** 檔案。</span><span class="sxs-lookup"><span data-stu-id="cc019-184">The first `<ItemGroup>` node you need to add to your project includes the **App.xaml** file that represents the startup config and resources your app uses.</span></span> <span data-ttu-id="cc019-185">**App.xaml** 檔案也隨附一個 **App.xaml.cs**檔案，但它會自動包含在不同的 `<ItemGroup>` 中。</span><span class="sxs-lookup"><span data-stu-id="cc019-185">The **App.xaml** file also has an accompanying **App.xaml.cs** file, but it will be automatically included in a different `<ItemGroup>`.</span></span>

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

<span data-ttu-id="cc019-186">接著，將下列 `<ItemGroup>` 節點新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="cc019-186">Next, add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="cc019-187">每個陳述式都包含一個檔案 Glob 模式，其中包含子目錄。</span><span class="sxs-lookup"><span data-stu-id="cc019-187">Each statement includes a file glob pattern that includes child directories.</span></span> <span data-ttu-id="cc019-188">它包含您專案的原始程式碼、任何設定檔案和任何資源。</span><span class="sxs-lookup"><span data-stu-id="cc019-188">It includes the source code for your project, any settings files, and any resources.</span></span> <span data-ttu-id="cc019-189">**Obj** 目錄會遭到明確排除。</span><span class="sxs-lookup"><span data-stu-id="cc019-189">The **obj** directory is explicitly excluded.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="cc019-190">接下來，包括另一個 `<ItemGroup>` 節點，其中專案中的每個 **xaml** 檔案都含有一個 `<Page>` 項目，但 **App.xaml** 檔案除外。</span><span class="sxs-lookup"><span data-stu-id="cc019-190">Next, include another `<ItemGroup>` node that contains a `<Page>` entry for every **xaml** file in your project except the **App.xaml** file.</span></span> <span data-ttu-id="cc019-191">這些包含所有 **xaml** 格式的視窗、頁面和資源。</span><span class="sxs-lookup"><span data-stu-id="cc019-191">These contain all of the windows, pages, and resources that are in **xaml** format.</span></span> <span data-ttu-id="cc019-192">您無法在這裡使用 glob 模式，而且必須針對每個檔案新增一個項目，並指出使用了 `<Generator>`。</span><span class="sxs-lookup"><span data-stu-id="cc019-192">You cannot use a glob pattern here and must add an entry for every file and indicate the `<Generator>` used.</span></span>

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a><span data-ttu-id="cc019-193">新增 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="cc019-193">Add NuGet packages</span></span>

<span data-ttu-id="cc019-194">將 .NET Framework 專案參考的每個 NuGet 套件新增至 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="cc019-194">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="cc019-195">很可能您的 .NET Framework WPF 應用程式有一個 **packages.config** 檔案，其中包含您的專案所參考的 NuGet 套件的清單。</span><span class="sxs-lookup"><span data-stu-id="cc019-195">Most likely your .NET Framework WPF app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="cc019-196">您可以查看這份清單以判斷要新增至 .NET Core 專案的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="cc019-196">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="cc019-197">例如，如果 .NET Framework 專案參考 `MahApps.Metro` NuGet 封裝，則使用 Visual Studio 將其新增至專案。</span><span class="sxs-lookup"><span data-stu-id="cc019-197">For example, if the .NET Framework project references the `MahApps.Metro` NuGet package, add it to the project with Visual Studio.</span></span> <span data-ttu-id="cc019-198">您也可以使用 .NET Core CLI，從 **SolutionFolder** 目錄新增封裝參考：</span><span class="sxs-lookup"><span data-stu-id="cc019-198">You can also add the package reference with the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

<span data-ttu-id="cc019-199">上述命令會將下列 NuGet 參考新增到 **MyWPFCore.csproj** 專案中：</span><span class="sxs-lookup"><span data-stu-id="cc019-199">The previous command would add the following NuGet reference to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="cc019-200">編譯的問題</span><span class="sxs-lookup"><span data-stu-id="cc019-200">Problems compiling</span></span>

<span data-ttu-id="cc019-201">如果您在編譯專案時遇到問題，則您可能正在使用 .NET Framework 中提供但不適用於 .NET Core 的一些僅限 Windows 的 API。</span><span class="sxs-lookup"><span data-stu-id="cc019-201">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="cc019-202">您可以嘗試將 [Windows 相容性套件][compat-pack] NuGet 套件加入您的專案。</span><span class="sxs-lookup"><span data-stu-id="cc019-202">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="cc019-203">此套件只能在 Windows 上執行，並為 .NET Core 和 .NET Standard 專案新增了大約 20,000 個 Windows API。</span><span class="sxs-lookup"><span data-stu-id="cc019-203">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="cc019-204">上一個命令會將下列內容新增到 **MyWPFCore.csproj** 專案：</span><span class="sxs-lookup"><span data-stu-id="cc019-204">The previous command adds the following to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a><span data-ttu-id="cc019-205">WPF 設計工具</span><span class="sxs-lookup"><span data-stu-id="cc019-205">WPF Designer</span></span>

<span data-ttu-id="cc019-206">如本文所述，Visual Studio 2019 預覽/RC 僅支援 .NET Framework 專案中的 WPF 設計工具。</span><span class="sxs-lookup"><span data-stu-id="cc019-206">As detailed in this article, Visual Studio 2019 Preview/RC only supports the WPF Designer in .NET Framework projects.</span></span> <span data-ttu-id="cc019-207">藉由建立並排.NET Core 專案，您可以在使用 .NET Framework 專案設計表單時，同時使用 .NET Core 測試您的專案。</span><span class="sxs-lookup"><span data-stu-id="cc019-207">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="cc019-208">您的方案檔包含 .NET Framework 和 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="cc019-208">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="cc019-209">在 .NET Framework 專案中新增和設計您的表單和控制項，且根據我們新增至 .NET Core 專案的檔案 Glob 模式，任何新的或已變更的檔案將自動包含在 .NET Core 專案中。</span><span class="sxs-lookup"><span data-stu-id="cc019-209">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="cc019-210">一旦 Visual Studio 2019 支援 WPF Form 設計工具，您就可以將 .NET Core 專案檔案的內容複製/貼上到 .NET Framework 專案檔案中。</span><span class="sxs-lookup"><span data-stu-id="cc019-210">Once Visual Studio 2019 supports the WPF Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="cc019-211">然後刪除新增了 `<Source>` 和 `<EmbeddedResource>` 項目的檔案 Glob 模式。</span><span class="sxs-lookup"><span data-stu-id="cc019-211">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="cc019-212">修正應用程式所使用之任何專案參考的路徑。</span><span class="sxs-lookup"><span data-stu-id="cc019-212">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="cc019-213">這會有效地將 .NET Framework 專案升級至 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="cc019-213">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="cc019-214">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cc019-214">Next steps</span></span>

* <span data-ttu-id="cc019-215">深入了解 [Windows 相容性套件][compat-pack]。</span><span class="sxs-lookup"><span data-stu-id="cc019-215">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
* <span data-ttu-id="cc019-216">觀看[有關移植](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) .NET Framework WPF 專案到 .NET Core 的影片。</span><span class="sxs-lookup"><span data-stu-id="cc019-216">Watch a [video on porting](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) your .NET Framework WPF project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
