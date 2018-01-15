---
title: ".NET Core 執行階段識別項 (RID) 目錄"
description: "了解執行階段識別碼 (RID) 以及 RID 在 .NET Core 中的使用方式。"
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 180aac7635746f9ede146c3e561deb9bba9a61ab
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="c0f97-103">.NET Core RID 類別目錄</span><span class="sxs-lookup"><span data-stu-id="c0f97-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="c0f97-104">RID 是*執行階段識別項*的縮寫。</span><span class="sxs-lookup"><span data-stu-id="c0f97-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="c0f97-105">RID 值是用來識別應用程式執行所在的目標平台。</span><span class="sxs-lookup"><span data-stu-id="c0f97-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="c0f97-106">.NET 套件會使用它們來代表 NuGet 套件中的平台特定資產。</span><span class="sxs-lookup"><span data-stu-id="c0f97-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="c0f97-107">下列值是 RID 的範例：`linux-x64`、`ubuntu.14.04-x64`、`win7-x64` 或 `osx.10.12-x64`。</span><span class="sxs-lookup"><span data-stu-id="c0f97-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="c0f97-108">針對具有原生相依性的套件，RID 也可指定能在哪些平台上還原套件。</span><span class="sxs-lookup"><span data-stu-id="c0f97-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="c0f97-109">RID 可在您專案檔的 `<RuntimeIdentifier>` 元素中設定。</span><span class="sxs-lookup"><span data-stu-id="c0f97-109">RIDs can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="c0f97-110">它們也可以透過以`--runtime`選項搭配下列 [.NET Core CLI 命令](./tools/index.md)來使用：</span><span class="sxs-lookup"><span data-stu-id="c0f97-110">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="c0f97-111">dotnet build</span><span class="sxs-lookup"><span data-stu-id="c0f97-111">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="c0f97-112">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="c0f97-112">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="c0f97-113">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="c0f97-113">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="c0f97-114">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="c0f97-114">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="c0f97-115">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="c0f97-115">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="c0f97-116">dotnet run</span><span class="sxs-lookup"><span data-stu-id="c0f97-116">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="c0f97-117">dotnet store</span><span class="sxs-lookup"><span data-stu-id="c0f97-117">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="c0f97-118">代表具體作業系統的 RID 通常遵循 `[os].[version]-[architecture]-[additional qualifiers]` 這個模式，其中：</span><span class="sxs-lookup"><span data-stu-id="c0f97-118">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="c0f97-119">`[os]` 是作業/平台系統 Moniker。</span><span class="sxs-lookup"><span data-stu-id="c0f97-119">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="c0f97-120">例如，`ubuntu`。</span><span class="sxs-lookup"><span data-stu-id="c0f97-120">For example, `ubuntu`.</span></span>

- <span data-ttu-id="c0f97-121">`[version]` 是作業系統版本，使用以點分隔 (`.`) 的版本號碼表示。</span><span class="sxs-lookup"><span data-stu-id="c0f97-121">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="c0f97-122">例如，`15.10`。</span><span class="sxs-lookup"><span data-stu-id="c0f97-122">For example, `15.10`.</span></span>

  - <span data-ttu-id="c0f97-123">版本**不應為**行銷版本，因為行銷版本通常代表作業系統的多個個別版本，且具有不同平台 API 介面區。</span><span class="sxs-lookup"><span data-stu-id="c0f97-123">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="c0f97-124">`[architecture]` 處理器架構。</span><span class="sxs-lookup"><span data-stu-id="c0f97-124">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="c0f97-125">例如：`x86`、`x64`、`arm` 或 `arm64`。</span><span class="sxs-lookup"><span data-stu-id="c0f97-125">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="c0f97-126">`[additional qualifiers]` 進一步區分不同平台。</span><span class="sxs-lookup"><span data-stu-id="c0f97-126">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="c0f97-127">例如：`aot` 或 `corert`。</span><span class="sxs-lookup"><span data-stu-id="c0f97-127">For example: `aot` or `corert`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="c0f97-128">RID 圖表</span><span class="sxs-lookup"><span data-stu-id="c0f97-128">RID graph</span></span>

