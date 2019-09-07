---
title: .NET Core 發佈封裝
description: 了解如何封裝、命名以及建立 .NET Core 版本以進行發佈。
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: d72677cba1e7685f8e05cf479ec508683dd77b55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394152"
---
# <a name="net-core-distribution-packaging"></a><span data-ttu-id="b6b34-103">.NET Core 發佈封裝</span><span class="sxs-lookup"><span data-stu-id="b6b34-103">.NET Core distribution packaging</span></span>

<span data-ttu-id="b6b34-104">隨著 .NET Core 可在越來越多的平台上使用，了解如何封裝、命名和建立 .NET Core 版本是有用的。</span><span class="sxs-lookup"><span data-stu-id="b6b34-104">As .NET Core becomes available on more and more platforms, it's useful to learn how to package, name, and version it.</span></span> <span data-ttu-id="b6b34-105">如此一來，套件維護人員可以協助確保一致的體驗，無論使用者選擇在何處執行 .NET。</span><span class="sxs-lookup"><span data-stu-id="b6b34-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="b6b34-106">本文適用於符合下列項目的使用者：</span><span class="sxs-lookup"><span data-stu-id="b6b34-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="b6b34-107">嘗試從來源建置 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="b6b34-107">Attempting to build .NET Core from source.</span></span>
- <span data-ttu-id="b6b34-108">希望對可能影響產生之配置或套件的 .NET Core CLI 進行變更。</span><span class="sxs-lookup"><span data-stu-id="b6b34-108">Wanting to make changes to the .NET Core CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="b6b34-109">磁碟配置</span><span class="sxs-lookup"><span data-stu-id="b6b34-109">Disk layout</span></span>

