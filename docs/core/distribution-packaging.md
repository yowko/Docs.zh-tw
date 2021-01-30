---
title: .NET 散發封裝
description: 瞭解如何封裝、命名和版本 .NET 以進行散發。
author: tmds
ms.date: 10/09/2019
ms.openlocfilehash: 93d040064eb739b3bd045fdb16b356732353ddc8
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216300"
---
# <a name="net-distribution-packaging"></a><span data-ttu-id="03ee0-103">.NET 散發封裝</span><span class="sxs-lookup"><span data-stu-id="03ee0-103">.NET distribution packaging</span></span>

<span data-ttu-id="03ee0-104">由於 .NET 5 (和 .NET Core) 和更新版本會在更多平臺上提供使用，因此瞭解如何封裝、命名和使用它的應用程式和程式庫，是很有用的。</span><span class="sxs-lookup"><span data-stu-id="03ee0-104">As .NET 5 (and .NET Core) and later versions become available on more and more platforms, it's useful to learn how to package, name, and version apps and libraries that use it.</span></span> <span data-ttu-id="03ee0-105">如此一來，套件維護人員可以協助確保一致的體驗，無論使用者選擇在何處執行 .NET。</span><span class="sxs-lookup"><span data-stu-id="03ee0-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="03ee0-106">本文適用於符合下列項目的使用者：</span><span class="sxs-lookup"><span data-stu-id="03ee0-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="03ee0-107">正在嘗試從來源建立 .NET。</span><span class="sxs-lookup"><span data-stu-id="03ee0-107">Attempting to build .NET from source.</span></span>
- <span data-ttu-id="03ee0-108">想要變更可能會影響所產生之配置或封裝的 .NET CLI。</span><span class="sxs-lookup"><span data-stu-id="03ee0-108">Wanting to make changes to the .NET CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="03ee0-109">磁碟配置</span><span class="sxs-lookup"><span data-stu-id="03ee0-109">Disk layout</span></span>

<span data-ttu-id="03ee0-110">安裝時，.NET 會包含幾個配置檔案系統中的元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="03ee0-110">When installed, .NET consists of several components that are laid out as follows in the file system:</span></span>