<span data-ttu-id="c0f97-129">RID 圖表或執行階段後援圖形是與彼此相容的 RID 清單。</span><span class="sxs-lookup"><span data-stu-id="c0f97-129">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="c0f97-130">RID 是在 [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) 套件中定義。</span><span class="sxs-lookup"><span data-stu-id="c0f97-130">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="c0f97-131">您可以在 [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) 檔案 (位於 CoreFX 存放庫) 中看到支援的 RID 清單與 RID 圖形。</span><span class="sxs-lookup"><span data-stu-id="c0f97-131">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="c0f97-132">在此檔案中，您可以看到所有 RID (基底項目除外) 都包含 `"#import"` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c0f97-132">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="c0f97-133">這些陳述式指出相容的 RID。</span><span class="sxs-lookup"><span data-stu-id="c0f97-133">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="c0f97-134">當 NuGet 還原套件時，它會嘗試尋找與所指定執行階段完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="c0f97-134">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="c0f97-135">若找不到完全相符的項目，NuGet 會返回到圖形，直到它根據 RID 圖形找到最接近的相容系統。</span><span class="sxs-lookup"><span data-stu-id="c0f97-135">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="c0f97-136">下列範例是 `osx.10.12-x64` RID 的實際項目：</span><span class="sxs-lookup"><span data-stu-id="c0f97-136">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="c0f97-137">上述 RID 指定 `osx.10.12-x64` 匯入 `osx.10.11-x64`。</span><span class="sxs-lookup"><span data-stu-id="c0f97-137">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="c0f97-138">因此，當 NuGet 還原套件時，它會嘗試在套件中尋找與 `osx.10.12-x64` 完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="c0f97-138">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="c0f97-139">例如，若 NuGet 找不到特定執行階段，它可以還原指定 `osx.10.11-x64` 執行階段的套件。</span><span class="sxs-lookup"><span data-stu-id="c0f97-139">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="c0f97-140">下列範例顯示也在 *runtime.json* 檔案中定義的稍大 RID 圖形：</span><span class="sxs-lookup"><span data-stu-id="c0f97-140">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

<span data-ttu-id="c0f97-141">所有的 RID 最終將對應至根 `any` RID。</span><span class="sxs-lookup"><span data-stu-id="c0f97-141">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="c0f97-142">處理 RID 時，您必須謹記一些考量：</span><span class="sxs-lookup"><span data-stu-id="c0f97-142">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="c0f97-143">RID 是**隱晦字串**，因此必須以黑箱視之。</span><span class="sxs-lookup"><span data-stu-id="c0f97-143">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="c0f97-144">不要以程式設計方式建置 RID。</span><span class="sxs-lookup"><span data-stu-id="c0f97-144">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="c0f97-145">使用已針對平台定義的 RID。</span><span class="sxs-lookup"><span data-stu-id="c0f97-145">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="c0f97-146">RID 必須是特定的，因此不要假設實際 RID 值會怎樣。</span><span class="sxs-lookup"><span data-stu-id="c0f97-146">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="c0f97-147">使用 RID</span><span class="sxs-lookup"><span data-stu-id="c0f97-147">Using RIDs</span></span>

<span data-ttu-id="c0f97-148">若要使用 RID，必須先了解有哪些 RID 存在。</span><span class="sxs-lookup"><span data-stu-id="c0f97-148">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="c0f97-149">新的值會定期新增至平台。</span><span class="sxs-lookup"><span data-stu-id="c0f97-149">New values are added regularly to the platform.</span></span>
<span data-ttu-id="c0f97-150">如需最新的完整版本，請查看 CoreFX 存放庫上的 [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) 檔案。</span><span class="sxs-lookup"><span data-stu-id="c0f97-150">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="c0f97-151">.NET Core 2.0 SDK 引進可攜式 RID 的概念。</span><span class="sxs-lookup"><span data-stu-id="c0f97-151">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="c0f97-152">它們是新增到 RID 圖形且未繫結到特定版本或 OS 發行版本的新值。</span><span class="sxs-lookup"><span data-stu-id="c0f97-152">They are new values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="c0f97-153">處理多個 Linux 散發時，它們特別實用。</span><span class="sxs-lookup"><span data-stu-id="c0f97-153">They're particularly useful when dealing with multiple Linux distros.</span></span>

<span data-ttu-id="c0f97-154">下列清單顯示用於每個 OS 的最常見 RID。</span><span class="sxs-lookup"><span data-stu-id="c0f97-154">The following list shows the most common RIDs used for each OS.</span></span> <span data-ttu-id="c0f97-155">它不涵蓋 `arm` 或 `corert` 值。</span><span class="sxs-lookup"><span data-stu-id="c0f97-155">It doesn't cover `arm` or `corert` values.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="c0f97-156">Windows RID</span><span class="sxs-lookup"><span data-stu-id="c0f97-156">Windows RIDs</span></span>

- <span data-ttu-id="c0f97-157">可攜式</span><span class="sxs-lookup"><span data-stu-id="c0f97-157">Portable</span></span>
  - `win-x86`
  - `win-x64`