<span data-ttu-id="b6b34-110">安裝後，.NET Core 包含幾個元件，這些元件在檔案系統中以下列所示進行配置：</span><span class="sxs-lookup"><span data-stu-id="b6b34-110">When installed, .NET Core consists of several components that are laid out as follows in the filesystem:</span></span>

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
├── packs
│   ├── Microsoft.AspNetCore.App.Ref
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref
│       └── <netstandard version>        (15)
├── shared
│   ├── Microsoft.NETCore.App
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App
│       └── <desktop app version> (7)
└── templates
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="b6b34-111">(1) **dotnet** 主機 (也稱為"muxer") 有兩個不同的角色：啟用執行階段以啟動應用程式，以及啟用 SDK 將命令分派給它。</span><span class="sxs-lookup"><span data-stu-id="b6b34-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="b6b34-112">主機是原生可執行檔 (`dotnet.exe`)。</span><span class="sxs-lookup"><span data-stu-id="b6b34-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="b6b34-113">雖然是單一主機，但大部分其他元件都會位於已建立版本的目錄中 (2、3、5、6)。</span><span class="sxs-lookup"><span data-stu-id="b6b34-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="b6b34-114">這表示多個版本可能會存在於系統上，因為為並排安裝。</span><span class="sxs-lookup"><span data-stu-id="b6b34-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="b6b34-115">(2) **host/fxr/\<fxr 版本>** 包含主機所使用的架構解析邏輯。</span><span class="sxs-lookup"><span data-stu-id="b6b34-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="b6b34-116">主機會使用已安裝的最新 hostfxr。</span><span class="sxs-lookup"><span data-stu-id="b6b34-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="b6b34-117">hostfxr 負責在執行 .NET Core 應用程式時選取適當的執行階段。</span><span class="sxs-lookup"><span data-stu-id="b6b34-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET Core application.</span></span> <span data-ttu-id="b6b34-118">例如，針對 .NET Core 2.0.0 建置的應用程式會在可用時使用 2.0.5 執行階段。</span><span class="sxs-lookup"><span data-stu-id="b6b34-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="b6b34-119">同樣地，hostfxr 會在開發期間選取適當的 SDK。</span><span class="sxs-lookup"><span data-stu-id="b6b34-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="b6b34-120">(3) **sdk/\< 版本>** SDK (也稱為「工具」) 是一組受控工具，用於撰寫和建置 .NET Core 程式庫和應用程式。</span><span class="sxs-lookup"><span data-stu-id="b6b34-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET Core libraries and applications.</span></span> <span data-ttu-id="b6b34-121">SDK 包含 .NET Core 命令列介面 (CLI)、受控語言編譯器、MSBuild 以及相關聯的建置工作和目標、NuGet、新專案範本等。</span><span class="sxs-lookup"><span data-stu-id="b6b34-121">The SDK includes the .NET Core Command-line interface (CLI), the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="b6b34-122">(4) **sdk/NuGetFallbackFolder** 包含 SDK 在還原作業期間使用的 NuGet 套件快取，例如在執行 `dotnet restore` 或 `dotnet build /t:Restore` 時。</span><span class="sxs-lookup"><span data-stu-id="b6b34-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="b6b34-123">此資料夾只會在 .NET Core 3.0 之前使用。</span><span class="sxs-lookup"><span data-stu-id="b6b34-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="b6b34-124">它無法從來源建立，因為它包含來自的`nuget.org`預建二進位資產。</span><span class="sxs-lookup"><span data-stu-id="b6b34-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="b6b34-125">**共用**資料夾包含架構。</span><span class="sxs-lookup"><span data-stu-id="b6b34-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="b6b34-126">共用架構在集中位置提供一組程式庫，以供不同的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="b6b34-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="b6b34-127">(5) **shared/Microsoft.NETCore.App/\<執行階段版本>** 此架構包含 .NET Core 執行階段和支援受控程式庫。</span><span class="sxs-lookup"><span data-stu-id="b6b34-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET Core runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="b6b34-128">（6） **shared/AspNetCore。 {App、All}/\<aspnetcore 版本 >** 包含 ASP.NET Core 程式庫。</span><span class="sxs-lookup"><span data-stu-id="b6b34-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="b6b34-129">在 .NET Core 專案期間，開發並支援 `Microsoft.AspNetCore.App` 下的程式庫。</span><span class="sxs-lookup"><span data-stu-id="b6b34-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET Core project.</span></span> <span data-ttu-id="b6b34-130">在 `Microsoft.AspNetCore.All` 下的程式庫是超集，其中也包含第三方程式庫。</span><span class="sxs-lookup"><span data-stu-id="b6b34-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="b6b34-131">（7）**共用/桌上型 app/\<傳統型應用程式版本 >** 包含 Windows 桌面程式庫。</span><span class="sxs-lookup"><span data-stu-id="b6b34-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="b6b34-132">這不包含在非 Windows 平臺上。</span><span class="sxs-lookup"><span data-stu-id="b6b34-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="b6b34-133">(8) **LICENSE.txt、ThirdPartyNotices.txt** 分別是在 .NET Core 中使用的 .NET Core 授權和第三方程式庫授權。</span><span class="sxs-lookup"><span data-stu-id="b6b34-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET Core license and licenses of third-party libraries used in .NET Core, respectively.</span></span>

- <span data-ttu-id="b6b34-134">(9、10) **dotnet.1.gz，dotnet** `dotnet.1.gz` 是 dotnet 手冊頁面。</span><span class="sxs-lookup"><span data-stu-id="b6b34-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="b6b34-135">`dotnet` 是 dotnet host(1) 的符號連結。</span><span class="sxs-lookup"><span data-stu-id="b6b34-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="b6b34-136">這些檔案會安裝在已知位置，以進行系統整合。</span><span class="sxs-lookup"><span data-stu-id="b6b34-136">These files are installed at well known locations for system integration.</span></span>