```
{dotnet_root}                                     (*)
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host                                          (*)
│   └── fxr                                       (*)
│       └── <fxr version>        (2)
├── sdk                                           (*)
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)              (*)
├── packs                                         (*)
│   ├── Microsoft.AspNetCore.App.Ref              (*)
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref                 (*)
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>          (*)
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref          (*)
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref                   (*)
│       └── <netstandard version>        (15)
├── shared                                        (*)
│   ├── Microsoft.NETCore.App                     (*)
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App                  (*)
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All                  (*)
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App              (*)
│       └── <desktop app version> (7)
└── templates                                     (*)
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="03ee0-111">(1) **dotnet** 主機 (也稱為"muxer") 有兩個不同的角色：啟用執行階段以啟動應用程式，以及啟用 SDK 將命令分派給它。</span><span class="sxs-lookup"><span data-stu-id="03ee0-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="03ee0-112">主機是原生可執行檔 (`dotnet.exe`)。</span><span class="sxs-lookup"><span data-stu-id="03ee0-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="03ee0-113">雖然是單一主機，但大部分其他元件都會位於已建立版本的目錄中 (2、3、5、6)。</span><span class="sxs-lookup"><span data-stu-id="03ee0-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="03ee0-114">這表示多個版本可能會存在於系統上，因為為並排安裝。</span><span class="sxs-lookup"><span data-stu-id="03ee0-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="03ee0-115"> (2) **host/fxr/ \<fxr version>** 包含主機所使用的架構解析邏輯。</span><span class="sxs-lookup"><span data-stu-id="03ee0-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="03ee0-116">主機會使用已安裝的最新 hostfxr。</span><span class="sxs-lookup"><span data-stu-id="03ee0-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="03ee0-117">Hostfxr 會負責在執行 .NET 應用程式時選取適當的執行時間。</span><span class="sxs-lookup"><span data-stu-id="03ee0-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET application.</span></span> <span data-ttu-id="03ee0-118">例如，針對 .NET Core 2.0.0 建置的應用程式會在可用時使用 2.0.5 執行階段。</span><span class="sxs-lookup"><span data-stu-id="03ee0-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="03ee0-119">同樣地，hostfxr 會在開發期間選取適當的 SDK。</span><span class="sxs-lookup"><span data-stu-id="03ee0-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="03ee0-120"> (3) **sdk/ \<sdk version>** sdk (也稱為「工具」 ) 是一組受管理的工具，可用來撰寫和建立 .net 程式庫和應用程式。</span><span class="sxs-lookup"><span data-stu-id="03ee0-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET libraries and applications.</span></span> <span data-ttu-id="03ee0-121">SDK 包含 .NET CLI、managed 語言編譯器、MSBuild，以及相關聯的組建工作與目標、NuGet、新專案範本等等。</span><span class="sxs-lookup"><span data-stu-id="03ee0-121">The SDK includes the .NET CLI, the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="03ee0-122">(4) **sdk/NuGetFallbackFolder** 包含 SDK 在還原作業期間使用的 NuGet 套件快取，例如在執行 `dotnet restore` 或 `dotnet build` 時。</span><span class="sxs-lookup"><span data-stu-id="03ee0-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build`.</span></span> <span data-ttu-id="03ee0-123">此資料夾只會在 .NET Core 3.0 之前使用。</span><span class="sxs-lookup"><span data-stu-id="03ee0-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="03ee0-124">它無法從來源建立，因為它包含預建的二進位資產 `nuget.org` 。</span><span class="sxs-lookup"><span data-stu-id="03ee0-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="03ee0-125">**共用** 資料夾包含架構。</span><span class="sxs-lookup"><span data-stu-id="03ee0-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="03ee0-126">共用架構在集中位置提供一組程式庫，以供不同的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="03ee0-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="03ee0-127"> (5) **shared/NETCore. App/ \<runtime version>** 此架構包含 .net 執行時間和支援的 managed 程式庫。</span><span class="sxs-lookup"><span data-stu-id="03ee0-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="03ee0-128"> (6) **shared/AspNetCore. {App、All}/ \<aspnetcore version>** 包含 ASP.NET Core 程式庫。</span><span class="sxs-lookup"><span data-stu-id="03ee0-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="03ee0-129">下的程式庫 `Microsoft.AspNetCore.App` 是在 .net 專案中開發和支援的。</span><span class="sxs-lookup"><span data-stu-id="03ee0-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET project.</span></span> <span data-ttu-id="03ee0-130">在 `Microsoft.AspNetCore.All` 下的程式庫是超集，其中也包含第三方程式庫。</span><span class="sxs-lookup"><span data-stu-id="03ee0-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="03ee0-131"> (7) **共用/Microsoft. App/ \<desktop app version>** 包含 Windows 桌面程式庫。</span><span class="sxs-lookup"><span data-stu-id="03ee0-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="03ee0-132">這不包含在非 Windows 平臺上。</span><span class="sxs-lookup"><span data-stu-id="03ee0-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="03ee0-133"> (8) **LICENSE.txt，ThirdPartyNotices.txt** 分別是 .net 中使用的 .net 授權和協力廠商程式庫的授權。</span><span class="sxs-lookup"><span data-stu-id="03ee0-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET license and licenses of third-party libraries used in .NET, respectively.</span></span>

- <span data-ttu-id="03ee0-134">(9、10) **dotnet.1.gz，dotnet** `dotnet.1.gz` 是 dotnet 手冊頁面。</span><span class="sxs-lookup"><span data-stu-id="03ee0-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="03ee0-135">`dotnet` 是 dotnet host(1) 的符號連結。</span><span class="sxs-lookup"><span data-stu-id="03ee0-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="03ee0-136">這些檔案會安裝在已知的位置以進行系統整合。</span><span class="sxs-lookup"><span data-stu-id="03ee0-136">These files are installed at well-known locations for system integration.</span></span>

