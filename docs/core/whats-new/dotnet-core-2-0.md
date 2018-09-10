---
title: .NET Core 2.0 的新功能
description: 了解 .NET Core 所提供的新功能。
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.openlocfilehash: 02aac2dab2b892927c0c98fae30bb287a6e24ad6
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44191049"
---
# <a name="whats-new-in-net-core-20"></a><span data-ttu-id="127b3-103">.NET Core 2.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="127b3-103">What's new in .NET Core 2.0</span></span>

<span data-ttu-id="127b3-104">.NET Core 2.0 包含針對下列區域的增強與新功能：</span><span class="sxs-lookup"><span data-stu-id="127b3-104">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="127b3-105">工具</span><span class="sxs-lookup"><span data-stu-id="127b3-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="127b3-106">語言支援</span><span class="sxs-lookup"><span data-stu-id="127b3-106">Language support</span></span>](#language-support)
- [<span data-ttu-id="127b3-107">平台改善</span><span class="sxs-lookup"><span data-stu-id="127b3-107">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="127b3-108">API 變更</span><span class="sxs-lookup"><span data-stu-id="127b3-108">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="127b3-109">Visual Studio 整合</span><span class="sxs-lookup"><span data-stu-id="127b3-109">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="127b3-110">文件改善</span><span class="sxs-lookup"><span data-stu-id="127b3-110">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="127b3-111">Tooling</span><span class="sxs-lookup"><span data-stu-id="127b3-111">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="127b3-112">dotnet restore 以隱含方式執行</span><span class="sxs-lookup"><span data-stu-id="127b3-112">dotnet restore runs implicitly</span></span>

<span data-ttu-id="127b3-113">在舊版的 .NET Core 中，您在使用 [dotnet new](../tools/dotnet-new.md) 命令建立新專案之後，以及將新的相依性新增至專案時，都必須立即執行 [dotnet restore](../tools/dotnet-restore.md) 命令以下載相依性。</span><span class="sxs-lookup"><span data-stu-id="127b3-113">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="127b3-114">您也可以透過將 `--no-restore` 參數傳遞至 `new`、`run`、`build`、`publish`、`pack`，以及 `test` 命令，來停用 `dotnet restore` 的自動引動過程。</span><span class="sxs-lookup"><span data-stu-id="127b3-114">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span>

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="127b3-115">將目標重定至 .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="127b3-115">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="127b3-116">如果已安裝 .NET Core 2.0 SDK，原先以 .NET Core 1.x 為目標的專案可以將目標重定至 .NET Core 2.0。</span><span class="sxs-lookup"><span data-stu-id="127b3-116">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="127b3-117">若要將目標重定至 .NET Core 2.0，請透過將 `<TargetFramework>` 元素 (在專案檔中具有多個目標的情況下則是 `<TargetFrameworks>` 元素) 的值從 1.x 變更至 2.0 來編輯專案檔：</span><span class="sxs-lookup"><span data-stu-id="127b3-117">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="127b3-118">您也可以用相同的方式，將目標從 .NET Standard 程式庫重定至 .NET Standard 2.0：</span><span class="sxs-lookup"><span data-stu-id="127b3-118">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="127b3-119">如需將專案移轉至 .NET Core 2.0 的詳細資訊，請參閱[從 ASP.NET Core 1.x 移轉至 ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index)。</span><span class="sxs-lookup"><span data-stu-id="127b3-119">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="127b3-120">語言支援</span><span class="sxs-lookup"><span data-stu-id="127b3-120">Language support</span></span>

<span data-ttu-id="127b3-121">.NET Core 2.0 除了支援 C# 和 F# 之外，也支援 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="127b3-121">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="127b3-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="127b3-122">Visual Basic</span></span>

<span data-ttu-id="127b3-123">.NET Core 2.0 現已支援 Visual Basic 2017。</span><span class="sxs-lookup"><span data-stu-id="127b3-123">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="127b3-124">您可以使用 Visual Basic 建立下列專案類型：</span><span class="sxs-lookup"><span data-stu-id="127b3-124">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="127b3-125">.NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="127b3-125">.NET Core console apps</span></span>
- <span data-ttu-id="127b3-126">.NET Core 類別庫</span><span class="sxs-lookup"><span data-stu-id="127b3-126">.NET Core class libraries</span></span>
- <span data-ttu-id="127b3-127">.NET Standard 類別庫</span><span class="sxs-lookup"><span data-stu-id="127b3-127">.NET Standard class libraries</span></span>
- <span data-ttu-id="127b3-128">.NET Core 單元測試專案</span><span class="sxs-lookup"><span data-stu-id="127b3-128">.NET Core unit test projects</span></span>
- <span data-ttu-id="127b3-129">.NET Core xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="127b3-129">.NET Core xUnit test projects</span></span>

<span data-ttu-id="127b3-130">例如，若要建立 Visual Basic "Hello World" 應用程式，請從命令列執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="127b3-130">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="127b3-131">開啟主控台視窗，建立專案的目錄，並將其設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="127b3-131">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="127b3-132">輸入 `dotnet new console -lang vb` 命令。</span><span class="sxs-lookup"><span data-stu-id="127b3-132">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="127b3-133">該命令會建立具有 `.vbproj` 副檔名的專案檔，以及名為 *Program.vb* 的 Visual Basic 原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="127b3-133">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="127b3-134">此檔案包含將 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="127b3-134">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="127b3-135">字串寫入至主控台視窗的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="127b3-135">to the console window.</span></span>

1. <span data-ttu-id="127b3-136">輸入 `dotnet run` 命令。</span><span class="sxs-lookup"><span data-stu-id="127b3-136">Enter the command `dotnet run`.</span></span> <span data-ttu-id="127b3-137">[.NET Core CLI](../tools/index.md) 會自動編譯並執行應用程式，該應用程式則會在主控台視窗中顯示 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="127b3-137">The [.NET Core CLI](../tools/index.md) automatically compiles and executes the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="127b3-138">。</span><span class="sxs-lookup"><span data-stu-id="127b3-138">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="127b3-139">針對 C# 7.1 的支援</span><span class="sxs-lookup"><span data-stu-id="127b3-139">Support for C# 7.1</span></span>

<span data-ttu-id="127b3-140">.NET Core 2.0 支援 C# 7.1，此版本加入了數個新的功能，包括：</span><span class="sxs-lookup"><span data-stu-id="127b3-140">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="127b3-141">`Main` 方法 (應用程式進入點) 可以使用 [async](../../csharp/language-reference/keywords/async.md) 關鍵字進行標記。</span><span class="sxs-lookup"><span data-stu-id="127b3-141">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="127b3-142">推斷的元組名稱。</span><span class="sxs-lookup"><span data-stu-id="127b3-142">Inferred tuple names.</span></span>
- <span data-ttu-id="127b3-143">預設運算式。</span><span class="sxs-lookup"><span data-stu-id="127b3-143">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="127b3-144">平台改善</span><span class="sxs-lookup"><span data-stu-id="127b3-144">Platform improvements</span></span>

<span data-ttu-id="127b3-145">.NET Core 2.0 包含可以更輕鬆地安裝 .NET Core 並在支援的作業系統上使用它的數個功能。</span><span class="sxs-lookup"><span data-stu-id="127b3-145">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="127b3-146">適用於 Linux 的 .NET Core 為單一實作</span><span class="sxs-lookup"><span data-stu-id="127b3-146">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="127b3-147">.NET Core 2.0 提供可在多個 Linux 發行版本上運作的單一 Linux 實作。</span><span class="sxs-lookup"><span data-stu-id="127b3-147">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="127b3-148">.NET Core 1.x 需要您下載發行版本特定的 Linux 實作。</span><span class="sxs-lookup"><span data-stu-id="127b3-148">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="127b3-149">您也可以開發以單一作業系統形式的 Linux 作為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="127b3-149">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="127b3-150">.NET Core 1.x 需要您個別以每個 Linux 發行版本作為目標。</span><span class="sxs-lookup"><span data-stu-id="127b3-150">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="127b3-151">針對 Apple 加密編譯程式庫的支援</span><span class="sxs-lookup"><span data-stu-id="127b3-151">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="127b3-152">.NET Core 1.x 在 macOS 上需要 OpenSSL 工具組的加密編譯程式庫。</span><span class="sxs-lookup"><span data-stu-id="127b3-152">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="127b3-153">.NET Core 2.0 使用 Apple 加密編譯程式庫，且不需要 OpenSSL，因此您已不必安裝它。</span><span class="sxs-lookup"><span data-stu-id="127b3-153">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="127b3-154">API 變更和程式庫支援</span><span class="sxs-lookup"><span data-stu-id="127b3-154">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="127b3-155">針對 .NET Standard 2.0 的支援</span><span class="sxs-lookup"><span data-stu-id="127b3-155">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="127b3-156">.NET Standard 會定義一組必須在符合該標準版本之 .NET 實作上提供的已建立版本 API。</span><span class="sxs-lookup"><span data-stu-id="127b3-156">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="127b3-157">.NET Standard 是以程式庫開發人員為目標。</span><span class="sxs-lookup"><span data-stu-id="127b3-157">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="127b3-158">它的目的在於針對每個 .NET 實作上以 .NET Standard 的某個版本為目標的程式庫，保證程式庫中所能使用的功能。</span><span class="sxs-lookup"><span data-stu-id="127b3-158">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="127b3-159">.NET Core 1.x 支援 .NET Standard 1.6 版，.NET Core 2.0 則支援最新 .NET Standard 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="127b3-159">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="127b3-160">如需詳細資訊，請參閱 [.NET Standard](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="127b3-160">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="127b3-161">除了 .NET Standard 1.6 原先所提供的 API 之外，.NET Standard 2.0 更包含了超過 20,000 個額外的 API。</span><span class="sxs-lookup"><span data-stu-id="127b3-161">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="127b3-162">我們主要是透過將 .NET Framework 和 Xamarin 的常見 API 合併至 .NET Standard，來對介面區進行擴展。</span><span class="sxs-lookup"><span data-stu-id="127b3-162">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="127b3-163">.NET Standard 2.0 類別庫也可以參考 .NET Framework 類別庫，前提是這些類別庫必須呼叫存在於 .NET Standard 2.0 中的 API。</span><span class="sxs-lookup"><span data-stu-id="127b3-163">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="127b3-164">不需要對 .NET Framework 程式庫進行任何重新編譯。</span><span class="sxs-lookup"><span data-stu-id="127b3-164">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="127b3-165">如需於 .NET Standard 1.6 之後新增至 .NET Standard 的 API 清單，請參閱 [.NET Standard 2.0 與1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="127b3-165">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="127b3-166">擴展的介面區</span><span class="sxs-lookup"><span data-stu-id="127b3-166">Expanded surface area</span></span>

<span data-ttu-id="127b3-167">.NET Core 2.0 上的可用 API 總數，比 .NET Core 1.1 所提供的 API 多出了超過一倍的數量。</span><span class="sxs-lookup"><span data-stu-id="127b3-167">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="127b3-168">而從 .NET Framework 移植 [Windows 相容性套件](../porting/windows-compat-pack.md)也會變得簡單許多。</span><span class="sxs-lookup"><span data-stu-id="127b3-168">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="127b3-169">針對 .NET Framework 程式庫的支援</span><span class="sxs-lookup"><span data-stu-id="127b3-169">Support for .NET Framework libraries</span></span>

<span data-ttu-id="127b3-170">.NET Core 程式碼可以參考現有的 .NET Framework 程式庫，包括現有的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="127b3-170">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="127b3-171">請注意，程式庫必須使用 .NET Standard 所提供的 API。</span><span class="sxs-lookup"><span data-stu-id="127b3-171">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="127b3-172">Visual Studio 整合</span><span class="sxs-lookup"><span data-stu-id="127b3-172">Visual Studio integration</span></span>

<span data-ttu-id="127b3-173">Visual Studio 2017 15.3 版 (以及某些情況下的 Visual Studio for Mac) 能為 .NET Core 開發人員提供數個顯著的增強功能。</span><span class="sxs-lookup"><span data-stu-id="127b3-173">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="127b3-174">重定 .NET Core 應用程式和 .NET Standard 程式庫的目標</span><span class="sxs-lookup"><span data-stu-id="127b3-174">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="127b3-175">如果已安裝 .NET Core 2.0 SDK，您可以將 .NET Core 1.x 專案的目標重定至 .NET Core 2.0，並將 .NET Standard 1.x 程式庫的目標重定至 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="127b3-175">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="127b3-176">若要在 Visual Studio 中重定專案的目標，請開啟專案屬性對話方塊的 [應用程式] 索引標籤，並將 [目標 Framework] 的值變更為 [.NET Core 2.0] 或 [.NET Standard 2.0]。</span><span class="sxs-lookup"><span data-stu-id="127b3-176">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="127b3-177">另一個變更它的方法，則是以滑鼠右鍵按一下專案並選取 [編輯 \*.csproj 檔案] 選項。</span><span class="sxs-lookup"><span data-stu-id="127b3-177">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="127b3-178">如需詳細資訊，請參閱本主題稍早的[工具](#tooling)小節。</span><span class="sxs-lookup"><span data-stu-id="127b3-178">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="127b3-179">.NET Core 的即時單元測試支援</span><span class="sxs-lookup"><span data-stu-id="127b3-179">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="127b3-180">每當您修改程式碼時，Live Unit Testing 會在背景自動執行任何受影響的單元測試，並會在 Visual Studio 環境中呈現即時的結果和程式碼涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="127b3-180">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="127b3-181">.NET Core 2.0 現已支援 Live Unit Testing。</span><span class="sxs-lookup"><span data-stu-id="127b3-181">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="127b3-182">先前 Live Unit Testing 僅針對 .NET Framework 應用程式提供。</span><span class="sxs-lookup"><span data-stu-id="127b3-182">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="127b3-183">如需詳細資訊，請參閱 [Visual Studio 2017 的 Live Unit Testing](/visualstudio/test/live-unit-testing) 及 [Live Unit Testing 常見問題集](/visualstudio/test/live-unit-testing-faq)。</span><span class="sxs-lookup"><span data-stu-id="127b3-183">For more information, see [Live Unit Testing with Visual Studio 2017](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="127b3-184">更佳的多目標 Framework 支援</span><span class="sxs-lookup"><span data-stu-id="127b3-184">Better support for multiple target frameworks</span></span>

<span data-ttu-id="127b3-185">如果您正在針對多目標 Framework 建置專案，現在已可以從最上層功能表選取目標平台。</span><span class="sxs-lookup"><span data-stu-id="127b3-185">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="127b3-186">在下圖中，名為 SCD1 的專案是以 64 位元的 macOS X 10.11 (`osx.10.11-x64`)，以及 64 位元的 Windows 10/Windows Server 2016 (`win10-x64`) 為目標。</span><span class="sxs-lookup"><span data-stu-id="127b3-186">In the following figure, a project named SCD1 targets 64-bit macOS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="127b3-187">您可以在選取專案按鈕 (在此情況下為執行偵錯組建) 之前選取目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="127b3-187">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![於建置專案時選取目標 Framework](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="127b3-189">針對 .NET Core SDK 的並存功能支援</span><span class="sxs-lookup"><span data-stu-id="127b3-189">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="127b3-190">您現在可以獨立於 Visual Studio 安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="127b3-190">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="127b3-191">這可以讓單一版本的 Visual Studio 建置以不同 .NET Core 版本為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="127b3-191">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="127b3-192">在此之前，Visual Studio 和 .NET Core SDK 必須緊密關聯，只有特定版本的 SDK 才能搭配特定版本的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="127b3-192">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="127b3-193">文件改善</span><span class="sxs-lookup"><span data-stu-id="127b3-193">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="127b3-194">.NET 應用程式架構</span><span class="sxs-lookup"><span data-stu-id="127b3-194">.NET Application Architecture</span></span>

<span data-ttu-id="127b3-195">[.NET 應用程式架構](https://www.microsoft.com/net/learn/architecture)可讓您存取一系列針對使用 .NET 進行建置提供指引、最佳做法和範例應用程式的電子書：</span><span class="sxs-lookup"><span data-stu-id="127b3-195">[.NET Application Architecture](https://www.microsoft.com/net/learn/architecture) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- [<span data-ttu-id="127b3-196">微服務和 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="127b3-196">Microservices and Docker containers</span></span>](../../standard/microservices-architecture/index.md)
- [<span data-ttu-id="127b3-197">使用 ASP.NET 的 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="127b3-197">Web applications with ASP.NET</span></span>](../../standard/modern-web-apps-azure-architecture/index.md)
- [<span data-ttu-id="127b3-198">使用 Xamarin 的行動應用程式</span><span class="sxs-lookup"><span data-stu-id="127b3-198">Mobile applications with Xamarin</span></span>](/xamarin/xamarin-forms/enterprise-application-patterns/index.md)
- [<span data-ttu-id="127b3-199">使用 Azure 部署至雲端的應用程式</span><span class="sxs-lookup"><span data-stu-id="127b3-199">Applications that are deployed to the Cloud with Azure</span></span>](/azure/architecture/reference-architectures/index.md)

## <a name="see-also"></a><span data-ttu-id="127b3-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="127b3-200">See also</span></span>

* [<span data-ttu-id="127b3-201">ASP.NET Core 2.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="127b3-201">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)