- <span data-ttu-id="b6b34-137">（11，12） **NETCore**會分別描述 .net Core `x.y`版本的 API 和 ASP.NET Core 的應用程式開發介面（AspNetCore）。</span><span class="sxs-lookup"><span data-stu-id="b6b34-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET Core and ASP.NET Core respectively.</span></span> <span data-ttu-id="b6b34-138">這些套件會在針對那些目標版本進行編譯時使用。</span><span class="sxs-lookup"><span data-stu-id="b6b34-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="b6b34-139">（13） **NETCore\< 。rid >** 包含適用于平臺`rid`的原生二進位檔。</span><span class="sxs-lookup"><span data-stu-id="b6b34-139">(13) **Microsoft.NETCore.App.Host.\<rid>** contains a native binary for platform `rid`.</span></span> <span data-ttu-id="b6b34-140">將 .NET Core 應用程式編譯成該平臺的原生二進位檔時，此二進位檔是範本。</span><span class="sxs-lookup"><span data-stu-id="b6b34-140">This binary is a template when compiling a .NET Core application into a native binary for that platform.</span></span>

- <span data-ttu-id="b6b34-141">（14） **WindowsDesktop**說明 Windows 桌面應用程式`x.y`版本的 API。</span><span class="sxs-lookup"><span data-stu-id="b6b34-141">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="b6b34-142">針對該目標編譯時，會使用這些檔案。</span><span class="sxs-lookup"><span data-stu-id="b6b34-142">These files are used when compiling for that target.</span></span> <span data-ttu-id="b6b34-143">這不是在非 Windows 平臺上提供。</span><span class="sxs-lookup"><span data-stu-id="b6b34-143">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="b6b34-144">（15） **NETStandard**描述 NETStandard `x.y` API。</span><span class="sxs-lookup"><span data-stu-id="b6b34-144">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="b6b34-145">針對該目標編譯時，會使用這些檔案。</span><span class="sxs-lookup"><span data-stu-id="b6b34-145">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="b6b34-146">（16） **/etc/dotnet/install_location**是一個檔案，其中包含包含`dotnet`主機二進位檔之資料夾的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b6b34-146">(16) **/etc/dotnet/install_location** is a file that contains the full path to the folder that contains the `dotnet` host binary.</span></span> <span data-ttu-id="b6b34-147">路徑可能以分行符號結束。</span><span class="sxs-lookup"><span data-stu-id="b6b34-147">The path may be terminated with a newline.</span></span> <span data-ttu-id="b6b34-148">當根目錄為`/usr/share/dotnet`時，不需要新增此檔案。</span><span class="sxs-lookup"><span data-stu-id="b6b34-148">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="b6b34-149">（17）**範本**包含 SDK 所使用的範本。</span><span class="sxs-lookup"><span data-stu-id="b6b34-149">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="b6b34-150">例如， `dotnet new`在這裡尋找專案範本。</span><span class="sxs-lookup"><span data-stu-id="b6b34-150">For example, `dotnet new` finds project templates here.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="b6b34-151">建議的套件</span><span class="sxs-lookup"><span data-stu-id="b6b34-151">Recommended packages</span></span>