- <span data-ttu-id="c0f97-158">Windows 7/Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c0f97-158">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="c0f97-159">Windows 8/Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c0f97-159">Windows 8 / Windows Server 2012</span></span>
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- <span data-ttu-id="c0f97-160">Windows 8.1/Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c0f97-160">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="c0f97-161">Windows 10/Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="c0f97-161">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="c0f97-162">如需詳細資訊，請參閱 [Windows 上 .NET Core 的必要條件](windows-prerequisites.md)。</span><span class="sxs-lookup"><span data-stu-id="c0f97-162">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="c0f97-163">Linux RID</span><span class="sxs-lookup"><span data-stu-id="c0f97-163">Linux RIDs</span></span>

- <span data-ttu-id="c0f97-164">可攜式</span><span class="sxs-lookup"><span data-stu-id="c0f97-164">Portable</span></span>
  - `linux-x64`
- <span data-ttu-id="c0f97-165">CentOS</span><span class="sxs-lookup"><span data-stu-id="c0f97-165">CentOS</span></span>
  - `centos-x64`
  - `centos.7-x64`
- <span data-ttu-id="c0f97-166">Debian</span><span class="sxs-lookup"><span data-stu-id="c0f97-166">Debian</span></span>
  - `debian-x64`
  - `debian.8-x64`
- <span data-ttu-id="c0f97-167">Fedora</span><span class="sxs-lookup"><span data-stu-id="c0f97-167">Fedora</span></span>
  - `fedora-x64`
  - `fedora.24-x64`
  - <span data-ttu-id="c0f97-168">`fedora.25-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="c0f97-168">`fedora.25-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="c0f97-169">`fedora.26-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="c0f97-169">`fedora.26-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="c0f97-170">Gentoo (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="c0f97-170">Gentoo (.NET Core 2.0 or later versions)</span></span>
  - `gentoo-x64`
- <span data-ttu-id="c0f97-171">openSUSE</span><span class="sxs-lookup"><span data-stu-id="c0f97-171">openSUSE</span></span>
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- <span data-ttu-id="c0f97-172">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="c0f97-172">Oracle Linux</span></span>
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- <span data-ttu-id="c0f97-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="c0f97-173">Red Hat Enterprise Linux</span></span>
  - `rhel-x64`
  - <span data-ttu-id="c0f97-174">`rhel.6-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="c0f97-174">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - <span data-ttu-id="c0f97-175">`rhel.7.3-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="c0f97-175">`rhel.7.3-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="c0f97-176">`rhel.7.4-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="c0f97-176">`rhel.7.4-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="c0f97-177">Tizen (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="c0f97-177">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
- <span data-ttu-id="c0f97-178">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c0f97-178">Ubuntu</span></span>
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- <span data-ttu-id="c0f97-179">Ubuntu 衍生版</span><span class="sxs-lookup"><span data-stu-id="c0f97-179">Ubuntu derivatives</span></span>
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - <span data-ttu-id="c0f97-180">`linuxmint.18.1-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="c0f97-180">`linuxmint.18.1-x64` (.NET Core 2.0 or later versions)</span></span>

<span data-ttu-id="c0f97-181">如需詳細資訊，請參閱 [Linux 上 .NET Core 的必要條件](linux-prerequisites.md)。</span><span class="sxs-lookup"><span data-stu-id="c0f97-181">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="c0f97-182">macOS RID</span><span class="sxs-lookup"><span data-stu-id="c0f97-182">macOS RIDs</span></span>

<span data-ttu-id="c0f97-183">macOS RID 使用較舊的 "OSX" 商標。</span><span class="sxs-lookup"><span data-stu-id="c0f97-183">macOS RIDs use the older "OSX" branding.</span></span>

- <span data-ttu-id="c0f97-184">`osx-x64` (.NET Core 2.0 或更新版本，最小版本為 `osx.10.12-x64`)</span><span class="sxs-lookup"><span data-stu-id="c0f97-184">`osx-x64` (.NET Core 2.0 or later versions, minimum version is `osx.10.12-x64`)</span></span>
- `osx.10.10-x64`
- `osx.10.11-x64`
- <span data-ttu-id="c0f97-185">`osx.10.12-x64` (.NET Core 1.1 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="c0f97-185">`osx.10.12-x64` (.NET Core 1.1 or later versions)</span></span>
- `osx.10.13-x64`

<span data-ttu-id="c0f97-186">如需詳細資訊，請參閱 [macOS 上 .NET Core 的必要條件](macos-prerequisites.md)。</span><span class="sxs-lookup"><span data-stu-id="c0f97-186">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="android-rids-net-core-20-or-later-versions"></a><span data-ttu-id="c0f97-187">Android RID (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="c0f97-187">Android RIDs (.NET Core 2.0 or later versions)</span></span>

- `android`
- `android.21`

## <a name="see-also"></a><span data-ttu-id="c0f97-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0f97-188">See also</span></span>

[<span data-ttu-id="c0f97-189">執行階段識別碼</span><span class="sxs-lookup"><span data-stu-id="c0f97-189">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
