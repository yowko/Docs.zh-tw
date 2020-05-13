---
title: .NET Core 3.0 的新功能
description: 了解 .NET Core 3.0 所提供的新功能。
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: 422cb7b20e2644ab44f9573f101fb6b53ab1dd2f
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378829"
---
# <a name="whats-new-in-net-core-30"></a><span data-ttu-id="e9feb-103">.NET Core 3.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="e9feb-103">What's new in .NET Core 3.0</span></span>

<span data-ttu-id="e9feb-104">本文說明 .NET Core 3.0 中的新功能。</span><span class="sxs-lookup"><span data-stu-id="e9feb-104">This article describes what is new in .NET Core 3.0.</span></span> <span data-ttu-id="e9feb-105">其中一個最大的增強功能是對 Windows 傳統型應用程式的支援 (僅限 Windows)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="e9feb-106">您可以使用 .NET Core 3.0 SDK 元件「Windows 傳統型」來移植 Windows Forms 和 Windows Presentation Foundation (WPF) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9feb-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="e9feb-107">具體而言，只有在 Windows 上才支援並包含「Windows 傳統型」元件。</span><span class="sxs-lookup"><span data-stu-id="e9feb-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="e9feb-108">如需詳細資訊，請參閱本文稍後的 [Windows 傳統型](#windows-desktop)一節。</span><span class="sxs-lookup"><span data-stu-id="e9feb-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="e9feb-109">.NET Core 3.0 新增 C# 8.0 支援。</span><span class="sxs-lookup"><span data-stu-id="e9feb-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="e9feb-110">強烈建議您使用[Visual Studio 2019 16.3 版](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或更新版本， [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview)或更新版本，或使用最新的**c # 擴充**功能[Visual Studio Code](https://code.visualstudio.com/) 。</span><span class="sxs-lookup"><span data-stu-id="e9feb-110">It's highly recommended that you use [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or newer, [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview) or newer, or [Visual Studio Code](https://code.visualstudio.com/) with the latest **C# extension**.</span></span>