- <span data-ttu-id="03ee0-137"> (11，12) **NETCore。 ref** 分別描述 .net 版本的 API 和 ASP.NET Core 的應用程式開發介面 `x.y` 。</span><span class="sxs-lookup"><span data-stu-id="03ee0-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET and ASP.NET Core respectively.</span></span> <span data-ttu-id="03ee0-138">針對這些目標版本進行編譯時，會使用這些套件。</span><span class="sxs-lookup"><span data-stu-id="03ee0-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="03ee0-139"> (13) **NETCore \<rid>** 。</span><span class="sxs-lookup"><span data-stu-id="03ee0-139">(13) **Microsoft.NETCore.App.Host.\<rid>**</span></span> <span data-ttu-id="03ee0-140">包含平臺的原生二進位檔 `rid` 。</span><span class="sxs-lookup"><span data-stu-id="03ee0-140">contains a native binary for platform `rid`.</span></span> <span data-ttu-id="03ee0-141">將 .NET 應用程式編譯為該平臺的原生二進位檔時，此二進位檔是範本。</span><span class="sxs-lookup"><span data-stu-id="03ee0-141">This binary is a template when compiling a .NET application into a native binary for that platform.</span></span>

- <span data-ttu-id="03ee0-142"> (14) **WindowsDesktop** 描述 `x.y` Windows 傳統型應用程式版本的 API。</span><span class="sxs-lookup"><span data-stu-id="03ee0-142">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="03ee0-143">針對該目標編譯時，會使用這些檔案。</span><span class="sxs-lookup"><span data-stu-id="03ee0-143">These files are used when compiling for that target.</span></span> <span data-ttu-id="03ee0-144">非 Windows 平臺上不會提供此資訊。</span><span class="sxs-lookup"><span data-stu-id="03ee0-144">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="03ee0-145"> (15) **NETStandard** 描述 NETStandard `x.y` API。</span><span class="sxs-lookup"><span data-stu-id="03ee0-145">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="03ee0-146">針對該目標編譯時，會使用這些檔案。</span><span class="sxs-lookup"><span data-stu-id="03ee0-146">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="03ee0-147"> (16) **/etc/dotnet/install_location** 是包含完整路徑的檔案 `{dotnet_root}` 。</span><span class="sxs-lookup"><span data-stu-id="03ee0-147">(16) **/etc/dotnet/install_location** is a file that contains the full path for `{dotnet_root}`.</span></span> <span data-ttu-id="03ee0-148">路徑結尾可以是分行符號。</span><span class="sxs-lookup"><span data-stu-id="03ee0-148">The path may end with a newline.</span></span> <span data-ttu-id="03ee0-149">當根目錄為時，並不需要加入這個檔案 `/usr/share/dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="03ee0-149">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="03ee0-150"> (17) **範本** 包含 SDK 所使用的範本。</span><span class="sxs-lookup"><span data-stu-id="03ee0-150">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="03ee0-151">例如， `dotnet new` 在這裡尋找專案範本。</span><span class="sxs-lookup"><span data-stu-id="03ee0-151">For example, `dotnet new` finds project templates here.</span></span>

<span data-ttu-id="03ee0-152">標記為的資料夾 `(*)` 會由多個套件使用。</span><span class="sxs-lookup"><span data-stu-id="03ee0-152">The folders marked with `(*)` are used by multiple packages.</span></span> <span data-ttu-id="03ee0-153">某些封裝格式 (例如， `rpm`) 需要這類資料夾的特殊處理。</span><span class="sxs-lookup"><span data-stu-id="03ee0-153">Some package formats (for example, `rpm`) require special handling of such folders.</span></span> <span data-ttu-id="03ee0-154">封裝維護程式必須負責處理。</span><span class="sxs-lookup"><span data-stu-id="03ee0-154">The package maintainer must take care of this.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="03ee0-155">建議的套件</span><span class="sxs-lookup"><span data-stu-id="03ee0-155">Recommended packages</span></span>

<span data-ttu-id="03ee0-156">.NET 版本控制是以執行時間元件的 `[major].[minor]` 版本號碼為基礎。</span><span class="sxs-lookup"><span data-stu-id="03ee0-156">.NET versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="03ee0-157">SDK 版本使用相同的 `[major].[minor]`，且具有獨立的 `[patch]`，其結合 SDK 的功能及修補程式語意。</span><span class="sxs-lookup"><span data-stu-id="03ee0-157">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="03ee0-158">例如： SDK 版本2.2.302 版是支援2.2 執行時間之 SDK 第三項功能版本的第二個修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="03ee0-158">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="03ee0-159">如需版本控制運作方式的詳細資訊，請參閱 [.net 版本控制總覽](./versions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="03ee0-159">For more information about how versioning works, see [.NET versioning overview](./versions/index.md).</span></span>

<span data-ttu-id="03ee0-160">部分套件的名稱包含版本號碼部分。</span><span class="sxs-lookup"><span data-stu-id="03ee0-160">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="03ee0-161">這可讓您安裝特定版本。</span><span class="sxs-lookup"><span data-stu-id="03ee0-161">This allows you to install a specific version.</span></span>
<span data-ttu-id="03ee0-162">其餘的版本不包含在版本名稱中。</span><span class="sxs-lookup"><span data-stu-id="03ee0-162">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="03ee0-163">這可讓 OS 套件管理員更新套件 (例如自動安裝安全性修正程式)。</span><span class="sxs-lookup"><span data-stu-id="03ee0-163">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="03ee0-164">支援的套件管理員特定於 Linux。</span><span class="sxs-lookup"><span data-stu-id="03ee0-164">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="03ee0-165">以下列出建議的封裝：</span><span class="sxs-lookup"><span data-stu-id="03ee0-165">The following lists the recommended packages:</span></span>

- <span data-ttu-id="03ee0-166">`dotnet-sdk-[major].[minor]` -安裝適用于特定執行時間的最新 sdk</span><span class="sxs-lookup"><span data-stu-id="03ee0-166">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="03ee0-167">**版本：**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="03ee0-167">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="03ee0-168">**範例：** dotnet-sdk-2。1</span><span class="sxs-lookup"><span data-stu-id="03ee0-168">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="03ee0-169">**包含：** (3) 、 (4) </span><span class="sxs-lookup"><span data-stu-id="03ee0-169">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="03ee0-170">相依性 **：** `dotnet-runtime-[major].[minor]` 、 `aspnetcore-runtime-[major].[minor]` 、 `dotnet-targeting-pack-[major].[minor]` 、 `aspnetcore-targeting-pack-[major].[minor]` 、、 `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` `dotnet-apphost-pack-[major].[minor]` 、`dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="03ee0-170">**Dependencies:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="03ee0-171">`aspnetcore-runtime-[major].[minor]` -安裝特定的 ASP.NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="03ee0-171">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="03ee0-172">**版本：**\<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="03ee0-172">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="03ee0-173">**範例：** aspnetcore-runtime-2。1</span><span class="sxs-lookup"><span data-stu-id="03ee0-173">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="03ee0-174">**包含：** (6) </span><span class="sxs-lookup"><span data-stu-id="03ee0-174">**Contains:** (6)</span></span>
  - <span data-ttu-id="03ee0-175">相依性 **：**`dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="03ee0-175">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="03ee0-176">`dotnet-runtime-deps-[major].[minor]`_(選擇性)_ -安裝執行獨立應用程式的相依性</span><span class="sxs-lookup"><span data-stu-id="03ee0-176">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="03ee0-177">**版本：**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="03ee0-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="03ee0-178">**範例：** dotnet-runtime-d-2。1</span><span class="sxs-lookup"><span data-stu-id="03ee0-178">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="03ee0-179">相依性 **：** _散發特定_ 相依性</span><span class="sxs-lookup"><span data-stu-id="03ee0-179">**Dependencies:** _distribution-specific dependencies_</span></span>

- <span data-ttu-id="03ee0-180">`dotnet-runtime-[major].[minor]` -安裝特定執行時間</span><span class="sxs-lookup"><span data-stu-id="03ee0-180">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="03ee0-181">**版本：**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="03ee0-181">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="03ee0-182">**範例：** dotnet-runtime-2。1</span><span class="sxs-lookup"><span data-stu-id="03ee0-182">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="03ee0-183">**包含：** (5) </span><span class="sxs-lookup"><span data-stu-id="03ee0-183">**Contains:** (5)</span></span>
  - <span data-ttu-id="03ee0-184">相依性 **：** `dotnet-hostfxr-[major].[minor]` 、`dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="03ee0-184">**Dependencies:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="03ee0-185">`dotnet-hostfxr-[major].[minor]` -相依性</span><span class="sxs-lookup"><span data-stu-id="03ee0-185">`dotnet-hostfxr-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="03ee0-186">**版本：**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="03ee0-186">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="03ee0-187">**範例：** dotnet-hostfxr-3。0</span><span class="sxs-lookup"><span data-stu-id="03ee0-187">**Example:** dotnet-hostfxr-3.0</span></span>
  - <span data-ttu-id="03ee0-188">**包含：** (2) </span><span class="sxs-lookup"><span data-stu-id="03ee0-188">**Contains:** (2)</span></span>
  - <span data-ttu-id="03ee0-189">相依性 **：**`dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="03ee0-189">**Dependencies:** `dotnet-host`</span></span>