<span data-ttu-id="b6b34-152">.NET Core 版本設定是以執行階段元件 `[major].[minor]` 版本號碼為基礎。</span><span class="sxs-lookup"><span data-stu-id="b6b34-152">.NET Core versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="b6b34-153">SDK 版本使用相同的 `[major].[minor]`，且具有獨立的 `[patch]`，其結合 SDK 的功能及修補程式語意。</span><span class="sxs-lookup"><span data-stu-id="b6b34-153">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="b6b34-154">例如：SDK 2.2.302 版是 SDK 第三個功能版本的第二個修補程式版本，其支援 2.2 執行階段。</span><span class="sxs-lookup"><span data-stu-id="b6b34-154">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="b6b34-155">如需版本設定運作方式的詳細資訊，請參閱 [.NET Core 版本設定概觀](../versions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b6b34-155">For more information about how versioning works, see [.NET Core versioning overview](../versions/index.md).</span></span>

<span data-ttu-id="b6b34-156">部分套件的名稱包含版本號碼部分。</span><span class="sxs-lookup"><span data-stu-id="b6b34-156">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="b6b34-157">這可讓您安裝特定版本。</span><span class="sxs-lookup"><span data-stu-id="b6b34-157">This allows you to install a specific version.</span></span>
<span data-ttu-id="b6b34-158">其餘的版本不包含在版本名稱中。</span><span class="sxs-lookup"><span data-stu-id="b6b34-158">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="b6b34-159">這可讓 OS 套件管理員更新套件 (例如自動安裝安全性修正程式)。</span><span class="sxs-lookup"><span data-stu-id="b6b34-159">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="b6b34-160">支援的套件管理員特定於 Linux。</span><span class="sxs-lookup"><span data-stu-id="b6b34-160">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="b6b34-161">下列列出建議的套件：</span><span class="sxs-lookup"><span data-stu-id="b6b34-161">The following lists the recommended packages:</span></span>

- <span data-ttu-id="b6b34-162">`dotnet-sdk-[major].[minor]`-安裝適用于特定執行時間的最新 sdk</span><span class="sxs-lookup"><span data-stu-id="b6b34-162">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="b6b34-163">**版本：** \<執行階段版本 ></span><span class="sxs-lookup"><span data-stu-id="b6b34-163">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b6b34-164">**範例：** dotnet-sdk-2。1</span><span class="sxs-lookup"><span data-stu-id="b6b34-164">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="b6b34-165">**包含**(3),(4)</span><span class="sxs-lookup"><span data-stu-id="b6b34-165">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="b6b34-166">相依性 **：** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`,`dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="b6b34-166">**Dependencies:** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="b6b34-167">`aspnetcore-runtime-[major].[minor]`-安裝特定的 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="b6b34-167">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="b6b34-168">**版本：** \<aspnetcore 執行階段版本 ></span><span class="sxs-lookup"><span data-stu-id="b6b34-168">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="b6b34-169">**範例：** aspnetcore-runtime-2。1</span><span class="sxs-lookup"><span data-stu-id="b6b34-169">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="b6b34-170">**包含**(6)</span><span class="sxs-lookup"><span data-stu-id="b6b34-170">**Contains:** (6)</span></span>
  - <span data-ttu-id="b6b34-171">相依性 **：** `dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="b6b34-171">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="b6b34-172">`dotnet-runtime-deps-[major].[minor]` _（選擇性）_ -安裝執行獨立應用程式的相依性</span><span class="sxs-lookup"><span data-stu-id="b6b34-172">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="b6b34-173">**版本：** \<執行階段版本 ></span><span class="sxs-lookup"><span data-stu-id="b6b34-173">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b6b34-174">**範例：** dotnet-runtime-.deps.json-2。1</span><span class="sxs-lookup"><span data-stu-id="b6b34-174">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="b6b34-175">相依性 **：** _散發版本特定_相依性</span><span class="sxs-lookup"><span data-stu-id="b6b34-175">**Dependencies:** _distro specific dependencies_</span></span>

- <span data-ttu-id="b6b34-176">`dotnet-runtime-[major].[minor]`-安裝特定執行時間</span><span class="sxs-lookup"><span data-stu-id="b6b34-176">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="b6b34-177">**版本：** \<執行階段版本 ></span><span class="sxs-lookup"><span data-stu-id="b6b34-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b6b34-178">**範例：** dotnet-runtime-2。1</span><span class="sxs-lookup"><span data-stu-id="b6b34-178">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="b6b34-179">**包含**(5)</span><span class="sxs-lookup"><span data-stu-id="b6b34-179">**Contains:** (5)</span></span>
  - <span data-ttu-id="b6b34-180">相依性 **：** `dotnet-hostfxr:<runtime version>+`,`dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="b6b34-180">**Dependencies:** `dotnet-hostfxr:<runtime version>+`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="b6b34-181">`dotnet-hostfxr`-dependency</span><span class="sxs-lookup"><span data-stu-id="b6b34-181">`dotnet-hostfxr` - dependency</span></span>
  - <span data-ttu-id="b6b34-182">**版本：** \<執行階段版本 ></span><span class="sxs-lookup"><span data-stu-id="b6b34-182">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b6b34-183">**範例：** dotnet-用 hostfxr</span><span class="sxs-lookup"><span data-stu-id="b6b34-183">**Example:** dotnet-hostfxr</span></span>
  - <span data-ttu-id="b6b34-184">**包含**(2)</span><span class="sxs-lookup"><span data-stu-id="b6b34-184">**Contains:** (2)</span></span>
  - <span data-ttu-id="b6b34-185">相依性 **：** `host:<runtime version>+`</span><span class="sxs-lookup"><span data-stu-id="b6b34-185">**Dependencies:** `host:<runtime version>+`</span></span>

- <span data-ttu-id="b6b34-186">`dotnet-host`-dependency</span><span class="sxs-lookup"><span data-stu-id="b6b34-186">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="b6b34-187">**版本：** \<執行階段版本 ></span><span class="sxs-lookup"><span data-stu-id="b6b34-187">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b6b34-188">**範例：** dotnet-host</span><span class="sxs-lookup"><span data-stu-id="b6b34-188">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="b6b34-189">**包含**（1）、（8）、（9）、（10）、（16）</span><span class="sxs-lookup"><span data-stu-id="b6b34-189">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="b6b34-190">`dotnet-apphost-pack-[major].[minor]`-dependency</span><span class="sxs-lookup"><span data-stu-id="b6b34-190">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="b6b34-191">**版本：** \<執行階段版本 ></span><span class="sxs-lookup"><span data-stu-id="b6b34-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b6b34-192">**包含**十三</span><span class="sxs-lookup"><span data-stu-id="b6b34-192">**Contains:** (13)</span></span>

- <span data-ttu-id="b6b34-193">`dotnet-targeting-pack-[major].[minor]`-允許以非最新的執行時間為目標</span><span class="sxs-lookup"><span data-stu-id="b6b34-193">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="b6b34-194">**版本：** \<執行階段版本 ></span><span class="sxs-lookup"><span data-stu-id="b6b34-194">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="b6b34-195">**包含**12</span><span class="sxs-lookup"><span data-stu-id="b6b34-195">**Contains:** (12)</span></span>

- <span data-ttu-id="b6b34-196">`aspnetcore-targeting-pack-[major].[minor]`-允許以非最新的執行時間為目標</span><span class="sxs-lookup"><span data-stu-id="b6b34-196">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="b6b34-197">**版本：** \<aspnetcore 執行階段版本 ></span><span class="sxs-lookup"><span data-stu-id="b6b34-197">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="b6b34-198">**包含**英寸</span><span class="sxs-lookup"><span data-stu-id="b6b34-198">**Contains:** (11)</span></span>

- <span data-ttu-id="b6b34-199">`netstandard-targeting-pack-[major].[minor]`-允許以 netstandard 版本為目標</span><span class="sxs-lookup"><span data-stu-id="b6b34-199">`netstandard-targeting-pack-[major].[minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="b6b34-200">**版本：** \<sdk 版本 ></span><span class="sxs-lookup"><span data-stu-id="b6b34-200">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="b6b34-201">**包含**次</span><span class="sxs-lookup"><span data-stu-id="b6b34-201">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="b6b34-202">**版本：** \<sdk 版本 ></span><span class="sxs-lookup"><span data-stu-id="b6b34-202">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="b6b34-203">**包含**次</span><span class="sxs-lookup"><span data-stu-id="b6b34-203">**Contains:** (15)</span></span>

<span data-ttu-id="b6b34-204">需要瞭解散發版本特有的相依性。 `dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="b6b34-204">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro specific dependencies_.</span></span> <span data-ttu-id="b6b34-205">由於散發版本組建系統可能能夠自動衍生此專案，因此封裝是選擇性的，在此情況下，這些相依性會直接新增`dotnet-runtime-[major].[minor]`至封裝中。</span><span class="sxs-lookup"><span data-stu-id="b6b34-205">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="b6b34-206">當套件內容在已建立版本的資料夾下時， `[major].[minor]`套件名稱會符合已建立版本的資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="b6b34-206">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="b6b34-207">除了以外`netstandard-targeting-pack-[major].[minor]`的所有套件，這也符合 .net Core 版本。</span><span class="sxs-lookup"><span data-stu-id="b6b34-207">For all packages, except the `netstandard-targeting-pack-[major].[minor]`, this also matches with the .NET Core version.</span></span>

<span data-ttu-id="b6b34-208">封裝之間的相依性應使用_等於或大於_版本需求。</span><span class="sxs-lookup"><span data-stu-id="b6b34-208">Dependencies between packages should use a _equal or greater than_ version requirement.</span></span> <span data-ttu-id="b6b34-209">例如， `dotnet-sdk-2.2:2.2.401`需要`aspnetcore-runtime-2.2 >= 2.2.6`。</span><span class="sxs-lookup"><span data-stu-id="b6b34-209">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="b6b34-210">如此一來，使用者就可以透過根封裝（例如`dnf update dotnet-sdk-2.2`）升級其安裝。</span><span class="sxs-lookup"><span data-stu-id="b6b34-210">This makes it possible for the user to upgrade their installation via a root package (e.g. `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="b6b34-211">大部分的發佈都需要從來源建置的所有成品。</span><span class="sxs-lookup"><span data-stu-id="b6b34-211">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="b6b34-212">這會對套件造成某個影響：</span><span class="sxs-lookup"><span data-stu-id="b6b34-212">This has some impact on the packages:</span></span>

- <span data-ttu-id="b6b34-213">`shared/Microsoft.AspNetCore.All` 下的第三方程式庫無法從來源輕鬆建置。</span><span class="sxs-lookup"><span data-stu-id="b6b34-213">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="b6b34-214">因此會從 `aspnetcore-runtime` 套件省略該資料夾。</span><span class="sxs-lookup"><span data-stu-id="b6b34-214">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="b6b34-215">使用 `nuget.org` 中的二進位成品填入 `NuGetFallbackFolder`。</span><span class="sxs-lookup"><span data-stu-id="b6b34-215">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="b6b34-216">它應該維持空白。</span><span class="sxs-lookup"><span data-stu-id="b6b34-216">It should remain empty.</span></span>

<span data-ttu-id="b6b34-217">多個 `dotnet-sdk` 套件可能會提供相同的 `NuGetFallbackFolder` 檔案。</span><span class="sxs-lookup"><span data-stu-id="b6b34-217">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="b6b34-218">為了避免套件管理員問題，這些檔案都應該相同 (總和檢查碼、修改日期等)。</span><span class="sxs-lookup"><span data-stu-id="b6b34-218">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="b6b34-219">建置套件</span><span class="sxs-lookup"><span data-stu-id="b6b34-219">Building packages</span></span>

<span data-ttu-id="b6b34-220">[dotnet/source-build](https://github.com/dotnet/source-build) \(英文\) 存放庫提供有關如何建置 .NET Core SDK 與其所有元件之來源 tarball 的指示。</span><span class="sxs-lookup"><span data-stu-id="b6b34-220">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET Core SDK and all its components.</span></span> <span data-ttu-id="b6b34-221">source-build 存放庫的輸出會比對本文第一節中所述的配置。</span><span class="sxs-lookup"><span data-stu-id="b6b34-221">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
