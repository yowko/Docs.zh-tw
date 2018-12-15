---
title: .NET Core 3.0 的新功能
description: 了解 .NET Core 3.0 所提供的新功能。
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/04/2018
ms.openlocfilehash: 3ca833031eb8bb0f43a334f833f2e0075842d57d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53156666"
---
# <a name="whats-new-in-net-core-30-preview-1"></a><span data-ttu-id="1aa65-103">.NET Core 3.0 (Preview 1) 的新功能</span><span class="sxs-lookup"><span data-stu-id="1aa65-103">What's new in .NET Core 3.0 (Preview 1)</span></span>

<span data-ttu-id="1aa65-104">本文描述 .NET Core 3.0 (Preview 1) 的新功能。</span><span class="sxs-lookup"><span data-stu-id="1aa65-104">This article describes what is new in .NET Core 3.0 (preview 1).</span></span> <span data-ttu-id="1aa65-105">其中一個最大的增強功能是對 Windows 傳統型應用程式的支援 (僅限 Windows)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="1aa65-106">您可以運用名為「Windows 傳統型」的 .NET Core 3.0 元件來移植 Windows Forms 和 Windows Presentation Foundation (WPF) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1aa65-106">By utilizing a .NET Core 3.0 component called Windows Desktop, you can port your Windows Forms Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="1aa65-107">具體而言，只有在 Windows 上才支援「Windows 傳統型」元件。</span><span class="sxs-lookup"><span data-stu-id="1aa65-107">To be clear, the Windows Desktop component is only supported on Windows.</span></span> <span data-ttu-id="1aa65-108">如需詳細資訊，請參閱下面的 [Windows 傳統型](#windows-desktop)一節。</span><span class="sxs-lookup"><span data-stu-id="1aa65-108">For more information, see the section [Windows desktop](#windows-desktop) below.</span></span>

<span data-ttu-id="1aa65-109">.NET Core 3.0 新增 C# 8.0 支援。</span><span class="sxs-lookup"><span data-stu-id="1aa65-109">.NET Core 3.0 adds support for C# 8.0.</span></span>