<span data-ttu-id="e9feb-111">立即在 Windows、macOS 或 Linux 上[下載並開始使用 .Net Core 3.0](https://aka.ms/netcore3download) 。</span><span class="sxs-lookup"><span data-stu-id="e9feb-111">[Download and get started with .NET Core 3.0](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="e9feb-112">如需版本的詳細資訊，請參閱[.Net Core 3.0 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-112">For more information about the release, see the [.NET Core 3.0 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span></span>

<span data-ttu-id="e9feb-113">.NET Core RC1 被視為 Microsoft 準備好的生產環境，並受到完整支援。</span><span class="sxs-lookup"><span data-stu-id="e9feb-113">.NET Core RC1 was considered production ready by Microsoft and was fully supported.</span></span> <span data-ttu-id="e9feb-114">如果您使用的是預覽版本，您必須移至 RTM 版本以繼續支援。</span><span class="sxs-lookup"><span data-stu-id="e9feb-114">If you're using a preview release, you must move to the RTM version for continued support.</span></span>

## <a name="language-improvements-c-80"></a><span data-ttu-id="e9feb-115">語言增強功能 c # 8。0</span><span class="sxs-lookup"><span data-stu-id="e9feb-115">Language improvements C# 8.0</span></span>

<span data-ttu-id="e9feb-116">C # 8.0 也是此版本的一部分，其中包括[可為 null 的參考型別](../../csharp/tutorials/nullable-reference-types.md)功能、[非同步資料流程](../../csharp/tutorials/generate-consume-asynchronous-stream.md)和[其他模式](../../csharp/tutorials/pattern-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-116">C# 8.0 is also part of this release, which includes the [nullable reference types](../../csharp/tutorials/nullable-reference-types.md) feature, [async streams](../../csharp/tutorials/generate-consume-asynchronous-stream.md), and [more patterns](../../csharp/tutorials/pattern-matching.md).</span></span> <span data-ttu-id="e9feb-117">如需 C# 8.0 功能的詳細資訊，請參閱 [C# 8.0 的新功能](../../csharp/whats-new/csharp-8.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-117">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

<span data-ttu-id="e9feb-118">已新增語言增強功能，以支援以下詳述的下列 API 功能：</span><span class="sxs-lookup"><span data-stu-id="e9feb-118">Language enhancements were added to support the following API features detailed below:</span></span>

- [<span data-ttu-id="e9feb-119">範圍和索引</span><span class="sxs-lookup"><span data-stu-id="e9feb-119">Ranges and indices</span></span>](#ranges-and-indices)
- [<span data-ttu-id="e9feb-120">非同步資料流</span><span class="sxs-lookup"><span data-stu-id="e9feb-120">Async streams</span></span>](#async-streams)

## <a name="net-standard-21"></a><span data-ttu-id="e9feb-121">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="e9feb-121">.NET Standard 2.1</span></span>

<span data-ttu-id="e9feb-122">.NET Core 3.0 會實行 **.NET Standard 2.1**。</span><span class="sxs-lookup"><span data-stu-id="e9feb-122">.NET Core 3.0 implements **.NET Standard 2.1**.</span></span> <span data-ttu-id="e9feb-123">不過，預設 `dotnet new classlib` 範本會產生仍以 **.NET Standard 2.0**為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="e9feb-123">However, the default `dotnet new classlib` template generates a project that still targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="e9feb-124">若要以 **.NET Standard 2.1** 為目標，請編輯您的專案檔並將 `TargetFramework` 屬性變更為 `netstandard2.1`：</span><span class="sxs-lookup"><span data-stu-id="e9feb-124">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="e9feb-125">如果目前使用 Visual Studio，您需要 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)，因為 Visual Studio 2017 不支援 **.NET Standard 2.1** 或 **.NET Core 3.0**。</span><span class="sxs-lookup"><span data-stu-id="e9feb-125">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="compiledeploy"></a><span data-ttu-id="e9feb-126">編譯/部署</span><span class="sxs-lookup"><span data-stu-id="e9feb-126">Compile/Deploy</span></span>

### <a name="default-executables"></a><span data-ttu-id="e9feb-127">預設可執行檔</span><span class="sxs-lookup"><span data-stu-id="e9feb-127">Default executables</span></span>

<span data-ttu-id="e9feb-128">.NET Core 現在預設會建立[執行時間相依的可執行檔](../deploying/index.md#publish-runtime-dependent)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-128">.NET Core now builds [runtime-dependent executables](../deploying/index.md#publish-runtime-dependent) by default.</span></span> <span data-ttu-id="e9feb-129">這對於使用 .NET Core 全域安裝版本的應用程式來說，是一項新行為。</span><span class="sxs-lookup"><span data-stu-id="e9feb-129">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="e9feb-130">先前，只有[獨立式部署](../deploying/index.md#publish-self-contained)會產生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="e9feb-130">Previously, only [self-contained deployments](../deploying/index.md#publish-self-contained) would produce an executable.</span></span>

<span data-ttu-id="e9feb-131">在 `dotnet build` 或期間 `dotnet publish` ，會建立可執行檔（稱為**appHost**），以符合您所使用之 SDK 的環境和平臺。</span><span class="sxs-lookup"><span data-stu-id="e9feb-131">During `dotnet build` or `dotnet publish`, an executable (known as the **appHost**) is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="e9feb-132">針對這些可執行檔，您可以預期能夠進行與其他原生可執行檔相同的操作，例如：</span><span class="sxs-lookup"><span data-stu-id="e9feb-132">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="e9feb-133">您可以按兩下可執行檔。</span><span class="sxs-lookup"><span data-stu-id="e9feb-133">You can double-click on the executable.</span></span>
- <span data-ttu-id="e9feb-134">您可以直接從命令提示字元啟動應用程式，例如在 Windows 上為 `myapp.exe`，在 Linux 和 macOS 上為 `./myapp`。</span><span class="sxs-lookup"><span data-stu-id="e9feb-134">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

### <a name="macos-apphost-and-notarization"></a><span data-ttu-id="e9feb-135">macOS appHost 和 notarization</span><span class="sxs-lookup"><span data-stu-id="e9feb-135">macOS appHost and notarization</span></span>

<span data-ttu-id="e9feb-136">*僅限 macOS*</span><span class="sxs-lookup"><span data-stu-id="e9feb-136">*macOS only*</span></span>

<span data-ttu-id="e9feb-137">從適用于 macOS 的公證 .NET Core SDK 3.0 開始，預設會停用產生預設可執行檔（稱為 appHost）的設定。</span><span class="sxs-lookup"><span data-stu-id="e9feb-137">Starting with the notarized .NET Core SDK 3.0 for macOS, the setting to produce a default executable (known as the appHost) is disabled by default.</span></span> <span data-ttu-id="e9feb-138">如需詳細資訊，請參閱[MacOS Catalina Notarization 和對 .Net Core 下載和專案的影響](../install/macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-138">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="e9feb-139">當 appHost 設定啟用時，.NET Core 會在您建立或發行時產生原生符合-O 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="e9feb-139">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="e9feb-140">當您的應用程式是從使用命令的原始程式碼執行 `dotnet run` ，或直接啟動符合-O 可執行檔時，就會在 appHost 的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="e9feb-140">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="e9feb-141">如果沒有 appHost，使用者唯一可以啟動[執行時間相依](../deploying/index.md#publish-runtime-dependent)應用程式的方式是使用 `dotnet <filename.dll>` 命令。</span><span class="sxs-lookup"><span data-stu-id="e9feb-141">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="e9feb-142">當您發佈[獨立](../deploying/index.md#publish-self-contained)應用程式時，一律會建立 appHost。</span><span class="sxs-lookup"><span data-stu-id="e9feb-142">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="e9feb-143">您可以在專案層級設定 appHost，或使用參數來切換特定命令的 appHost `dotnet` `-p:UseAppHost` ：</span><span class="sxs-lookup"><span data-stu-id="e9feb-143">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="e9feb-144">專案檔</span><span class="sxs-lookup"><span data-stu-id="e9feb-144">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="e9feb-145">命令列參數</span><span class="sxs-lookup"><span data-stu-id="e9feb-145">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="e9feb-146">如需設定的詳細資訊 `UseAppHost` ，請參閱[適用于 Microsoft .Net 的 MSBuild 屬性](../project-sdk/msbuild-props.md#useapphost)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-146">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

### <a name="single-file-executables"></a><span data-ttu-id="e9feb-147">單一檔案可執行檔</span><span class="sxs-lookup"><span data-stu-id="e9feb-147">Single-file executables</span></span>

<span data-ttu-id="e9feb-148">`dotnet publish` 命令支援將您的應用程式封裝成平台特定單一檔案可執行檔。</span><span class="sxs-lookup"><span data-stu-id="e9feb-148">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="e9feb-149">可執行檔會自我解壓縮，並包含執行應用程式所需的所有相依性 (包括原生)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-149">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="e9feb-150">第一次執行應用程式時，系統會將應用程式解壓縮到以應用程式名稱和組建識別碼為基礎的目錄。</span><span class="sxs-lookup"><span data-stu-id="e9feb-150">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="e9feb-151">再次執行應用程式時的啟動速度會更快。</span><span class="sxs-lookup"><span data-stu-id="e9feb-151">Startup is faster when the application is run again.</span></span> <span data-ttu-id="e9feb-152">除非使用新版本，否則應用程式不需要再次自我解壓縮。</span><span class="sxs-lookup"><span data-stu-id="e9feb-152">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="e9feb-153">若要發佈單一檔案可執行檔，請在專案中或在命令列上使用 `dotnet publish` 命令來設定 `PublishSingleFile`：</span><span class="sxs-lookup"><span data-stu-id="e9feb-153">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="e9feb-154">-或-</span><span class="sxs-lookup"><span data-stu-id="e9feb-154">-or-</span></span>

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

<span data-ttu-id="e9feb-155">如需單一檔案發佈的詳細資訊，請參閱[單一檔案搭配程式設計文件](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-155">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

### <a name="assembly-linking"></a><span data-ttu-id="e9feb-156">組件連結</span><span class="sxs-lookup"><span data-stu-id="e9feb-156">Assembly linking</span></span>

<span data-ttu-id="e9feb-157">.NET Core 3.0 SDK 隨附能透過分析 IL 並修剪未使用的組件來減少應用程式大小的工具。</span><span class="sxs-lookup"><span data-stu-id="e9feb-157">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="e9feb-158">自封式應用程式包含執行程式碼所需的一切項目，因此不需要在主機電腦上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="e9feb-158">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="e9feb-159">不過，應用程式經常只需要一小部分的架構子集便能運作，而其他未使用的程式庫則可以被移除。</span><span class="sxs-lookup"><span data-stu-id="e9feb-159">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="e9feb-160">.NET Core 現在包含會使用 [IL 連結器](https://github.com/mono/linker) \(英文\) 工具來掃描應用程式 IL 的設定。</span><span class="sxs-lookup"><span data-stu-id="e9feb-160">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="e9feb-161">此工具會偵測所需的程式碼，然後修剪未使用的程式庫。</span><span class="sxs-lookup"><span data-stu-id="e9feb-161">This tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="e9feb-162">此工具可以大幅減少某些應用程式的部署大小。</span><span class="sxs-lookup"><span data-stu-id="e9feb-162">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="e9feb-163">若要啟用此工具，請在專案中新增 `<PublishTrimmed>` 設定，並發佈獨立式應用程式：</span><span class="sxs-lookup"><span data-stu-id="e9feb-163">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="e9feb-164">例如，所包含的基本 "hello world" 新主控台專案在發佈時的大小大約是 70 MB。</span><span class="sxs-lookup"><span data-stu-id="e9feb-164">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="e9feb-165">透過使用 `<PublishTrimmed>`，該大小會被縮減為大約 30 MB。</span><span class="sxs-lookup"><span data-stu-id="e9feb-165">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="e9feb-166">請務必記得，對使用反映或相關動態功能的應用程式或架構 (包括 ASP.NET Core 和 WPF) 進行修剪經常會發生中斷的情況。</span><span class="sxs-lookup"><span data-stu-id="e9feb-166">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="e9feb-167">會發生此中斷的原因是因為連結器不知道此動態行為，因此無法判斷反映所需的架構類型有哪些。</span><span class="sxs-lookup"><span data-stu-id="e9feb-167">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="e9feb-168">可以對 IL 連結器工具加以設定來使其注意到此情況。</span><span class="sxs-lookup"><span data-stu-id="e9feb-168">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="e9feb-169">無論如何，請務必在修剪後測試您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9feb-169">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="e9feb-170">如需 IL 連結器工具的詳細資訊，請參閱[文件](https://aka.ms/dotnet-illink) \(英文\) 或造訪 [mono/linker]( https://github.com/mono/linker) \(英文\) 存放庫。</span><span class="sxs-lookup"><span data-stu-id="e9feb-170">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

### <a name="tiered-compilation"></a><span data-ttu-id="e9feb-171">階層式編譯</span><span class="sxs-lookup"><span data-stu-id="e9feb-171">Tiered compilation</span></span>

<span data-ttu-id="e9feb-172">.NET Core 3.0 預設會開啟[階層式編譯](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md) (TC)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-172">[Tiered compilation](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="e9feb-173">這項功能可讓執行時間更方便地使用即時（JIT）編譯器，以達到更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="e9feb-173">This feature enables the runtime to more adaptively use the just-in-time (JIT) compiler to achieve better performance.</span></span>

<span data-ttu-id="e9feb-174">階層式編譯的主要優點是提供兩種方式來 jitting 方法：以較低品質但更快速的層級，或較高品質但較慢的階層。</span><span class="sxs-lookup"><span data-stu-id="e9feb-174">The main benefit of tiered compilation is to provide two ways of jitting methods: in a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="e9feb-175">品質是指方法的優化程度。</span><span class="sxs-lookup"><span data-stu-id="e9feb-175">The quality refers to how well the method is optimized.</span></span> <span data-ttu-id="e9feb-176">TC 有助於改善應用程式的效能，因為它會經歷各種執行階段，從啟動到穩定的狀態。</span><span class="sxs-lookup"><span data-stu-id="e9feb-176">TC helps to improve the performance of an application as it goes through various stages of execution, from startup through steady state.</span></span> <span data-ttu-id="e9feb-177">停用階層式編譯時，每個方法都會以單一方式編譯，而非啟動效能的穩定狀態效能。</span><span class="sxs-lookup"><span data-stu-id="e9feb-177">When tiered compilation is disabled, every method is compiled in a single way that's biased to steady-state performance over startup performance.</span></span>

<span data-ttu-id="e9feb-178">當啟用 TC 時，下列行為適用于應用程式啟動時的方法編譯：</span><span class="sxs-lookup"><span data-stu-id="e9feb-178">When TC is enabled, the following behavior applies for method compilation when an app starts up:</span></span>

- <span data-ttu-id="e9feb-179">如果方法有預先編譯的程式碼或[ReadyToRun](#readytorun-images)，則會使用預先產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9feb-179">If the method has ahead-of-time-compiled code, or [ReadyToRun](#readytorun-images), the pregenerated code is used.</span></span>
- <span data-ttu-id="e9feb-180">否則，方法會進行 jit 編譯。</span><span class="sxs-lookup"><span data-stu-id="e9feb-180">Otherwise, the method is jitted.</span></span> <span data-ttu-id="e9feb-181">一般而言，這些方法都是實數值型別的泛型。</span><span class="sxs-lookup"><span data-stu-id="e9feb-181">Typically, these methods are generics over value types.</span></span>
  - <span data-ttu-id="e9feb-182">*快速 JIT*會更快速地產生較低品質（或較不優化的）程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9feb-182">*Quick JIT* produces lower-quality (or less optimized) code more quickly.</span></span> <span data-ttu-id="e9feb-183">在 .NET Core 3.0 中，預設會針對不包含迴圈且在啟動時慣用的方法，啟用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="e9feb-183">In .NET Core 3.0, Quick JIT is enabled by default for methods that don't contain loops and is preferred during startup.</span></span>
  - <span data-ttu-id="e9feb-184">完全優化 JIT 會產生較高品質（或更優化的）程式碼，速度更慢。</span><span class="sxs-lookup"><span data-stu-id="e9feb-184">The fully optimizing JIT produces higher-quality (or more optimized) code more slowly.</span></span> <span data-ttu-id="e9feb-185">針對不使用快速 JIT 的方法（例如，如果方法是使用進行屬性化 <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType> ），則會使用完全優化的 jit。</span><span class="sxs-lookup"><span data-stu-id="e9feb-185">For methods where Quick JIT would not be used (for example, if the method is attributed with <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>), the fully optimizing JIT is used.</span></span>

<span data-ttu-id="e9feb-186">對於經常被呼叫的方法，即時編譯器最後會在背景中建立完全優化的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9feb-186">For frequently called methods, the just-in-time compiler eventually creates fully optimized code in the background.</span></span> <span data-ttu-id="e9feb-187">然後，優化的程式碼會取代該方法的預先編譯器代碼。</span><span class="sxs-lookup"><span data-stu-id="e9feb-187">The optimized code then replaces the pre-compiled code for that method.</span></span>

<span data-ttu-id="e9feb-188">快速 JIT 產生的程式碼可能會以較慢的速度執行、配置更多記憶體，或使用更多堆疊空間。</span><span class="sxs-lookup"><span data-stu-id="e9feb-188">Code generated by Quick JIT may run slower, allocate more memory, or use more stack space.</span></span> <span data-ttu-id="e9feb-189">如果有問題，您可以在專案檔中使用此 MSBuild 屬性來停用快速 JIT：</span><span class="sxs-lookup"><span data-stu-id="e9feb-189">If there are issues, you can disabled Quick JIT using this MSBuild property in the project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="e9feb-190">若要完全停用 TC，請在專案檔中使用此 MSBuild 屬性：</span><span class="sxs-lookup"><span data-stu-id="e9feb-190">To disable TC completely, use this MSBuild property in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="e9feb-191">如果您在專案檔中變更這些設定，可能需要執行全新的組建，才會反映新的設定（刪除 `obj` 和 `bin` 目錄並重建）。</span><span class="sxs-lookup"><span data-stu-id="e9feb-191">If you change these settings in the project file, you may need to perform a clean build for the new settings to be reflected (delete the `obj` and `bin` directories and rebuild).</span></span>

<span data-ttu-id="e9feb-192">如需在執行時間設定編譯的詳細資訊，請參閱[編譯的執行時間設定選項](../run-time-config/compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-192">For more information about configuring compilation at run time, see [Run-time configuration options for compilation](../run-time-config/compilation.md).</span></span>

### <a name="readytorun-images"></a><span data-ttu-id="e9feb-193">ReadyToRun 映像</span><span class="sxs-lookup"><span data-stu-id="e9feb-193">ReadyToRun images</span></span>

<span data-ttu-id="e9feb-194">您可以透過將應用程式組件編譯為 ReadyToRun (R2R) 格式，來改善 .NET Core 應用程式的啟動時間。</span><span class="sxs-lookup"><span data-stu-id="e9feb-194">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="e9feb-195">R2R 是一種預先(AOT) 編譯。</span><span class="sxs-lookup"><span data-stu-id="e9feb-195">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="e9feb-196">R2R 二進位檔會透過減少 Just-In-Time (JIT) 編譯器在應用程式載入時所需執行的工作量，來改善啟動效能。</span><span class="sxs-lookup"><span data-stu-id="e9feb-196">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="e9feb-197">二進位檔包含的機器碼，與 JIT 所會產生的內容類似。</span><span class="sxs-lookup"><span data-stu-id="e9feb-197">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="e9feb-198">但是，R2R 二進位檔大小較大，因為它們會同時包含中繼語言 (IL) 程式碼 (在某些案例下仍需要使用)，以及相同程式碼的原生版本。</span><span class="sxs-lookup"><span data-stu-id="e9feb-198">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="e9feb-199">R2R 只有在您發佈以特定執行階段環境 (RID) (例如 Linux x64 或 Windows x64) 為目標的獨立式應用程式時才可供使用。</span><span class="sxs-lookup"><span data-stu-id="e9feb-199">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="e9feb-200">若要將您的專案編譯為 ReadyToRun，請執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="e9feb-200">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="e9feb-201">將 `<PublishReadyToRun>` 設定新增至您的專案：</span><span class="sxs-lookup"><span data-stu-id="e9feb-201">Add the `<PublishReadyToRun>` setting to your project:</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="e9feb-202">發佈自封式應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9feb-202">Publish a self-contained app.</span></span> <span data-ttu-id="e9feb-203">例如，此命令會針對 64 位元版本的 Windows 建立自封式應用程式：</span><span class="sxs-lookup"><span data-stu-id="e9feb-203">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="e9feb-204">跨平台/架構限制</span><span class="sxs-lookup"><span data-stu-id="e9feb-204">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="e9feb-205">ReadyToRun 編譯器目前不支援跨目標。</span><span class="sxs-lookup"><span data-stu-id="e9feb-205">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="e9feb-206">您必須在指定的目標上進行編譯。</span><span class="sxs-lookup"><span data-stu-id="e9feb-206">You must compile on a given target.</span></span> <span data-ttu-id="e9feb-207">例如，如果您想要適用於 Windows x64 的 R2R 映像，便需要在該環境上執行發佈命令。</span><span class="sxs-lookup"><span data-stu-id="e9feb-207">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="e9feb-208">鎖定多重目標的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="e9feb-208">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="e9feb-209">Windows x64 可以用來編譯 Windows ARM32、ARM64 及 x86 映像。</span><span class="sxs-lookup"><span data-stu-id="e9feb-209">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="e9feb-210">Windows x86 可以用來編譯 Windows ARM32 映像。</span><span class="sxs-lookup"><span data-stu-id="e9feb-210">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="e9feb-211">Linux x64 可以用來編譯 Linux ARM32 和 ARM64 映像。</span><span class="sxs-lookup"><span data-stu-id="e9feb-211">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="runtimesdk"></a><span data-ttu-id="e9feb-212">執行時間/SDK</span><span class="sxs-lookup"><span data-stu-id="e9feb-212">Runtime/SDK</span></span>

### <a name="major-version-runtime-roll-forward"></a><span data-ttu-id="e9feb-213">主要版本執行時間向前復原</span><span class="sxs-lookup"><span data-stu-id="e9feb-213">Major-version runtime roll forward</span></span>

<span data-ttu-id="e9feb-214">.NET Core 3.0 引進選擇性功能，可讓您的應用程式向前復原到 .NET Core 最新主要版本。</span><span class="sxs-lookup"><span data-stu-id="e9feb-214">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="e9feb-215">此外，也已新增設定來控制如何將向前復原套用至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9feb-215">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="e9feb-216">這可透過下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="e9feb-216">This can be configured in the following ways:</span></span>

- <span data-ttu-id="e9feb-217">專案檔屬性：`RollForward`</span><span class="sxs-lookup"><span data-stu-id="e9feb-217">Project file property: `RollForward`</span></span>
- <span data-ttu-id="e9feb-218">執行時間配置檔案屬性：`rollForward`</span><span class="sxs-lookup"><span data-stu-id="e9feb-218">Run-time configuration file property: `rollForward`</span></span>
- <span data-ttu-id="e9feb-219">環境變數：`DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="e9feb-219">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="e9feb-220">命令列引數：`--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="e9feb-220">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="e9feb-221">必須指定下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="e9feb-221">One of the following values must be specified.</span></span> <span data-ttu-id="e9feb-222">若省略設定，**Minor** 會是預設值。</span><span class="sxs-lookup"><span data-stu-id="e9feb-222">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="e9feb-223">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="e9feb-223">**LatestPatch**</span></span>\
<span data-ttu-id="e9feb-224">向前復原到最高的修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="e9feb-224">Roll forward to the highest patch version.</span></span> <span data-ttu-id="e9feb-225">這會停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="e9feb-225">This disables minor version roll forward.</span></span>
- <span data-ttu-id="e9feb-226">**刻度**</span><span class="sxs-lookup"><span data-stu-id="e9feb-226">**Minor**</span></span>\
<span data-ttu-id="e9feb-227">如果缺少要求的次要版本，則會向前復原到最低次要版本中次高的版本。</span><span class="sxs-lookup"><span data-stu-id="e9feb-227">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="e9feb-228">如果要求的次要版本存在，則會使用 **LatestPatch** 原則。</span><span class="sxs-lookup"><span data-stu-id="e9feb-228">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="e9feb-229">**巨大**</span><span class="sxs-lookup"><span data-stu-id="e9feb-229">**Major**</span></span>\
<span data-ttu-id="e9feb-230">如果缺少要求的主要版本，則會向前復原到最低主要版本中次高的版本，以及最低的次要版本。</span><span class="sxs-lookup"><span data-stu-id="e9feb-230">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="e9feb-231">如果要求的主要版本存在，則會使用 **Minor** 原則。</span><span class="sxs-lookup"><span data-stu-id="e9feb-231">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="e9feb-232">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="e9feb-232">**LatestMinor**</span></span>\
<span data-ttu-id="e9feb-233">向前復原到最高的次要版本，即使要求的次要版本存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="e9feb-233">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="e9feb-234">適用於裝載案例的元件。</span><span class="sxs-lookup"><span data-stu-id="e9feb-234">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="e9feb-235">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="e9feb-235">**LatestMajor**</span></span>\
<span data-ttu-id="e9feb-236">向前復原到最高主要版本和最高次要版本，即使要求的主要版本存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="e9feb-236">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="e9feb-237">適用於裝載案例的元件。</span><span class="sxs-lookup"><span data-stu-id="e9feb-237">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="e9feb-238">**啟用**</span><span class="sxs-lookup"><span data-stu-id="e9feb-238">**Disable**</span></span>\
<span data-ttu-id="e9feb-239">不會向前復原。</span><span class="sxs-lookup"><span data-stu-id="e9feb-239">Don't roll forward.</span></span> <span data-ttu-id="e9feb-240">只會繫結至指定的版本。</span><span class="sxs-lookup"><span data-stu-id="e9feb-240">Only bind to specified version.</span></span> <span data-ttu-id="e9feb-241">此原則不建議一般用途，因為它會停用向前復原到最新修補程式的功能。</span><span class="sxs-lookup"><span data-stu-id="e9feb-241">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="e9feb-242">只有測試時才建議使用這個值。</span><span class="sxs-lookup"><span data-stu-id="e9feb-242">This value is only recommended for testing.</span></span>

<span data-ttu-id="e9feb-243">除了 **Disable** 設定，所有設定都會使用最高可用的修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="e9feb-243">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="e9feb-244">根據預設，如果要求的版本（如應用程式中所指定 `.runtimeconfig.json` ）是發行版本，則只會將發行版本視為向前復原。</span><span class="sxs-lookup"><span data-stu-id="e9feb-244">By default, if the requested version (as specified in `.runtimeconfig.json` for the application) is a release version, only release versions are considered for roll forward.</span></span> <span data-ttu-id="e9feb-245">任何發行前版本都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="e9feb-245">Any pre-release versions are ignored.</span></span> <span data-ttu-id="e9feb-246">如果沒有相符的發行版本，則會將發行前版本納入考慮。</span><span class="sxs-lookup"><span data-stu-id="e9feb-246">If there is no matching release version, then pre-release versions are taken into account.</span></span> <span data-ttu-id="e9feb-247">設定可以變更此行為 `DOTNET_ROLL_FORWARD_TO_PRERELEASE=1` ，在此情況下，一律會考慮所有版本。</span><span class="sxs-lookup"><span data-stu-id="e9feb-247">This behavior can be changed by setting `DOTNET_ROLL_FORWARD_TO_PRERELEASE=1`, in which case all versions are always considered.</span></span>

### <a name="build-copies-dependencies"></a><span data-ttu-id="e9feb-248">組建複本相依性</span><span class="sxs-lookup"><span data-stu-id="e9feb-248">Build copies dependencies</span></span>

<span data-ttu-id="e9feb-249">`dotnet build` 命令現在會從 NuGet 快取將您應用程式的 NuGet 相依性複製到組建輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="e9feb-249">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="e9feb-250">先前，只有在進行 `dotnet publish` 的過程中，才會複製相依性。</span><span class="sxs-lookup"><span data-stu-id="e9feb-250">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="e9feb-251">有些作業 (例如連結和 Razor 頁面發佈) 仍然需要發佈。</span><span class="sxs-lookup"><span data-stu-id="e9feb-251">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

### <a name="local-tools"></a><span data-ttu-id="e9feb-252">本機工具</span><span class="sxs-lookup"><span data-stu-id="e9feb-252">Local tools</span></span>

<span data-ttu-id="e9feb-253">.NET Core 3.0 引進本機工具。</span><span class="sxs-lookup"><span data-stu-id="e9feb-253">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="e9feb-254">本機工具類似于[全域工具](../tools/global-tools.md)，但與磁片上的特定位置相關聯。</span><span class="sxs-lookup"><span data-stu-id="e9feb-254">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="e9feb-255">本機工具並非全域可用，而是以 NuGet 套件形式散發。</span><span class="sxs-lookup"><span data-stu-id="e9feb-255">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="e9feb-256">如果您在 .NET Core 3.0 Preview 1 中嘗試本機工具 (例如執行 `dotnet tool restore` 或 `dotnet tool install`)，請刪除本機工具快取資料夾。</span><span class="sxs-lookup"><span data-stu-id="e9feb-256">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="e9feb-257">否則，本機工具將無法在任何較新版本中運作。</span><span class="sxs-lookup"><span data-stu-id="e9feb-257">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="e9feb-258">此資料夾位於：</span><span class="sxs-lookup"><span data-stu-id="e9feb-258">This folder is located at:</span></span>
>
> <span data-ttu-id="e9feb-259">在 macOS 上，Linux：`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="e9feb-259">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="e9feb-260">在 Windows 上：`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="e9feb-260">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="e9feb-261">本機工具會倚賴您目前目錄中名為 `dotnet-tools.json` 的資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="e9feb-261">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="e9feb-262">此資訊清單檔定義可在該資料夾和以下資料夾提供的工具。</span><span class="sxs-lookup"><span data-stu-id="e9feb-262">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="e9feb-263">您可以隨程式碼散發資訊清單檔，確保使用您程式碼的任何人都能進行還原並使用相同工具。</span><span class="sxs-lookup"><span data-stu-id="e9feb-263">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="e9feb-264">不論是全域工具還是區域工具，都需要一個相容的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="e9feb-264">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="e9feb-265">NuGet.org 上目前許多工具都以 .NET Core 執行階段 2.1 為目標。</span><span class="sxs-lookup"><span data-stu-id="e9feb-265">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="e9feb-266">若要在全域或本機安裝這些工具，您仍然需要安裝 [.NET Core 2.1 執行階段](https://dotnet.microsoft.com/download/dotnet-core/2.1)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-266">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

### <a name="new-globaljson-options"></a><span data-ttu-id="e9feb-267">新的 global. json 選項</span><span class="sxs-lookup"><span data-stu-id="e9feb-267">New global.json options</span></span>

<span data-ttu-id="e9feb-268">當您嘗試定義所使用的 .NET Core SDK 版本時， *global.asax*檔案有新的選項可提供更大的彈性。</span><span class="sxs-lookup"><span data-stu-id="e9feb-268">The *global.json* file has new options that provide more flexibility when you're trying to define which version of the .NET Core SDK is used.</span></span> <span data-ttu-id="e9feb-269">新的選項包括：</span><span class="sxs-lookup"><span data-stu-id="e9feb-269">The new options are:</span></span>

- <span data-ttu-id="e9feb-270">`allowPrerelease`：指出 SDK 解析程式在選取要使用的 SDK 版本時，是否應考慮發行前版本。</span><span class="sxs-lookup"><span data-stu-id="e9feb-270">`allowPrerelease`: Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>
- <span data-ttu-id="e9feb-271">`rollForward`：表示選取 SDK 版本時要使用的向前復原原則，可以在特定 SDK 版本遺失時做為回溯，或做為使用較高版本的指示詞。</span><span class="sxs-lookup"><span data-stu-id="e9feb-271">`rollForward`: Indicates the roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span>

<span data-ttu-id="e9feb-272">如需有關變更的詳細資訊，包括預設值、支援的值和新的比對規則，請參閱[global.asax 總覽](../tools/global-json.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-272">For more information about the changes including default values, supported values, and new matching rules, see [global.json overview](../tools/global-json.md).</span></span>

### <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="e9feb-273">較小的記憶體回收堆積大小</span><span class="sxs-lookup"><span data-stu-id="e9feb-273">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="e9feb-274">已減少記憶體回收行程的預設堆積大小，而導致 .NET Core 使用較少的記憶體。</span><span class="sxs-lookup"><span data-stu-id="e9feb-274">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="e9feb-275">這項變更較符合使用新式處理器快取大小的層代 0 配置預算。</span><span class="sxs-lookup"><span data-stu-id="e9feb-275">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

### <a name="garbage-collection-large-page-support"></a><span data-ttu-id="e9feb-276">記憶體回收大型頁面支援</span><span class="sxs-lookup"><span data-stu-id="e9feb-276">Garbage Collection Large Page support</span></span>

<span data-ttu-id="e9feb-277">大型頁面 (Large Page，在 Linux 上又稱為 Huge Page) 是一項功能，其中作業系統能夠建立大於原生頁面大小 (通常為 4K) 的記憶體區域，以提升要求這些大型頁面的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="e9feb-277">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="e9feb-278">記憶體回收行程現在可以設定 **GCLargePages** 設定作為選擇性功能，來選擇在 Windows 上配置大型頁面。</span><span class="sxs-lookup"><span data-stu-id="e9feb-278">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="windows-desktop--com"></a><span data-ttu-id="e9feb-279">Windows 桌面 & COM</span><span class="sxs-lookup"><span data-stu-id="e9feb-279">Windows Desktop & COM</span></span>

### <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="e9feb-280">.NET Core SDK Windows Installer</span><span class="sxs-lookup"><span data-stu-id="e9feb-280">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="e9feb-281">Windows 的 MSI 安裝程式從 .NET Core 3.0 開始即已變更。</span><span class="sxs-lookup"><span data-stu-id="e9feb-281">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="e9feb-282">SDK 安裝程式現在會就地升級 SDK 功能帶版本。</span><span class="sxs-lookup"><span data-stu-id="e9feb-282">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="e9feb-283">功能帶是在版本號碼「修補程式」\*\* 部分以「一百」\*\* 為單位的群組中定義。</span><span class="sxs-lookup"><span data-stu-id="e9feb-283">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="e9feb-284">例如，**3.0._101_** 和 **3.0._201_** 便是位於兩個不同功能帶中的版本，而 **3.0._101_** 和 **3.0._199_** 則位於相同的功能帶。</span><span class="sxs-lookup"><span data-stu-id="e9feb-284">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="e9feb-285">此外，安裝 .NET Core SDK **3.0._101_** 時，.NET Core SDK **3.0._100_** 便會從電腦移除 (若存在的話)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-285">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="e9feb-286">在相同電腦上安裝 .NET Core SDK **3.0._200_** 時，不會移除 .NET Core SDK **3.0._101_**。</span><span class="sxs-lookup"><span data-stu-id="e9feb-286">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="e9feb-287">如需版本設定的詳細資訊，請參閱 [.NET Core 版本設定概觀](../versions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-287">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

### <a name="windows-desktop"></a><span data-ttu-id="e9feb-288">Windows 桌面</span><span class="sxs-lookup"><span data-stu-id="e9feb-288">Windows desktop</span></span>

<span data-ttu-id="e9feb-289">.NET Core 3.0 支援使用 Windows Presentation Foundation (WPF) 和 Windows Forms 的 Windows 傳統型應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9feb-289">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="e9feb-290">這些架構也支援透過 [XAML 島](/windows/uwp/xaml-platform/xaml-host-controls)使用來自 Windows UI XAML 程式庫 (WinUI) 的新式控制項和 Fluent 樣式。</span><span class="sxs-lookup"><span data-stu-id="e9feb-290">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="e9feb-291">「Windows 傳統型」元件是 Windows .NET Core 3.0 SDK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="e9feb-291">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="e9feb-292">您可以使用下列 `dotnet` 命令來建立新的 WPF 或 Windows Forms 應用程式：</span><span class="sxs-lookup"><span data-stu-id="e9feb-292">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```dotnetcli
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="e9feb-293">Visual Studio 2019 會新增 [新增專案]\*\*\*\* 範本，供 .NET Core 3.0 Windows Forms 和 WPF 使用。</span><span class="sxs-lookup"><span data-stu-id="e9feb-293">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="e9feb-294">如需如何移植現有 .NET Framework 應用程式的詳細資訊，請參閱[移植 WPF 專案](../../desktop-wpf/migration/convert-project-from-net-framework.md)和[移植 Windows Forms 專案](../porting/winforms.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-294">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../../desktop-wpf/migration/convert-project-from-net-framework.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

#### <a name="winforms-high-dpi"></a><span data-ttu-id="e9feb-295">WinForms 高 DPI</span><span class="sxs-lookup"><span data-stu-id="e9feb-295">WinForms high DPI</span></span>

<span data-ttu-id="e9feb-296">.NET Core Windows Forms 應用程式可以使用 <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType> 設定高 DPI 模式。</span><span class="sxs-lookup"><span data-stu-id="e9feb-296">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e9feb-297">除非已透過其他方法 (例如在 `Application.Run` 前面加上 `App.Manifest` 或 P/Invoke) 進行設定，否則 `SetHighDpiMode` 方法可以設定對應的高 DPI 模式。</span><span class="sxs-lookup"><span data-stu-id="e9feb-297">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="e9feb-298">可能的 `highDpiMode` 值 (如 <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> 列舉所示) 為：</span><span class="sxs-lookup"><span data-stu-id="e9feb-298">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="e9feb-299">如需高 DPI 模式的詳細資訊，請參閱[Windows 上的高 Dpi 桌面應用程式開發](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-299">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="create-com-components"></a><span data-ttu-id="e9feb-300">建立 COM 元件</span><span class="sxs-lookup"><span data-stu-id="e9feb-300">Create COM components</span></span>

<span data-ttu-id="e9feb-301">您現在可以在 Windows 上建立 COM 可呼叫受控元件。</span><span class="sxs-lookup"><span data-stu-id="e9feb-301">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="e9feb-302">此功能對於搭配 COM 增益集模型使用 .NET Core 很重要，也提供 .NET Framework 同位。</span><span class="sxs-lookup"><span data-stu-id="e9feb-302">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="e9feb-303">不同於 .NET Framework (其中使用 *mscoree.dll* 作為 COM 伺服器)，.NET Core 會在您建置 COM 元件時，將原生啟動器 DLL 新增至 *bin* 目錄。</span><span class="sxs-lookup"><span data-stu-id="e9feb-303">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="e9feb-304">如需如何建立及取用 COM 元件的範例，請參閱 [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) (COM 示範)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-304">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="e9feb-305">Windows 原生 Interop</span><span class="sxs-lookup"><span data-stu-id="e9feb-305">Windows Native Interop</span></span>

<span data-ttu-id="e9feb-306">Windows 提供豐富的原生 API，其採用的形式為一般 C API、COM 和 WinRT。</span><span class="sxs-lookup"><span data-stu-id="e9feb-306">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="e9feb-307">除了 .NET Core 3.0 支援 **P/Invoke** 之外，.NET Core 3.0 還新增 **CoCreate COM API** 和 **Activate WinRT API** 的功能。</span><span class="sxs-lookup"><span data-stu-id="e9feb-307">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="e9feb-308">如需程式碼範例，請參閱 [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo) (Excel 示範)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-308">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

### <a name="msix-deployment"></a><span data-ttu-id="e9feb-309">MSIX 部署</span><span class="sxs-lookup"><span data-stu-id="e9feb-309">MSIX Deployment</span></span>

<span data-ttu-id="e9feb-310">[MSIX](https://docs.microsoft.com/windows/msix/) 是新的 Windows 應用程式套件格式。</span><span class="sxs-lookup"><span data-stu-id="e9feb-310">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="e9feb-311">它可以用來將 .NET Core 3.0 桌面應用程式部署至 Windows 10。</span><span class="sxs-lookup"><span data-stu-id="e9feb-311">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="e9feb-312">Visual Studio 2019 中提供的 [Windows 應用程式套件專案](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net) \(機器翻譯\) 可讓您利用[獨立式](../deploying/index.md#publish-self-contained) .NET Core 應用程式建立 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="e9feb-312">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#publish-self-contained) .NET Core applications.</span></span>

<span data-ttu-id="e9feb-313">.NET Core 專案檔必須指定在 `<RuntimeIdentifiers>` 屬性中支援的執行階段：</span><span class="sxs-lookup"><span data-stu-id="e9feb-313">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a><span data-ttu-id="e9feb-314">Linux 改良功能</span><span class="sxs-lookup"><span data-stu-id="e9feb-314">Linux improvements</span></span>

### <a name="serialport-for-linux"></a><span data-ttu-id="e9feb-315">適用於 Linux 的 SerialPort</span><span class="sxs-lookup"><span data-stu-id="e9feb-315">SerialPort for Linux</span></span>

<span data-ttu-id="e9feb-316">.NET Core 3.0 提供 Linux 上 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> 的基本支援。</span><span class="sxs-lookup"><span data-stu-id="e9feb-316">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="e9feb-317">先前，.NET Core 僅支援在 Windows 上使用 `SerialPort`。</span><span class="sxs-lookup"><span data-stu-id="e9feb-317">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="e9feb-318">如需 Linux 上序列埠有限支援的詳細資訊，請參閱 [GitHub 問題 #33146](https://github.com/dotnet/corefx/issues/33146)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-318">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

### <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="e9feb-319">Docker 和 cgroup 記憶體限制</span><span class="sxs-lookup"><span data-stu-id="e9feb-319">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="e9feb-320">在 Linux 上使用 Docker 執行 .NET Core 3.0，會有更好的 cgroup 記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="e9feb-320">Running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="e9feb-321">使用記憶體限制 (例如使用 `docker run -m`) 執行 Docker 容器會變更 .NET Core 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="e9feb-321">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="e9feb-322">預設記憶體回收行程 (GC) 堆積大小：上限為 20 MB，或容器上 75% 的記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="e9feb-322">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="e9feb-323">可將明確大小設定為 cgroup 限制的絕對數目或百分比。</span><span class="sxs-lookup"><span data-stu-id="e9feb-323">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="e9feb-324">每個 GC 堆積的保留區段大小下限為 16 MB。</span><span class="sxs-lookup"><span data-stu-id="e9feb-324">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="e9feb-325">此大小可減少電腦上所建立的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="e9feb-325">This size reduces the number of heaps that are created on machines.</span></span>

### <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="e9feb-326">Raspberry Pi 的 GPIO 支援</span><span class="sxs-lookup"><span data-stu-id="e9feb-326">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="e9feb-327">兩個套件已發佈至您可以用於 GPIO 程式設計的 NuGet：</span><span class="sxs-lookup"><span data-stu-id="e9feb-327">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="e9feb-328">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="e9feb-328">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="e9feb-329">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="e9feb-329">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="e9feb-330">GPIO 套件包含 *GPIO*、*SPI*、*I2C* 和 *PWM* 裝置的 API。</span><span class="sxs-lookup"><span data-stu-id="e9feb-330">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="e9feb-331">IoT 繫結套件包含裝置繫結。</span><span class="sxs-lookup"><span data-stu-id="e9feb-331">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="e9feb-332">如需詳細資訊，請參閱[裝置 GitHub 存放庫](https://github.com/dotnet/iot/blob/master/src/devices/)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-332">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

### <a name="arm64-linux-support"></a><span data-ttu-id="e9feb-333">ARM64 Linux 支援</span><span class="sxs-lookup"><span data-stu-id="e9feb-333">ARM64 Linux support</span></span>

<span data-ttu-id="e9feb-334">.NET Core 3.0 新增 ARM64 for Linux 的支援。</span><span class="sxs-lookup"><span data-stu-id="e9feb-334">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="e9feb-335">ARM64 的主要使用案例目前是搭配 IoT 案例。</span><span class="sxs-lookup"><span data-stu-id="e9feb-335">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="e9feb-336">如需詳細資訊，請參閱 [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) (.NET Core ARM64 狀態)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-336">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="e9feb-337">[ARM64 上適用於 .NET Core 的 Docker 映像](https://hub.docker.com/r/microsoft/dotnet/)可供 Alpine、Debian 和 Ubuntu 使用。</span><span class="sxs-lookup"><span data-stu-id="e9feb-337">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="e9feb-338">目前尚未提供 **ARM64** Windows 支援。</span><span class="sxs-lookup"><span data-stu-id="e9feb-338">**ARM64** Windows support isn't yet available.</span></span>

## <a name="security"></a><span data-ttu-id="e9feb-339">安全性</span><span class="sxs-lookup"><span data-stu-id="e9feb-339">Security</span></span>

### <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="e9feb-340">Linux 上的 TLS 1.3 和 OpenSSL 1.1.1</span><span class="sxs-lookup"><span data-stu-id="e9feb-340">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="e9feb-341">.NET Core 現在會利用 [OpenSSL 1.1.1 中的 TLS 1.3 支援](https://www.openssl.org/blog/blog/2018/09/11/release111/) (當在指定的環境中有提供時)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-341">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="e9feb-342">透過 TLS 1.3：</span><span class="sxs-lookup"><span data-stu-id="e9feb-342">With TLS 1.3:</span></span>

- <span data-ttu-id="e9feb-343">因為用戶端與伺服器之間所需的來回行程次數減少，所以改善了連線時間。</span><span class="sxs-lookup"><span data-stu-id="e9feb-343">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="e9feb-344">因為移除各種已淘汰和不安全的密碼編譯演算法，所以提升了安全性。</span><span class="sxs-lookup"><span data-stu-id="e9feb-344">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="e9feb-345">.NET Core 3.0 在 Linux 系統上使用 **OpenSSL 1.1.1**、**OpenSSL 1.1.0** 或 **OpenSSL 1.0.2** (若可供使用)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-345">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="e9feb-346">當 **OpenSSL 1.1.1** 可供使用時，<xref:System.Net.Security.SslStream?displayProperty=nameWithType> 和 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 類型就會使用 **TLS 1.3** (假設用戶端和伺服器都支援 **TLS 1.3**)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-346">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9feb-347">Windows 和 macOS 尚未支援 **TLS 1.3**。</span><span class="sxs-lookup"><span data-stu-id="e9feb-347">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="e9feb-348">.NET Core 3.0 將在有支援可用時，在這些作業系統上支援 **TLS 1.3**。</span><span class="sxs-lookup"><span data-stu-id="e9feb-348">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="e9feb-349">下列 C# 8.0 範例示範連線至 <https://www.cloudflare.com> 之 Ubuntu 18.10 上的 .NET Core 3.0：</span><span class="sxs-lookup"><span data-stu-id="e9feb-349">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a><span data-ttu-id="e9feb-350">密碼編譯加密方式</span><span class="sxs-lookup"><span data-stu-id="e9feb-350">Cryptography ciphers</span></span>

<span data-ttu-id="e9feb-351">.NET 3.0 新增對 **AES-GCM** 和 **AES-CCM** 加密方式的支援，分別透過 <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> 和 <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> 來實作。</span><span class="sxs-lookup"><span data-stu-id="e9feb-351">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="e9feb-352">這些演算法都是[搭配關聯資料的驗證加密 (AEAD) 演算法](https://en.wikipedia.org/wiki/Authenticated_encryption)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-352">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="e9feb-353">下列程式碼示範如何使用 `AesGcm` 加密方式將隨機資料加密和解密。</span><span class="sxs-lookup"><span data-stu-id="e9feb-353">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a><span data-ttu-id="e9feb-354">密碼編譯金鑰匯入/匯出</span><span class="sxs-lookup"><span data-stu-id="e9feb-354">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="e9feb-355">.NET Core 3.0 支援從標準格式匯入及匯出非對稱式公開金鑰與私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="e9feb-355">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="e9feb-356">您無須使用 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="e9feb-356">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="e9feb-357">所有金鑰類型 (例如 *RSA*、*DSA*、*ECDsa* 和 *ECDiffieHellman*) 都支援下列格式：</span><span class="sxs-lookup"><span data-stu-id="e9feb-357">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="e9feb-358">**公開金鑰**</span><span class="sxs-lookup"><span data-stu-id="e9feb-358">**Public Key**</span></span>
  - <span data-ttu-id="e9feb-359">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="e9feb-359">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="e9feb-360">**私密金鑰**</span><span class="sxs-lookup"><span data-stu-id="e9feb-360">**Private key**</span></span>
  - <span data-ttu-id="e9feb-361">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="e9feb-361">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="e9feb-362">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="e9feb-362">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="e9feb-363">RSA 金鑰也支援：</span><span class="sxs-lookup"><span data-stu-id="e9feb-363">RSA keys also support:</span></span>

- <span data-ttu-id="e9feb-364">**公開金鑰**</span><span class="sxs-lookup"><span data-stu-id="e9feb-364">**Public Key**</span></span>
  - <span data-ttu-id="e9feb-365">PKCS#1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="e9feb-365">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="e9feb-366">**私密金鑰**</span><span class="sxs-lookup"><span data-stu-id="e9feb-366">**Private key**</span></span>
  - <span data-ttu-id="e9feb-367">PKCS#1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="e9feb-367">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="e9feb-368">匯出方法會產生 DER 編碼的二進位資料，而匯入方法也是如此。</span><span class="sxs-lookup"><span data-stu-id="e9feb-368">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="e9feb-369">如果金鑰是以適合文字的 PEM 格式儲存的，呼叫端在呼叫匯入方法之前，就必須先對內容進行 Base64 解碼。</span><span class="sxs-lookup"><span data-stu-id="e9feb-369">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="e9feb-370">**PKCS#8** 檔案可以使用 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> 來檢查，而 **PFX/PKCS#12** 檔案可以使用 <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType> 來檢查。</span><span class="sxs-lookup"><span data-stu-id="e9feb-370">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e9feb-371">**PFX/PKCS#12** 檔案可以使用 <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType> 來操作。</span><span class="sxs-lookup"><span data-stu-id="e9feb-371">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="net-core-30-api-changes"></a><span data-ttu-id="e9feb-372">.NET Core 3.0 API 變更</span><span class="sxs-lookup"><span data-stu-id="e9feb-372">.NET Core 3.0 API changes</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="e9feb-373">範圍和索引</span><span class="sxs-lookup"><span data-stu-id="e9feb-373">Ranges and indices</span></span>

<span data-ttu-id="e9feb-374">新的 <xref:System.Index?displayProperty=nameWithType> 類型可用於編製索引。</span><span class="sxs-lookup"><span data-stu-id="e9feb-374">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="e9feb-375">您可以從會從開頭算起的 `int` 或使用會從結尾算起的前置詞 `^` 運算子 (C#)，來建立一個索引：</span><span class="sxs-lookup"><span data-stu-id="e9feb-375">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="e9feb-376">此外，還有 <xref:System.Range?displayProperty=nameWithType> 類型，此類型由兩個 `Index` 值所組成 (一個代表開頭，一個代表結尾)，並可用 `x..y` 範圍運算式 (C#) 來撰寫。</span><span class="sxs-lookup"><span data-stu-id="e9feb-376">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="e9feb-377">您可以接著使用 `Range` 來編製索引以產生配量：</span><span class="sxs-lookup"><span data-stu-id="e9feb-377">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="e9feb-378">如需詳細資訊，請參閱[範圍和索引教學課程](../../csharp/tutorials/ranges-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-378">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="e9feb-379">非同步資料流</span><span class="sxs-lookup"><span data-stu-id="e9feb-379">Async streams</span></span>

<span data-ttu-id="e9feb-380"><xref:System.Collections.Generic.IAsyncEnumerable%601> 類型是 <xref:System.Collections.Generic.IEnumerable%601> 的新非同步版本。</span><span class="sxs-lookup"><span data-stu-id="e9feb-380">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="e9feb-381">此語言可讓您透過 `IAsyncEnumerable<T>` 執行 `await foreach` 以取用其元素，然後對它們使用 `yield return` 以產生元素。</span><span class="sxs-lookup"><span data-stu-id="e9feb-381">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="e9feb-382">下列範例同時示範如何產生和取用非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="e9feb-382">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="e9feb-383">`foreach` 是非同步陳述式，其本身會使用 `yield return` 來為呼叫端產生非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="e9feb-383">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="e9feb-384">此模式 (使用 `yield return`) 是針對產生非同步資料流建議採用的模型。</span><span class="sxs-lookup"><span data-stu-id="e9feb-384">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="e9feb-385">除了能夠執行 `await foreach` 之外，您也可以建立非同步迭代器，例如建立一個會傳回 `IAsyncEnumerable/IAsyncEnumerator` 以供您在其中執行 `await` 和 `yield` 的迭代器。</span><span class="sxs-lookup"><span data-stu-id="e9feb-385">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="e9feb-386">針對需要處置的物件，您可以使用各種 BCL 類型 (例如 `Stream` 和 `Timer`) 所實作的 `IAsyncDisposable`。</span><span class="sxs-lookup"><span data-stu-id="e9feb-386">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="e9feb-387">如需詳細資訊，請參閱[非同步資料流教學課程](../../csharp/tutorials/generate-consume-asynchronous-stream.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-387">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

### <a name="ieee-floating-point"></a><span data-ttu-id="e9feb-388">IEEE 浮點</span><span class="sxs-lookup"><span data-stu-id="e9feb-388">IEEE Floating-point</span></span>

<span data-ttu-id="e9feb-389">正在更新浮點 API，以遵守 [IEEE 754-2008 修訂](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-389">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="e9feb-390">這些變更的目標是要公開所有**必要**的作業，並確保其行為上與 IEEE 規格相容。如需浮點改良功能的詳細資訊，請參閱[.Net Core 3.0 中的浮點剖析和格式改進](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)文章。</span><span class="sxs-lookup"><span data-stu-id="e9feb-390">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="e9feb-391">剖析與格式化修正包括：</span><span class="sxs-lookup"><span data-stu-id="e9feb-391">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="e9feb-392">正確地剖析並捨入任意長度的輸入。</span><span class="sxs-lookup"><span data-stu-id="e9feb-392">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="e9feb-393">正確地剖析並格式化負零。</span><span class="sxs-lookup"><span data-stu-id="e9feb-393">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="e9feb-394">正確地剖析 `Infinity` 和 `NaN`，方法為執行不區分大小寫的檢查，並允許適當時在前面選擇性加上 `+`。</span><span class="sxs-lookup"><span data-stu-id="e9feb-394">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="e9feb-395">新的 <xref:System.Math?displayProperty=nameWithType> API 包括：</span><span class="sxs-lookup"><span data-stu-id="e9feb-395">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="e9feb-396"><xref:System.Math.BitIncrement(System.Double)> 和 <xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="e9feb-396"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="e9feb-397">對應至 `nextUp` 和 `nextDown` IEEE 作業。</span><span class="sxs-lookup"><span data-stu-id="e9feb-397">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="e9feb-398">它們會傳回最小浮點數，比較大於或小於輸入 (分別)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-398">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="e9feb-399">例如，`Math.BitIncrement(0.0)` 會傳回 `double.Epsilon`。</span><span class="sxs-lookup"><span data-stu-id="e9feb-399">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="e9feb-400"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> 和 <xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="e9feb-400"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="e9feb-401">對應至 `maxNumMag` 和 `minNumMag`IEEE 作業，它們傳回的值大於或小於兩個輸入的範圍 (分別)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-401">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="e9feb-402">例如，`Math.MaxMagnitude(2.0, -3.0)` 會傳回 `-3.0`。</span><span class="sxs-lookup"><span data-stu-id="e9feb-402">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="e9feb-403">對應至傳回整數值的 `logB` IEEE 作業，它會傳回輸入參數的對數，以整數 2 為底數。</span><span class="sxs-lookup"><span data-stu-id="e9feb-403">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="e9feb-404">此方法實際上與 `floor(log2(x))` 相同，但完成時發生最少捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9feb-404">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="e9feb-405">對應至採用整數值的 `scaleB` IEEE 作業，它會有效傳回 `x * pow(2, n)`，但完成時發生最少捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9feb-405">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="e9feb-406">對應至 `log2` IEEE 作業，它會傳回 2 為底數的對數。</span><span class="sxs-lookup"><span data-stu-id="e9feb-406">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="e9feb-407">它會將捨入錯誤減至最少。</span><span class="sxs-lookup"><span data-stu-id="e9feb-407">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="e9feb-408">對應至 `fma` IEEE 作業，它會執行融合的乘積和。</span><span class="sxs-lookup"><span data-stu-id="e9feb-408">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="e9feb-409">亦即，它會將 `(x * y) + z` 當作單一作業來執行，藉此將捨入錯誤減至最少。</span><span class="sxs-lookup"><span data-stu-id="e9feb-409">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="e9feb-410">例如 `FusedMultiplyAdd(1e308, 2.0, -1e308)` ，它會傳回 `1e308` 。</span><span class="sxs-lookup"><span data-stu-id="e9feb-410">An example is `FusedMultiplyAdd(1e308, 2.0, -1e308)`, which returns `1e308`.</span></span> <span data-ttu-id="e9feb-411">一般 `(1e308 * 2.0) - 1e308` 會傳回 `double.PositiveInfinity`。</span><span class="sxs-lookup"><span data-stu-id="e9feb-411">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="e9feb-412">對應至 `copySign` IEEE 作業，它會傳回 `x` 的值，但具有 `y` 的符號。</span><span class="sxs-lookup"><span data-stu-id="e9feb-412">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

### <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="e9feb-413">.NET 平台相依內建</span><span class="sxs-lookup"><span data-stu-id="e9feb-413">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="e9feb-414">已新增 API，允許存取特定效能導向的 CPU 指令，例如 **SIMD** 或**位元操作指令**集合。</span><span class="sxs-lookup"><span data-stu-id="e9feb-414">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="e9feb-415">這些指令可協助您在某些情況 (例如有效率地平行處理資料) 下大幅提升效能。</span><span class="sxs-lookup"><span data-stu-id="e9feb-415">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="e9feb-416">.NET 程式庫 (如果適用) 已開始使用這些指令來提升效能。</span><span class="sxs-lookup"><span data-stu-id="e9feb-416">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="e9feb-417">如需詳細資訊，請參閱[.Net 平臺相依內建函式](https://github.com/dotnet/designs/blob/master/accepted/2018/platform-intrinsics.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-417">For more information, see [.NET Platform-Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/2018/platform-intrinsics.md).</span></span>

### <a name="improved-net-core-version-apis"></a><span data-ttu-id="e9feb-418">改善的 .NET Core 版本 API</span><span class="sxs-lookup"><span data-stu-id="e9feb-418">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="e9feb-419">從 .NET Core 3.0 開始，.NET Core 所提供版本 API 現在會傳回您預期的資訊。</span><span class="sxs-lookup"><span data-stu-id="e9feb-419">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="e9feb-420">例如：</span><span class="sxs-lookup"><span data-stu-id="e9feb-420">For example:</span></span>

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result (notice the value includes any preview release information)
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="e9feb-421">重大變更。</span><span class="sxs-lookup"><span data-stu-id="e9feb-421">Breaking change.</span></span> <span data-ttu-id="e9feb-422">這是技術上的重大變更，因為版本設定配置已變更。</span><span class="sxs-lookup"><span data-stu-id="e9feb-422">This is technically a breaking change because the versioning scheme has changed.</span></span>

### <a name="fast-built-in-json-support"></a><span data-ttu-id="e9feb-423">快速的內建 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="e9feb-423">Fast built-in JSON support</span></span>

<span data-ttu-id="e9feb-424">.NET 使用者大多依賴[Newtonsoft](https://www.newtonsoft.com/json)和其他熱門的 json 程式庫，這會繼續是不錯的選擇。</span><span class="sxs-lookup"><span data-stu-id="e9feb-424">.NET users have largely relied on [Newtonsoft.Json](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="e9feb-425">`Newtonsoft.Json`使用 .NET 字串作為其基底資料類型，這是本質上的 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="e9feb-425">`Newtonsoft.Json` uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="e9feb-426">新的內建 JSON 支援是高效能、低配置，並可搭配 UTF-8 編碼的 JSON 文字使用。</span><span class="sxs-lookup"><span data-stu-id="e9feb-426">The new built-in JSON support is high-performance, low allocation, and works with UTF-8 encoded JSON text.</span></span> <span data-ttu-id="e9feb-427">如需 <xref:System.Text.Json> 命名空間和類型的詳細資訊，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="e9feb-427">For more information about the <xref:System.Text.Json> namespace and types, see the following articles:</span></span>

* [<span data-ttu-id="e9feb-428">.NET 中的 JSON 序列化-總覽</span><span class="sxs-lookup"><span data-stu-id="e9feb-428">JSON serialization in .NET - overview</span></span>](../../standard/serialization/system-text-json-overview.md)
* <span data-ttu-id="e9feb-429">[如何在 .net 中序列化和還原序列化 JSON](../../standard/serialization/system-text-json-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-429">[How to serialize and deserialize JSON in .NET](../../standard/serialization/system-text-json-how-to.md).</span></span>
* [<span data-ttu-id="e9feb-430">如何從 Newtonsoft 遷移至 System.web. Json</span><span class="sxs-lookup"><span data-stu-id="e9feb-430">How to migrate from Newtonsoft.Json to System.Text.Json</span></span>](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a><span data-ttu-id="e9feb-431">HTTP/2 支援</span><span class="sxs-lookup"><span data-stu-id="e9feb-431">HTTP/2 support</span></span>

<span data-ttu-id="e9feb-432"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 類型支援 HTTP/2 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e9feb-432">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="e9feb-433">如果啟用 HTTP/2，則會透過 TLS/ALPN 交涉 HTTP 通訊協定版本，並會在伺服器選擇使用它時使用 HTTP/2。</span><span class="sxs-lookup"><span data-stu-id="e9feb-433">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="e9feb-434">預設通訊協定會保持為 HTTP/1.1，但 HTTP/2 可以兩種不同的方式啟用。</span><span class="sxs-lookup"><span data-stu-id="e9feb-434">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="e9feb-435">首先，您可以設定 HTTP 要求訊息來使用 HTTP/2：</span><span class="sxs-lookup"><span data-stu-id="e9feb-435">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="e9feb-436">再來，您可以變更 <xref:System.Net.Http.HttpClient> 來預設使用 HTTP/2：</span><span class="sxs-lookup"><span data-stu-id="e9feb-436">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="e9feb-437">當您在開發應用程式時，經常會想要使用未加密的連線。</span><span class="sxs-lookup"><span data-stu-id="e9feb-437">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="e9feb-438">如果您知道目標端點會使用 HTTP/2，便可以針對 HTTP/2 開啟未加密的連線。</span><span class="sxs-lookup"><span data-stu-id="e9feb-438">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="e9feb-439">若要開啟它，您可以將 `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` 環境變數設定為 `1`，或是在應用程式內容中啟用它：</span><span class="sxs-lookup"><span data-stu-id="e9feb-439">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a><span data-ttu-id="e9feb-440">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e9feb-440">Next steps</span></span>

- [<span data-ttu-id="e9feb-441">檢查 .NET Core 2.2 和3.0 之間的重大變更。</span><span class="sxs-lookup"><span data-stu-id="e9feb-441">Review the breaking changes between .NET Core 2.2 and 3.0.</span></span>](../compatibility/2.2-3.0.md)
- [<span data-ttu-id="e9feb-442">請參閱 .NET Core 3.0 中適用于 Windows Forms 應用程式的重大變更。</span><span class="sxs-lookup"><span data-stu-id="e9feb-442">Review the breaking changes in .NET Core 3.0 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-30)