- <span data-ttu-id="03ee0-190">`dotnet-host` -相依性</span><span class="sxs-lookup"><span data-stu-id="03ee0-190">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="03ee0-191">**版本：**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="03ee0-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="03ee0-192">**範例：** dotnet-主機</span><span class="sxs-lookup"><span data-stu-id="03ee0-192">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="03ee0-193">**包含：** (1) 、 (8) 、 (9) 、 (10) 、 (16) </span><span class="sxs-lookup"><span data-stu-id="03ee0-193">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="03ee0-194">`dotnet-apphost-pack-[major].[minor]` -相依性</span><span class="sxs-lookup"><span data-stu-id="03ee0-194">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="03ee0-195">**版本：**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="03ee0-195">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="03ee0-196">**包含：** (13) </span><span class="sxs-lookup"><span data-stu-id="03ee0-196">**Contains:** (13)</span></span>

- <span data-ttu-id="03ee0-197">`dotnet-targeting-pack-[major].[minor]` -允許以非最新執行時間為目標</span><span class="sxs-lookup"><span data-stu-id="03ee0-197">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="03ee0-198">**版本：**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="03ee0-198">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="03ee0-199">**包含：** (12) </span><span class="sxs-lookup"><span data-stu-id="03ee0-199">**Contains:** (12)</span></span>