<span data-ttu-id="1aa65-110">請立即在 Windows、Mac 及 Linux 上[下載並開始使用 .NET Core 3 Preview 1](https://aka.ms/netcore3download)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-110">[Download and get started with .NET Core 3 Preview 1](https://aka.ms/netcore3download) right now on Windows, Mac and Linux.</span></span> <span data-ttu-id="1aa65-111">您可以在 [.NET Core 3 Preview 1 版本資訊](https://aka.ms/netcore3releasenotes) \(英文\) 中查看完整的版本詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1aa65-111">You can see complete details of the release in the [.NET Core 3 Preview 1 release notes](https://aka.ms/netcore3releasenotes).</span></span>

<span data-ttu-id="1aa65-112">如需詳細資訊，請參閱 [.NET Core 3.0 Preview 1 公告](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-112">For more information, see the [.NET Core 3.0 Preview 1 announcement](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="1aa65-113">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="1aa65-113">.NET Standard 2.1</span></span>

<span data-ttu-id="1aa65-114">.NET Core 3.0 實作 .NET Standard 2.1。</span><span class="sxs-lookup"><span data-stu-id="1aa65-114">.NET Core 3.0 implements .NET Standard 2.1.</span></span>

## <a name="default-executables"></a><span data-ttu-id="1aa65-115">預設可執行檔</span><span class="sxs-lookup"><span data-stu-id="1aa65-115">Default executables</span></span>

<span data-ttu-id="1aa65-116">.NET Core 現在預設將會建置可執行檔。</span><span class="sxs-lookup"><span data-stu-id="1aa65-116">.NET Core will now build executables by default.</span></span> <span data-ttu-id="1aa65-117">這對於使用 .NET Core 全域安裝版本的應用程式來說，是一項新功能。</span><span class="sxs-lookup"><span data-stu-id="1aa65-117">This is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="1aa65-118">到目前為止，只有[獨立式部署](../deploying/index.md#self-contained-deployments-scd)具有可執行檔。</span><span class="sxs-lookup"><span data-stu-id="1aa65-118">Until now, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) had executables.</span></span>

<span data-ttu-id="1aa65-119">進行 `dotnet build` 或 `dotnet publish` 期間，如果與您所使用 SDK 的環境和平台相符，就會建立可執行檔。</span><span class="sxs-lookup"><span data-stu-id="1aa65-119">During `dotnet build` or `dotnet publish`, an executable is created provided that matches the environment and platform of the SDK you are using.</span></span> <span data-ttu-id="1aa65-120">針對這些可執行檔，您可以預期能夠進行與其他原生可執行檔相同的操作，例如：</span><span class="sxs-lookup"><span data-stu-id="1aa65-120">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="1aa65-121">您可以按兩下可執行檔。</span><span class="sxs-lookup"><span data-stu-id="1aa65-121">You can double-click on the executable.</span></span>
* <span data-ttu-id="1aa65-122">您可以直接從命令提示字元啟動應用程式，例如在 Windows 上為 `myapp.exe`，在 Linux 和 macOS 上為 `./myapp`。</span><span class="sxs-lookup"><span data-stu-id="1aa65-122">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

> [!NOTE]
> <span data-ttu-id="1aa65-123">不支援使用 `dotnet publish -r` 或 `dotnet build -r` 引數為其他執行階段環境指定特定執行階段。</span><span class="sxs-lookup"><span data-stu-id="1aa65-123">Specifying a specific runtime with `dotnet publish -r` or `dotnet build -r` arguments for other runtime environments isn't supported.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="1aa65-124">組建複本相依性</span><span class="sxs-lookup"><span data-stu-id="1aa65-124">Build copies dependencies</span></span>

<span data-ttu-id="1aa65-125">`dotnet build` 現在會從 NuGet 快取將您應用程式的 NuGet 相依性複製到組建輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="1aa65-125">`dotnet build` now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="1aa65-126">先前，只有在進行 `dotnet publish` 的過程中，才會複製相依性。</span><span class="sxs-lookup"><span data-stu-id="1aa65-126">Previously, dependencies were only copied as part of `dotnet publish`.</span></span> 

<span data-ttu-id="1aa65-127">有些作業 (例如連結和 Razor 頁面發佈) 仍然需要發佈。</span><span class="sxs-lookup"><span data-stu-id="1aa65-127">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>


## <a name="local-dotnet-tools"></a><span data-ttu-id="1aa65-128">本機 dotnet 工具</span><span class="sxs-lookup"><span data-stu-id="1aa65-128">Local dotnet tools</span></span>

<span data-ttu-id="1aa65-129">.NET Core 2.1 支援全域工具，.NET Core 3.0 現在則具有本機工具。</span><span class="sxs-lookup"><span data-stu-id="1aa65-129">While .NET Core 2.1 supported global tools, .NET Core 3.0 now has local tools.</span></span> <span data-ttu-id="1aa65-130">本機工具與全域工具類似，但與磁碟上的某個特定位置相關聯。</span><span class="sxs-lookup"><span data-stu-id="1aa65-130">Local tools are similar to global tools but are associated with a particular location on disk.</span></span> <span data-ttu-id="1aa65-131">這可針對個別專案和個別存放庫提供工具。</span><span class="sxs-lookup"><span data-stu-id="1aa65-131">This enables per-project and per-repository tooling.</span></span> <span data-ttu-id="1aa65-132">所有安裝在本機的工具都不是全域可用的工具。</span><span class="sxs-lookup"><span data-stu-id="1aa65-132">Any tool installed locally isn't available globally.</span></span>

<span data-ttu-id="1aa65-133">本機工具會倚賴您目前目錄中名為 `dotnet-tools.json` 的資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="1aa65-133">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="1aa65-134">此資訊清單檔會定義將可供使用的工具。</span><span class="sxs-lookup"><span data-stu-id="1aa65-134">This manifest file defines the tools to be available.</span></span> <span data-ttu-id="1aa65-135">藉由在存放庫的根目錄建立此資訊清單檔，您便可確保任何複製您程式碼的人員都可進行還原，以及使用成功運用您程式碼所需的工具。</span><span class="sxs-lookup"><span data-stu-id="1aa65-135">By creating this manifest file at the root of your repository, you ensure anyone cloning your code can restore and use the tools that are needed to successfully work with your code.</span></span>

<span data-ttu-id="1aa65-136">當有本機工具資訊清單檔可用時，請使用下列命令在本機自動下載並安裝這些工具：</span><span class="sxs-lookup"><span data-stu-id="1aa65-136">When the local tools manifest file is available, use the following command to automatically download and install those tools locally:</span></span>

```console
dotnet tool restore
```

<span data-ttu-id="1aa65-137">使用下列命令來執行本機工具：</span><span class="sxs-lookup"><span data-stu-id="1aa65-137">Run a local tool with the following command:</span></span>

```console
dotnet tool run <tool-command-name>
```

<span data-ttu-id="1aa65-138">呼叫本機工具時，dotnet 會沿著目錄結構向上搜尋資訊清單。</span><span class="sxs-lookup"><span data-stu-id="1aa65-138">When a local tool is called, dotnet searches for a manifest up the directory structure.</span></span> <span data-ttu-id="1aa65-139">找到工具資訊清單檔時，會在其中搜尋所要求的工具。</span><span class="sxs-lookup"><span data-stu-id="1aa65-139">When a tool manifest file is found, it is searched for the requested tool.</span></span> <span data-ttu-id="1aa65-140">如果找到工具，它會包含在 NuGet 全域套件位置中尋找該工具所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="1aa65-140">If the tool is found, it includes the information needed to find the tool in the NuGet global packages location.</span></span> 

<span data-ttu-id="1aa65-141">如果在資訊清單中找到工具，但在快取中找不到，使用者就會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="1aa65-141">If the tool is found in the manifest, but not the cache, the user receives an error.</span></span> <span data-ttu-id="1aa65-142">在 Preview 1 之後，此訊息將改進為要求使用者執行 `dotnet tool restore`。</span><span class="sxs-lookup"><span data-stu-id="1aa65-142">The message will be improved after Preview 1 to request the user run `dotnet tool restore`.</span></span>

<span data-ttu-id="1aa65-143">若要將本機工具新增至目錄，您必須先建立工具資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="1aa65-143">To add local tools to a directory, you need to first create the tool manifest file.</span></span> <span data-ttu-id="1aa65-144">在 Preview 1 之後，我們將提供一個建立工具資訊清單檔的機制，例如 dotnet 新範本。</span><span class="sxs-lookup"><span data-stu-id="1aa65-144">After Preview 1, we will offer a mechanism for creating tool manifest files, such as a dotnet new template.</span></span> <span data-ttu-id="1aa65-145">針對 Preview 1，您必須建立一個名為 `dotnet-tools.json` 且含有下列內容的檔案：</span><span class="sxs-lookup"><span data-stu-id="1aa65-145">For Preview 1 you must create the file named `dotnet-tools.json` with the following contents:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="1aa65-146">建立資訊清單之後，您可以使用下列命令在資訊清單中新增本機工具：</span><span class="sxs-lookup"><span data-stu-id="1aa65-146">Once the manifest is created, you can add local tools to it using:</span></span>

```console
dotnet tool install <toolPackageId>
```

<span data-ttu-id="1aa65-147">此命令會安裝最新的工具版本，除非已指定另一個版本。</span><span class="sxs-lookup"><span data-stu-id="1aa65-147">This command installs the latest version of the tool, unless another version is specified.</span></span>  <span data-ttu-id="1aa65-148">即使已自動選擇最新版本，仍然會將工具的版本寫入至工具資訊清單檔，以允許還原或執行正確的工具版本。</span><span class="sxs-lookup"><span data-stu-id="1aa65-148">Even if the latest version was automatically chosen, the version of the tool is written into the tool manifest file to allow the correct version of the tool to be restored or run.</span></span>

<span data-ttu-id="1aa65-149">工具資訊清單檔的設計目的是要允許手動編輯 – 當您要更新與存放庫搭配運作所需的版本時，可能會這麼做。</span><span class="sxs-lookup"><span data-stu-id="1aa65-149">The tool manifest file is designed to allow hand editing – which you might do to update the required version for working with the repository.</span></span>

<span data-ttu-id="1aa65-150">以下是一個範例 `dotnet-tools.json` 檔案：</span><span class="sxs-lookup"><span data-stu-id="1aa65-150">Here is an example `dotnet-tools.json` file:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

<span data-ttu-id="1aa65-151">若要從工具資訊清單檔中移除某個工具，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1aa65-151">To remove a tool from the tool manifest file, run the following command:</span></span>

```console
dotnet tool uninstall <toolPackageId>
```

<span data-ttu-id="1aa65-152">不論是全域工具還是區域工具，都需要一個相容的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="1aa65-152">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="1aa65-153">NuGet.org 上目前許多工具都以 .NET Core 執行階段 2.1 為目標。</span><span class="sxs-lookup"><span data-stu-id="1aa65-153">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="1aa65-154">若要在全域或本機安裝這些工具，您仍然需要安裝 [NET Core 2.1 執行階段](https://dotnet.microsoft.com/download/dotnet-core/2.1)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-154">To install those globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="1aa65-155">如需詳細資訊，請參閱[本機工具早期預覽文件](https://github.com/dotnet/cli/issues/10288) \(工具\)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-155">For more information, see [Local Tools Early Preview Documentation](https://github.com/dotnet/cli/issues/10288).</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="1aa65-156">Windows 桌面</span><span class="sxs-lookup"><span data-stu-id="1aa65-156">Windows desktop</span></span>

<span data-ttu-id="1aa65-157">從 .NET Core 3.0 Preview 1 開始，您可以使用 WPF 和 Windows Forms 來建置 Windows 傳統型應用程式。</span><span class="sxs-lookup"><span data-stu-id="1aa65-157">Starting with .NET Core 3.0 Preview 1, you can build Windows desktop applications using WPF and Windows Forms.</span></span> <span data-ttu-id="1aa65-158">這些架構也支援透過 [XAML 島](/windows/uwp/xaml-platform/xaml-host-controls)使用來自 Windows UI XAML 程式庫 (WinUI) 的新式控制項和 Fluent 樣式。</span><span class="sxs-lookup"><span data-stu-id="1aa65-158">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="1aa65-159">「Windows 傳統型」元件是 Windows .NET Core 3.0 SDK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="1aa65-159">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="1aa65-160">您可以使用下列 `dotnet` 命令來建立新的 WPF 或 Windows Forms 應用程式：</span><span class="sxs-lookup"><span data-stu-id="1aa65-160">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="1aa65-161">您也可以在 Visual Studio 2019 Preview 1 中開啟、啟動 .NET Core 3.0 WPF 和 Windows Forms 專案，以及對這新專案進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="1aa65-161">You can also open, launch, and debug .NET Core 3.0 WPF and Windows Forms projects in Visual Studio 2019 Preview 1.</span></span> <span data-ttu-id="1aa65-162">目前您可以在 Visual Studio 2017 15.9 中開啟這些專案，不過，並不支援這樣的案例 (而且您必須[啟用預覽](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/))。</span><span class="sxs-lookup"><span data-stu-id="1aa65-162">It's currently possible to open these projects in Visual Studio 2017 15.9, however, it isn't a supported scenario (and you need to [enable previews](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).</span></span>

<span data-ttu-id="1aa65-163">新專案與現有的 .NET Core 專案相同，但有新增一些項目。</span><span class="sxs-lookup"><span data-stu-id="1aa65-163">The new projects are the same as existing .NET Core projects, with a couple additions.</span></span> <span data-ttu-id="1aa65-164">以下是基本 .NET Core 主控台專案與基本 Windows Forms 和 WPF 專案的比較。</span><span class="sxs-lookup"><span data-stu-id="1aa65-164">Here is the comparison of the basic .NET Core console project and a basic Windows Forms and WPF project.</span></span>

<span data-ttu-id="1aa65-165">在 .NET Core 主控台專案中，專案會使用 `Microsoft.NET.Sdk` SDK，並透過 `netcoreapp3.0` 目標架構宣告與 .NET Core 3.0 的相依性。</span><span class="sxs-lookup"><span data-stu-id="1aa65-165">In a .NET Core console project, the project uses the `Microsoft.NET.Sdk` SDK and declares a dependency on .NET Core 3.0 via the `netcoreapp3.0` target framework.</span></span> <span data-ttu-id="1aa65-166">若要建立 Windows 傳統型應用程式，請使用 `Microsoft.NET.Sdk.WindowsDesktop` SDK，然後選擇要使用的 UI 架構：</span><span class="sxs-lookup"><span data-stu-id="1aa65-166">To create a Windows Desktop app, use the `Microsoft.NET.Sdk.WindowsDesktop` SDK and choose which UI framework to use:</span></span>

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="1aa65-167">若要選擇 Windows Forms 而不選擇 WPF，請設定 `UseWindowsForms` 而不要設定 `UseWPF`：</span><span class="sxs-lookup"><span data-stu-id="1aa65-167">To choose Windows Forms over WPF, set `UseWindowsForms` instead of `UseWPF`:</span></span>

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="1aa65-168">如果應用程式同時使用這兩種架構 (例如當 Windows Forms 對話方塊裝載 WPF 控制項時)，則可以將 `UseWPF` 和 `UseWindowsForms` 都設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="1aa65-168">Both `UseWPF` and `UseWindowsForms` can be set to `true` if the app uses both frameworks, for example when a Windows Forms dialog is hosting a WPF control.</span></span>

<span data-ttu-id="1aa65-169">請在 [dotnet/winforms](https://github.com/dotnet/winforms/issues)、[dotnet/wpf](https://github.com/dotnet/wpf/issues) 及 [dotnet/core](https://github.com/dotnet/core/issues) 存放庫上分享您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="1aa65-169">Please share your feedback on the [dotnet/winforms](https://github.com/dotnet/winforms/issues),  [dotnet/wpf](https://github.com/dotnet/wpf/issues) and [dotnet/core](https://github.com/dotnet/core/issues) repos.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="1aa65-170">快速的內建 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="1aa65-170">Fast built-in JSON support</span></span>

<span data-ttu-id="1aa65-171">`System.Text.Json.Utf8JsonReader` 是一個高效能、低配置、只能順向讀取的 UTF-8 編碼 JSON 文字讀取器，會從 `ReadOnlySpan<byte>` 開始讀取。</span><span class="sxs-lookup"><span data-stu-id="1aa65-171">`System.Text.Json.Utf8JsonReader` is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="1aa65-172">`Utf8JsonReader` 是一個基礎的低階類型，可用來建置自訂剖析器和還原序列化程式。</span><span class="sxs-lookup"><span data-stu-id="1aa65-172">The `Utf8JsonReader` is a foundational, low-level type, that can be leveraged to build custom parsers and deserializers.</span></span> <span data-ttu-id="1aa65-173">使用新的 `Utf8JsonReader` 來讀取 JSON 承載會比使用來自 [Json.NET](https://www.newtonsoft.com/json) 的讀取器快兩倍。</span><span class="sxs-lookup"><span data-stu-id="1aa65-173">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from [Json.NET](https://www.newtonsoft.com/json).</span></span> <span data-ttu-id="1aa65-174">它會等到您需要將 JSON 權杖實現為 (UTF-16) 字串時，才進行配置。</span><span class="sxs-lookup"><span data-stu-id="1aa65-174">It does not allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="1aa65-175">這個新 API 將包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="1aa65-175">This new API will include the following components:</span></span>

* <span data-ttu-id="1aa65-176">在 Preview 1 中：JSON 讀取器 (循序存取)</span><span class="sxs-lookup"><span data-stu-id="1aa65-176">In Preview 1: JSON reader (sequential access)</span></span>
* <span data-ttu-id="1aa65-177">在即將推出的版本中：JSON 寫入器、DOM (隨機存取)、POCO 序列化程式、POCO 還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="1aa65-177">Coming next: JSON writer, DOM (random access), poco serializer, poco deserializer</span></span>

<span data-ttu-id="1aa65-178">以下是 `Utf8JsonReader` 的基本讀取器迴圈，您可以使用它作為起點：</span><span class="sxs-lookup"><span data-stu-id="1aa65-178">Here is the basic reader loop for the `Utf8JsonReader` that can be used as a starting point:</span></span>

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

<span data-ttu-id="1aa65-179">.NET 生態系統倚賴 [Json.NET](https://www.newtonsoft.com/json) 及其他熱門的 JSON 程式庫 (這些仍持續是絕佳的選擇)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-179">The .NET ecosystem has relied on [Json.NET](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="1aa65-180">JSON.NET 使用 .NET 字串作為其基底資料類型，實際上就是 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="1aa65-180">JSON.NET uses .NET strings as its base datatype, which are UTF-16 under the hood.</span></span> 

<span data-ttu-id="1aa65-181">在 .NET Core 2.1 和 3.0 中，我們新增了新的 API，可讓您根據使用 `Span<T>` 和 UTF-8 字串，撰寫所需記憶體少很多且更符合高輸送量應用程式 (例如 Kestrel、ASP.NET Core Web 伺服器) 需求的 JSON API (例如 `Utf8JsonReader`)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-181">In .NET Core 2.1 and 3.0, we added new APIs that makes it possible to write JSON APIs (such as `Utf8JsonReader`) that require much less memory, based on using `Span<T>` and UTF-8 strings, and better serve the needs of high-throughput applications like Kestrel, ASP.NET Core web server.</span></span>

## <a name="ranges-and-indices"></a><span data-ttu-id="1aa65-182">範圍和索引</span><span class="sxs-lookup"><span data-stu-id="1aa65-182">Ranges and indices</span></span>

<span data-ttu-id="1aa65-183">新的 `Index` 類型可用於編製索引。</span><span class="sxs-lookup"><span data-stu-id="1aa65-183">The new `Index` type can be used for indexing.</span></span> <span data-ttu-id="1aa65-184">您可以從會從開頭算起的 `int` 或使用會從結尾算起的前置詞 `^` 運算子 (C#)，來建立一個索引：</span><span class="sxs-lookup"><span data-stu-id="1aa65-184">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="1aa65-185">此外，還有 `Range` 類型，此類型由兩個 `Index` 值所組成 (一個代表開頭，一個代表結尾)，並可用 `x..y` 範圍運算式 (C#) 來撰寫。</span><span class="sxs-lookup"><span data-stu-id="1aa65-185">There is also a `Range` type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="1aa65-186">您可以接著使用 `Range` 來編製索引以產生配量：</span><span class="sxs-lookup"><span data-stu-id="1aa65-186">You can then index with a `Range` in order to produce a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

> [!NOTE]
> <span data-ttu-id="1aa65-187">只有 [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) 才支援 `Range` 和 `Index` 的語法。</span><span class="sxs-lookup"><span data-stu-id="1aa65-187">Only [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) supports syntax for `Range` and `Index`.</span></span>

## <a name="async-streams"></a><span data-ttu-id="1aa65-188">非同步資料流</span><span class="sxs-lookup"><span data-stu-id="1aa65-188">Async streams</span></span>

<span data-ttu-id="1aa65-189">`IAsyncEnumerable<T>` 類型是 `IEnumerable<T>` 的新非同步版本。</span><span class="sxs-lookup"><span data-stu-id="1aa65-189">The `IAsyncEnumerable<T>` type is a new asynchronous version of `IEnumerable<T>`.</span></span> <span data-ttu-id="1aa65-190">此語言可讓您針對這些執行 `await foreach` 以取用其元素，然後對它們執行 `yield return` 以產生元素。</span><span class="sxs-lookup"><span data-stu-id="1aa65-190">The language lets you `await foreach` over these to consume their elements, and `yield return` to them to produce elements.</span></span>

<span data-ttu-id="1aa65-191">下列範例同時示範如何產生和取用非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="1aa65-191">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="1aa65-192">`foreach` 是非同步陳述式，其本身會使用 `yield return` 來為呼叫端產生非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="1aa65-192">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="1aa65-193">此模式 (使用 `yield return`) 是針對產生非同步資料流建議採用的模型。</span><span class="sxs-lookup"><span data-stu-id="1aa65-193">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

> [!WARNING]
> <span data-ttu-id="1aa65-194">.NET Core 3.0 Preview 1 目前有 `await foreach` 方面的 Bug。</span><span class="sxs-lookup"><span data-stu-id="1aa65-194">.NET Core 3.0 Preview 1 currently has a bug with `await foreach`.</span></span> <span data-ttu-id="1aa65-195">請改用 `GetEnumerator` 和 `MoveNext` 來處理元素。</span><span class="sxs-lookup"><span data-stu-id="1aa65-195">Instead, use `GetEnumerator` and `MoveNext` to process elements.</span></span> <span data-ttu-id="1aa65-196">如需詳細資訊，請參閱 [roslyn/#31268](https://github.com/dotnet/roslyn/issues/31268)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-196">For more information, see [roslyn/#31268](https://github.com/dotnet/roslyn/issues/31268).</span></span>

<span data-ttu-id="1aa65-197">除了能夠執行 `await foreach` 之外，您也可以建立非同步迭代器，例如建立一個會傳回 `IAsyncEnumerable/IAsyncEnumerator` 以供您在其中執行 `await` 和 `yield` 的迭代器。</span><span class="sxs-lookup"><span data-stu-id="1aa65-197">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="1aa65-198">針對需要處置的物件，您可以使用各種 BCL 類型 (例如 `Stream` 和 `Timer`) 所實作的 `IAsyncDisposable`。</span><span class="sxs-lookup"><span data-stu-id="1aa65-198">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

> [!NOTE]
> <span data-ttu-id="1aa65-199">只有 [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) 才支援 `await foreach` 語法。</span><span class="sxs-lookup"><span data-stu-id="1aa65-199">Only [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) supports `await foreach` syntax.</span></span>

## <a name="type-sequencereader"></a><span data-ttu-id="1aa65-200">類型：SequenceReader</span><span class="sxs-lookup"><span data-stu-id="1aa65-200">Type: SequenceReader</span></span>

<span data-ttu-id="1aa65-201">在 .NET Core 3.0 中已新增 `System.Buffers.SequenceReader`，這可用來作為 `ReadOnlySequence<T>` 的讀取器。</span><span class="sxs-lookup"><span data-stu-id="1aa65-201">In .NET Core 3.0, `System.Buffers.SequenceReader` has been added which can be used as a reader for `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="1aa65-202">這可讓您以輕鬆、高效能、低配置的方式，剖析可跨多個支援緩衝區的 `System.IO.Pipelines` 資料。</span><span class="sxs-lookup"><span data-stu-id="1aa65-202">This allows easy, high performance, low allocation parsing of `System.IO.Pipelines` data that can cross multiple backing buffers.</span></span> 

<span data-ttu-id="1aa65-203">下列範例將輸入 `Sequence` 分成以 `CR/LF` 分隔的有效行：</span><span class="sxs-lookup"><span data-stu-id="1aa65-203">The following example breaks an input `Sequence` into valid `CR/LF` delimited lines:</span></span>

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a><span data-ttu-id="1aa65-204">類型：MetadataLoadContext</span><span class="sxs-lookup"><span data-stu-id="1aa65-204">Type: MetadataLoadContext</span></span>

<span data-ttu-id="1aa65-205">已新增 `MetadataLoadContext` 類型，可讓您讀取組件中繼資料，而不會影響到呼叫端的應用程式網域。</span><span class="sxs-lookup"><span data-stu-id="1aa65-205">The `MetadataLoadContext` type has been added that enables reading assembly metadata without affecting the caller’s application domain.</span></span> <span data-ttu-id="1aa65-206">讀取組件 (包括為與目前執行階段環境不同的架構和平台建置的組件) 時，會將組件當作資料來讀取。</span><span class="sxs-lookup"><span data-stu-id="1aa65-206">Assemblies are read as data, including assemblies built for different architectures and platforms than the current runtime environment.</span></span> <span data-ttu-id="1aa65-207">`MetadataLoadContext` 與 <xref:System.Reflection.Assembly.ReflectionOnlyLoad*> (只有在 .NET Framework 中才有提供) 重疊。</span><span class="sxs-lookup"><span data-stu-id="1aa65-207">`MetadataLoadContext` overlaps with the <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, which is only available in the .NET Framework.</span></span>

<span data-ttu-id="1aa65-208">`MetdataLoadContext` 是 [System.Reflection.MetadataLoadContext 套件](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext)中所提供的類型。</span><span class="sxs-lookup"><span data-stu-id="1aa65-208">`MetdataLoadContext` is available in the [System.Reflection.MetadataLoadContext package](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span></span> <span data-ttu-id="1aa65-209">這是一個 .NET Standard 2.0 套件。</span><span class="sxs-lookup"><span data-stu-id="1aa65-209">It is a .NET Standard 2.0 package.</span></span>

<span data-ttu-id="1aa65-210">`MetadataLoadContext` 公開 API 的方式與 <xref:System.Runtime.Loader.AssemblyLoadContext> 類型類似，但並非以該類型為基礎。</span><span class="sxs-lookup"><span data-stu-id="1aa65-210">The `MetadataLoadContext` exposes APIs similar to the <xref:System.Runtime.Loader.AssemblyLoadContext> type, but is not based on that type.</span></span> <span data-ttu-id="1aa65-211">就像 <xref:System.Runtime.Loader.AssemblyLoadContext> 一樣，`MetadataLoadContext` 也可讓您載入已隔離之組件載入 Universe 內的組件。</span><span class="sxs-lookup"><span data-stu-id="1aa65-211">Much like <xref:System.Runtime.Loader.AssemblyLoadContext>, the `MetadataLoadContext` enables loading assemblies within an isolated assembly loading universe.</span></span> <span data-ttu-id="1aa65-212">`MetdataLoadContext` API 會傳回 <xref:System.Reflection.Assembly> 物件，以讓您使用熟悉的反映 API。</span><span class="sxs-lookup"><span data-stu-id="1aa65-212">`MetdataLoadContext` APIs return <xref:System.Reflection.Assembly> objects, enabling the use of familiar reflection APIs.</span></span> <span data-ttu-id="1aa65-213">執行導向 API (例如 [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127)) 不是允許使用的 API，將會擲回 InvalidOperationException。</span><span class="sxs-lookup"><span data-stu-id="1aa65-213">Execution-oriented APIs, such as [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), are not allowed and will throw InvalidOperationException.</span></span>

<span data-ttu-id="1aa65-214">下列範例示範如何在實作指定介面的組件中尋找具體的類型：</span><span class="sxs-lookup"><span data-stu-id="1aa65-214">The following sample demonstrates how to find concrete types in an assembly that implements a given interface:</span></span>

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

<span data-ttu-id="1aa65-215">`MetadataLoadContext` 的案例包括設計階段功能、組建階段工具及執行階段啟動功能，這些功能需要將一組組件當作資料來檢查，並將所有檔案鎖定及在執行檢查後將記憶體釋出。</span><span class="sxs-lookup"><span data-stu-id="1aa65-215">Scenarios for `MetadataLoadContext` include design-time features, build-time tooling, and runtime light-up features that need to inspect a set of assemblies as data and have all file locks and memory freed after inspection is performed.</span></span>

<span data-ttu-id="1aa65-216">`MetadataLoadContext` 具有一個會傳送給其建構函式的解析程式類別。</span><span class="sxs-lookup"><span data-stu-id="1aa65-216">The `MetadataLoadContext` has a resolver class passed to its constructor.</span></span> <span data-ttu-id="1aa65-217">此解析程式的工作是在已指定 `AssemblyName` 的情況下載入 `Assembly`。</span><span class="sxs-lookup"><span data-stu-id="1aa65-217">The resolver's job is to load an `Assembly` given its `AssemblyName`.</span></span> <span data-ttu-id="1aa65-218">此解析程式類別衍生自抽象的 `MetadataAssemblyResolver` 類別。</span><span class="sxs-lookup"><span data-stu-id="1aa65-218">The resolver class derives from the abstract `MetadataAssemblyResolver` class.</span></span> <span data-ttu-id="1aa65-219">提供路徑型案例的解析器實作時，會以 `PathAssemblyResolver` 提供。</span><span class="sxs-lookup"><span data-stu-id="1aa65-219">An implementation of the resolver for path-based scenarios is provided with `PathAssemblyResolver`.</span></span>

<span data-ttu-id="1aa65-220">[MetadataLoadContext 測試](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) 示範許多使用案例。</span><span class="sxs-lookup"><span data-stu-id="1aa65-220">The [MetadataLoadContext tests](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstrate many use cases.</span></span> <span data-ttu-id="1aa65-221">[組件測試](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs)是一個絕佳的起點。</span><span class="sxs-lookup"><span data-stu-id="1aa65-221">The [Assembly tests](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) are a good place to start.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="1aa65-222">Linux 上的 TLS 1.3 和 OpenSSL 1.1.1</span><span class="sxs-lookup"><span data-stu-id="1aa65-222">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="1aa65-223">.NET Core 現在會利用 [OpenSSL 1.1.1 中的 TLS 1.3 支援](https://www.openssl.org/blog/blog/2018/09/11/release111/) (當在指定的環境中有提供時)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-223">.NET Core will now take advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it is available in a given environment.</span></span> <span data-ttu-id="1aa65-224">依據 [OpenSSL 小組](https://www.openssl.org/blog/blog/2018/09/11/release111/)，TLS 1.3 有多項優點：</span><span class="sxs-lookup"><span data-stu-id="1aa65-224">There are multiple benefits of TLS 1.3, per the [OpenSSL team](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span></span>

* <span data-ttu-id="1aa65-225">因為用戶端與伺服器之間的來回行程次數減少，所以改善了連線時間。</span><span class="sxs-lookup"><span data-stu-id="1aa65-225">Improved connection times due to a reduction in the number of round trips required between the client and server.</span></span>

* <span data-ttu-id="1aa65-226">因為移除各種已淘汰和不安全的密碼編譯演算法，並加密更大部分的連線信號交換，所以提升了安全性。</span><span class="sxs-lookup"><span data-stu-id="1aa65-226">Improved security due to the removal of various obsolete and insecure cryptographic algorithms and encryption of more of the connection handshake.</span></span>

<span data-ttu-id="1aa65-227">.NET Core 3.0 Preview 1 能夠利用 **OpenSSL 1.1.1**、**OpenSSL 1.1.0** 或 **OpenSSL 1.0.2** (不論在 Linux 系統上找到的最佳版本是哪一個)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-227">.NET Core 3.0 Preview 1 is capable of utilizing **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** (whatever the best version found is, on a Linux system).</span></span>  <span data-ttu-id="1aa65-228">當 **OpenSSL 1.1.1** 可供使用時，在使用 `SslProtocols.None` (系統預設通訊協定) 的情況下，如果用戶端和伺服器都支援 **TLS 1.3**，SslStream 和 HttpClient 類型就會使用 **TLS 1.3**。</span><span class="sxs-lookup"><span data-stu-id="1aa65-228">When **OpenSSL 1.1.1** is available the SslStream and HttpClient types will use **TLS 1.3** when using `SslProtocols.None` (system default protocols), assuming both the client and server support **TLS 1.3**.</span></span>

<span data-ttu-id="1aa65-229">下列範例示範連線至 <https://www.cloudflare.com> 之 Ubuntu 18.10 上的 .NET Core 3.0 Preview 1：</span><span class="sxs-lookup"><span data-stu-id="1aa65-229">The following sample demonstrates .NET Core 3.0 Preview 1 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
><span data-ttu-id="1aa65-230">Windows 和 macOS 尚未支援 **TLS 1.3**。</span><span class="sxs-lookup"><span data-stu-id="1aa65-230">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="1aa65-231">.NET Core 3.0 將在有支援可用時，在這些作業系統上支援 **TLS 1.3**。</span><span class="sxs-lookup"><span data-stu-id="1aa65-231">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

## <a name="cryptography"></a><span data-ttu-id="1aa65-232">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="1aa65-232">Cryptography</span></span>

<span data-ttu-id="1aa65-233">已新增對 **AES-GCM** 和 **AES-CCM** 加密方式的支援 (透過 `System.Security.Cryptography.AesGcm` 和 `System.Security.Cryptography.AesCcm` 來實作)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-233">Support has been added for **AES-GCM** and **AES-CCM** ciphers, implemented via `System.Security.Cryptography.AesGcm` and `System.Security.Cryptography.AesCcm`.</span></span> <span data-ttu-id="1aa65-234">這些演算法既是[搭配關聯資料的驗證加密 (AEAD) 演算法](https://en.wikipedia.org/wiki/Authenticated_encryption)，也是最先新增至 .NET Core 的「驗證加密」(AE) 演算法。</span><span class="sxs-lookup"><span data-stu-id="1aa65-234">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption), and the first Authenticated Encryption (AE) algorithms added to .NET Core.</span></span>

<span data-ttu-id="1aa65-235">下列程式碼示範如何使用 **AesGcm** 加密方式將隨機資料加密和解密。</span><span class="sxs-lookup"><span data-stu-id="1aa65-235">The following code demonstrates using **AesGcm** cipher to encrypt and decrypt random data.</span></span>

<span data-ttu-id="1aa65-236">**AesCcm** 的程式碼看起來幾乎完全相同 (只有類別變數名稱會有所不同)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-236">The code for **AesCcm** would look almost identical (only the class variable names would be different).</span></span>

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="1aa65-237">密碼編譯金鑰匯入/匯出</span><span class="sxs-lookup"><span data-stu-id="1aa65-237">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="1aa65-238">.NET Core 3.0 Preview 1 支援從標準格式匯入及匯出非對稱式公開金鑰與私密金鑰，而無須使用 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="1aa65-238">.NET Core 3.0 Preview 1 supports the import and export of asymmetric public and private keys from standard formats, without needing to use an X.509 certificate.</span></span>

<span data-ttu-id="1aa65-239">所有金鑰類型 (RSA、DSA、ECDsa、ECDiffieHellman) 都支援適用於公開金鑰的 **X.509 SubjectPublicKeyInfo** 格式，以及適用於私密金鑰的 **PKCS#8 PrivateKeyInfo** 和 **PKCS#8 EncryptedPrivateKeyInfo** 格式。</span><span class="sxs-lookup"><span data-stu-id="1aa65-239">All key types (RSA, DSA, ECDsa, ECDiffieHellman) support the **X.509 SubjectPublicKeyInfo** format for public keys, and the **PKCS#8 PrivateKeyInfo** and **PKCS#8 EncryptedPrivateKeyInfo** formats for private keys.</span></span> <span data-ttu-id="1aa65-240">RSA 還額外支援 **PKCS#1 RSAPublicKey** 和 **PKCS#1 RSAPrivateKey**。</span><span class="sxs-lookup"><span data-stu-id="1aa65-240">RSA additionally supports **PKCS#1 RSAPublicKey** and **PKCS#1 RSAPrivateKey**.</span></span> <span data-ttu-id="1aa65-241">所有匯出方法都會產生 DER 編碼的二進位資料，而匯出方法也是如此。</span><span class="sxs-lookup"><span data-stu-id="1aa65-241">The export methods all produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="1aa65-242">如果金鑰是以適合文字的 PEM 格式儲存的，呼叫端在呼叫匯入方法之前，就必須先對內容進行 Base64 解碼。</span><span class="sxs-lookup"><span data-stu-id="1aa65-242">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

<span data-ttu-id="1aa65-243">若要檢查 PKCS#8 檔案，可以使用 `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` 類別。</span><span class="sxs-lookup"><span data-stu-id="1aa65-243">PKCS#8 files can be inspected with the `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` class.</span></span>

<span data-ttu-id="1aa65-244">若要檢查和操作 PFX/PKCS#12 檔案，可以分別使用 `System.Security.Cryptography.Pkcs.Pkcs12Info` 和 `System.Security.Cryptography.Pkcs.Pkcs12Builder`。</span><span class="sxs-lookup"><span data-stu-id="1aa65-244">PFX/PKCS#12 files can be inspected and manipulated with `System.Security.Cryptography.Pkcs.Pkcs12Info` and `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectively.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="1aa65-245">適用於 Linux 的 SerialPort</span><span class="sxs-lookup"><span data-stu-id="1aa65-245">SerialPort for Linux</span></span>

<span data-ttu-id="1aa65-246">.NET Core 3.0 現已在 Linux 上支援 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1aa65-246">.NET Core 3.0 now supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="1aa65-247">先前，.NET Core 僅支援在 Windows 上使用 `SerialPort` 類型。</span><span class="sxs-lookup"><span data-stu-id="1aa65-247">Previously, .NET Core only supported using the `SerialPort` type on Windows.</span></span>

## <a name="more-bcl-improvements"></a><span data-ttu-id="1aa65-248">更多 BCL 改進</span><span class="sxs-lookup"><span data-stu-id="1aa65-248">More BCL Improvements</span></span>

<span data-ttu-id="1aa65-249">在 .NET Core 3.0 中，已將在 .NET Core 2.1 中導入的 `Span<T>`、`Memory<T>` 及相關類型最佳化。</span><span class="sxs-lookup"><span data-stu-id="1aa65-249">The `Span<T>`, `Memory<T>`, and related types that were introduced in .NET Core 2.1, have been optimized in .NET Core 3.0.</span></span> <span data-ttu-id="1aa65-250">範圍建構、配量、剖析及格式化等常見作業現在執行效能更佳。</span><span class="sxs-lookup"><span data-stu-id="1aa65-250">Common operations such as span construction, slicing, parsing, and formatting now perform better.</span></span> 

<span data-ttu-id="1aa65-251">此外，`String` 這類類型也有隱含的改進，使其在搭配 `Dictionary<TKey, TValue>` 及其他集合作為金鑰使用時更有效率。</span><span class="sxs-lookup"><span data-stu-id="1aa65-251">Additionally, types like `String` have seen under-the-cover improvements to make them more efficient when used as keys with `Dictionary<TKey, TValue>` and other collections.</span></span> <span data-ttu-id="1aa65-252">您無須進行任何程式碼變更，即可享有這些改進的好處。</span><span class="sxs-lookup"><span data-stu-id="1aa65-252">No code changes are required to benefit from these improvements.</span></span>

<span data-ttu-id="1aa65-253">以下也是 .NET Core 3 Preview 1 中新增的改進：</span><span class="sxs-lookup"><span data-stu-id="1aa65-253">The following improvements are also new in .NET Core 3 Preview 1:</span></span>

* <span data-ttu-id="1aa65-254">HttpClient 內建 Brotli 支援</span><span class="sxs-lookup"><span data-stu-id="1aa65-254">Brotli support built in to HttpClient</span></span>
* <span data-ttu-id="1aa65-255">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span><span class="sxs-lookup"><span data-stu-id="1aa65-255">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span></span>
* <span data-ttu-id="1aa65-256">Unsafe.Unbox</span><span class="sxs-lookup"><span data-stu-id="1aa65-256">Unsafe.Unbox</span></span>
* <span data-ttu-id="1aa65-257">CancellationToken.Unregister</span><span class="sxs-lookup"><span data-stu-id="1aa65-257">CancellationToken.Unregister</span></span>
* <span data-ttu-id="1aa65-258">複雜算術運算子</span><span class="sxs-lookup"><span data-stu-id="1aa65-258">Complex arithmetic operators</span></span>
* <span data-ttu-id="1aa65-259">適用於 TCP 持續連線的通訊端 API</span><span class="sxs-lookup"><span data-stu-id="1aa65-259">Socket APIs for TCP keep alive</span></span>
* <span data-ttu-id="1aa65-260">StringBuilder.GetChunks</span><span class="sxs-lookup"><span data-stu-id="1aa65-260">StringBuilder.GetChunks</span></span>
* <span data-ttu-id="1aa65-261">IPEndPoint 剖析</span><span class="sxs-lookup"><span data-stu-id="1aa65-261">IPEndPoint parsing</span></span>
* <span data-ttu-id="1aa65-262">RandomNumberGenerator.GetInt32</span><span class="sxs-lookup"><span data-stu-id="1aa65-262">RandomNumberGenerator.GetInt32</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="1aa65-263">階層式編譯</span><span class="sxs-lookup"><span data-stu-id="1aa65-263">Tiered compilation</span></span>

<span data-ttu-id="1aa65-264">使用 .NET Core 3.0 時，預設會開啟[階層式編譯](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-264">[Tiered compilation](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="1aa65-265">這是一項可讓執行階段更彈性使用 Just-In-Time (JIT) 編譯器的功能，可在啟動時及將輸送量最大化時獲得更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="1aa65-265">It is a feature that enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance, both at startup and to maximize throughput.</span></span>

<span data-ttu-id="1aa65-266">此功能在 [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) 中是新增為選用功能，然後在 [.NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/) 中為預設啟用的功能。</span><span class="sxs-lookup"><span data-stu-id="1aa65-266">This feature was added as an opt-in feature in [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) and then was enabled by default in [.NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span></span> <span data-ttu-id="1aa65-267">之後，在 .NET Core 2.2 版本中則又還原回選用功能。</span><span class="sxs-lookup"><span data-stu-id="1aa65-267">Subsequently, it has been reverted back to opt in with the .NET Core 2.2 release.</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="1aa65-268">ARM64 Linux 支援</span><span class="sxs-lookup"><span data-stu-id="1aa65-268">ARM64 Linux support</span></span>

<span data-ttu-id="1aa65-269">我們正於此版本中新增適用於 Linux 的 ARM64 支援。</span><span class="sxs-lookup"><span data-stu-id="1aa65-269">We are adding support for ARM64 for Linux this release.</span></span> <span data-ttu-id="1aa65-270">針對不同內容，我們藉由 .NET Core 2.1 新增了適用於 Linux 及藉由 .NET Core 2.2 新增了適用於 Windows 的 ARM32 支援。</span><span class="sxs-lookup"><span data-stu-id="1aa65-270">For context, we added support for ARM32 for Linux with .NET Core 2.1 and Windows with .NET Core 2.2.</span></span> <span data-ttu-id="1aa65-271">ARM64 的主要使用案例目前是搭配 IoT 案例。</span><span class="sxs-lookup"><span data-stu-id="1aa65-271">The primary use case for ARM64 is currently with IoT scenarios.</span></span>

<span data-ttu-id="1aa65-272">[針對適用於 ARM64 的 .NET Core 有提供 Docker 映像](https://hub.docker.com/r/microsoft/dotnet/) (Alpine、Debian 及 Ubuntu Docker 映像)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-272">Alpine, Debian and Ubuntu [Docker images are available for .NET Core for ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

<span data-ttu-id="1aa65-273">如需詳細資訊，請參閱 [.NET Core ARM64 狀態](https://github.com/dotnet/announcements/issues/82) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="1aa65-273">Please check [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) for more information.</span></span>

>[!NOTE]
> <span data-ttu-id="1aa65-274">目前尚未提供 **ARM64** Windows 支援。</span><span class="sxs-lookup"><span data-stu-id="1aa65-274">**ARM64** Windows support isn't yet available.</span></span>