- <span data-ttu-id="03ee0-200">`aspnetcore-targeting-pack-[major].[minor]` -允許以非最新執行時間為目標</span><span class="sxs-lookup"><span data-stu-id="03ee0-200">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="03ee0-201">**版本：**\<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="03ee0-201">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="03ee0-202">**包含：** (11) </span><span class="sxs-lookup"><span data-stu-id="03ee0-202">**Contains:** (11)</span></span>

- <span data-ttu-id="03ee0-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` -允許以 netstandard 版本為目標</span><span class="sxs-lookup"><span data-stu-id="03ee0-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="03ee0-204">**版本：**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="03ee0-204">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="03ee0-205">**包含：** (15) </span><span class="sxs-lookup"><span data-stu-id="03ee0-205">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="03ee0-206">**版本：**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="03ee0-206">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="03ee0-207">**包含：** (15) </span><span class="sxs-lookup"><span data-stu-id="03ee0-207">**Contains:** (15)</span></span>

<span data-ttu-id="03ee0-208">`dotnet-runtime-deps-[major].[minor]`需要瞭解 _發行版本特有_ 的相依性。</span><span class="sxs-lookup"><span data-stu-id="03ee0-208">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro-specific dependencies_.</span></span> <span data-ttu-id="03ee0-209">因為發行版本組建系統可能會自動衍生此封裝，所以封裝是選擇性的，在這種情況下，這些相依性會直接加入 `dotnet-runtime-[major].[minor]` 封裝中。</span><span class="sxs-lookup"><span data-stu-id="03ee0-209">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="03ee0-210">當套件內容位於已建立版本的資料夾之下時，套件名稱會與已建立 `[major].[minor]` 版本的資料夾名稱相符。</span><span class="sxs-lookup"><span data-stu-id="03ee0-210">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="03ee0-211">除了以外的所有封裝之外 `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` ，這也會與 .net 版本相符。</span><span class="sxs-lookup"><span data-stu-id="03ee0-211">For all packages, except the `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, this also matches with the .NET version.</span></span>

<span data-ttu-id="03ee0-212">套件之間的相依性應使用 _等於或大於_ 版本需求。</span><span class="sxs-lookup"><span data-stu-id="03ee0-212">Dependencies between packages should use an _equal or greater than_ version requirement.</span></span> <span data-ttu-id="03ee0-213">例如， `dotnet-sdk-2.2:2.2.401` 需要 `aspnetcore-runtime-2.2 >= 2.2.6` 。</span><span class="sxs-lookup"><span data-stu-id="03ee0-213">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="03ee0-214">如此一來，使用者就可以透過根封裝升級其安裝 (例如 `dnf update dotnet-sdk-2.2`) 。</span><span class="sxs-lookup"><span data-stu-id="03ee0-214">This makes it possible for the user to upgrade their installation via a root package (for example, `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="03ee0-215">大部分的發佈都需要從來源建置的所有成品。</span><span class="sxs-lookup"><span data-stu-id="03ee0-215">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="03ee0-216">這會對套件造成某個影響：</span><span class="sxs-lookup"><span data-stu-id="03ee0-216">This has some impact on the packages:</span></span>

- <span data-ttu-id="03ee0-217">`shared/Microsoft.AspNetCore.All` 下的第三方程式庫無法從來源輕鬆建置。</span><span class="sxs-lookup"><span data-stu-id="03ee0-217">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="03ee0-218">因此會從 `aspnetcore-runtime` 套件省略該資料夾。</span><span class="sxs-lookup"><span data-stu-id="03ee0-218">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="03ee0-219">使用 `nuget.org` 中的二進位成品填入 `NuGetFallbackFolder`。</span><span class="sxs-lookup"><span data-stu-id="03ee0-219">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="03ee0-220">它應該維持空白。</span><span class="sxs-lookup"><span data-stu-id="03ee0-220">It should remain empty.</span></span>

<span data-ttu-id="03ee0-221">多個 `dotnet-sdk` 套件可能會提供相同的 `NuGetFallbackFolder` 檔案。</span><span class="sxs-lookup"><span data-stu-id="03ee0-221">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="03ee0-222">為了避免套件管理員問題，這些檔案都應該相同 (總和檢查碼、修改日期等)。</span><span class="sxs-lookup"><span data-stu-id="03ee0-222">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="03ee0-223">建置套件</span><span class="sxs-lookup"><span data-stu-id="03ee0-223">Building packages</span></span>

<span data-ttu-id="03ee0-224">[Dotnet/來源組建](https://github.com/dotnet/source-build)存放庫提供如何建立 .net SDK 的來源 tarball 及其所有元件的指示。</span><span class="sxs-lookup"><span data-stu-id="03ee0-224">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET SDK and all its components.</span></span> <span data-ttu-id="03ee0-225">source-build 存放庫的輸出會比對本文第一節中所述的配置。</span><span class="sxs-lookup"><span data-stu-id="03ee0-225">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
