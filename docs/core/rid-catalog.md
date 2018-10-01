---
title: .NET Core 執行階段識別項 (RID) 目錄
description: 了解執行階段識別碼 (RID) 以及 RID 在 .NET Core 中的使用方式。
author: mairaw
ms.author: mairaw
ms.date: 07/19/2018
ms.openlocfilehash: ff0449f7c6f878131f0ec4b16d685d2c02d26719
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517375"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="efad0-103">.NET Core RID 類別目錄</span><span class="sxs-lookup"><span data-stu-id="efad0-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="efad0-104">RID 是*執行階段識別項*的縮寫。</span><span class="sxs-lookup"><span data-stu-id="efad0-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="efad0-105">RID 值是用來識別應用程式執行所在的目標平台。</span><span class="sxs-lookup"><span data-stu-id="efad0-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="efad0-106">.NET 套件會使用它們來代表 NuGet 套件中的平台特定資產。</span><span class="sxs-lookup"><span data-stu-id="efad0-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="efad0-107">下列值是 RID 的範例：`linux-x64`、`ubuntu.14.04-x64`、`win7-x64` 或 `osx.10.12-x64`。</span><span class="sxs-lookup"><span data-stu-id="efad0-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="efad0-108">針對具有原生相依性的套件，RID 也可指定能在哪些平台上還原套件。</span><span class="sxs-lookup"><span data-stu-id="efad0-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="efad0-109">單一 RID 可在您專案檔的 `<RuntimeIdentifier>` 元素中設定。</span><span class="sxs-lookup"><span data-stu-id="efad0-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="efad0-110">可以在專案檔的 `<RuntimeIdentifiers>` 元素中，將多個 RID 定義為以分號分隔的清單。</span><span class="sxs-lookup"><span data-stu-id="efad0-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="efad0-111">它們也可以透過以`--runtime`選項搭配下列 [.NET Core CLI 命令](./tools/index.md)來使用：</span><span class="sxs-lookup"><span data-stu-id="efad0-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="efad0-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="efad0-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="efad0-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="efad0-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="efad0-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="efad0-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="efad0-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="efad0-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="efad0-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="efad0-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="efad0-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="efad0-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="efad0-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="efad0-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="efad0-119">代表具體作業系統的 RID 通常遵循 `[os].[version]-[architecture]-[additional qualifiers]` 這個模式，其中：</span><span class="sxs-lookup"><span data-stu-id="efad0-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="efad0-120">`[os]` 是作業/平台系統 Moniker。</span><span class="sxs-lookup"><span data-stu-id="efad0-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="efad0-121">例如，`ubuntu`。</span><span class="sxs-lookup"><span data-stu-id="efad0-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="efad0-122">`[version]` 是作業系統版本，使用以點分隔 (`.`) 的版本號碼表示。</span><span class="sxs-lookup"><span data-stu-id="efad0-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="efad0-123">例如，`15.10`。</span><span class="sxs-lookup"><span data-stu-id="efad0-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="efad0-124">版本**不應為**行銷版本，因為行銷版本通常代表作業系統的多個個別版本，且具有不同平台 API 介面區。</span><span class="sxs-lookup"><span data-stu-id="efad0-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="efad0-125">`[architecture]` 處理器架構。</span><span class="sxs-lookup"><span data-stu-id="efad0-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="efad0-126">例如：`x86`、`x64`、`arm` 或 `arm64`。</span><span class="sxs-lookup"><span data-stu-id="efad0-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="efad0-127">`[additional qualifiers]` 進一步區分不同平台。</span><span class="sxs-lookup"><span data-stu-id="efad0-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="efad0-128">例如：`aot` 或 `corert`。</span><span class="sxs-lookup"><span data-stu-id="efad0-128">For example: `aot` or `corert`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="efad0-129">RID 圖表</span><span class="sxs-lookup"><span data-stu-id="efad0-129">RID graph</span></span>

<span data-ttu-id="efad0-130">RID 圖表或執行階段後援圖形是與彼此相容的 RID 清單。</span><span class="sxs-lookup"><span data-stu-id="efad0-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="efad0-131">RID 是在 [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) 套件中定義。</span><span class="sxs-lookup"><span data-stu-id="efad0-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="efad0-132">您可以在 [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) 檔案 (位於 CoreFX 存放庫) 中看到支援的 RID 清單與 RID 圖形。</span><span class="sxs-lookup"><span data-stu-id="efad0-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="efad0-133">在此檔案中，您可以看到所有 RID (基底項目除外) 都包含 `"#import"` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="efad0-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="efad0-134">這些陳述式指出相容的 RID。</span><span class="sxs-lookup"><span data-stu-id="efad0-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="efad0-135">當 NuGet 還原套件時，它會嘗試尋找與所指定執行階段完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="efad0-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="efad0-136">若找不到完全相符的項目，NuGet 會返回到圖形，直到它根據 RID 圖形找到最接近的相容系統。</span><span class="sxs-lookup"><span data-stu-id="efad0-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="efad0-137">下列範例是 `osx.10.12-x64` RID 的實際項目：</span><span class="sxs-lookup"><span data-stu-id="efad0-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="efad0-138">上述 RID 指定 `osx.10.12-x64` 匯入 `osx.10.11-x64`。</span><span class="sxs-lookup"><span data-stu-id="efad0-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="efad0-139">因此，當 NuGet 還原套件時，它會嘗試在套件中尋找與 `osx.10.12-x64` 完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="efad0-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="efad0-140">例如，若 NuGet 找不到特定執行階段，它可以還原指定 `osx.10.11-x64` 執行階段的套件。</span><span class="sxs-lookup"><span data-stu-id="efad0-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="efad0-141">下列範例顯示也在 *runtime.json* 檔案中定義的稍大 RID 圖形：</span><span class="sxs-lookup"><span data-stu-id="efad0-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="efad0-142">所有的 RID 最終將對應至根 `any` RID。</span><span class="sxs-lookup"><span data-stu-id="efad0-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="efad0-143">處理 RID 時，您必須謹記一些考量：</span><span class="sxs-lookup"><span data-stu-id="efad0-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="efad0-144">RID 是**隱晦字串**，因此必須以黑箱視之。</span><span class="sxs-lookup"><span data-stu-id="efad0-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="efad0-145">不要以程式設計方式建置 RID。</span><span class="sxs-lookup"><span data-stu-id="efad0-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="efad0-146">使用已針對平台定義的 RID。</span><span class="sxs-lookup"><span data-stu-id="efad0-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="efad0-147">RID 必須是特定的，因此不要假設實際 RID 值會怎樣。</span><span class="sxs-lookup"><span data-stu-id="efad0-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="efad0-148">使用 RID</span><span class="sxs-lookup"><span data-stu-id="efad0-148">Using RIDs</span></span>

<span data-ttu-id="efad0-149">若要使用 RID，必須先了解有哪些 RID 存在。</span><span class="sxs-lookup"><span data-stu-id="efad0-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="efad0-150">新的值會定期新增至平台。</span><span class="sxs-lookup"><span data-stu-id="efad0-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="efad0-151">如需最新的完整版本，請查看 CoreFX 存放庫上的 [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) 檔案。</span><span class="sxs-lookup"><span data-stu-id="efad0-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="efad0-152">.NET Core 2.0 SDK 引進可攜式 RID 的概念。</span><span class="sxs-lookup"><span data-stu-id="efad0-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="efad0-153">它們是新增到 RID 圖形且未繫結到特定版本或 OS 發行版本的新值。</span><span class="sxs-lookup"><span data-stu-id="efad0-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="efad0-154">處理多個 Linux 散發時，它們特別實用。</span><span class="sxs-lookup"><span data-stu-id="efad0-154">They're particularly useful when dealing with multiple Linux distros.</span></span>

<span data-ttu-id="efad0-155">下列清單顯示用於每個 OS 的最常見 RID。</span><span class="sxs-lookup"><span data-stu-id="efad0-155">The following list shows the most common RIDs used for each OS.</span></span> <span data-ttu-id="efad0-156">它不涵蓋 `arm` 或 `corert` 值。</span><span class="sxs-lookup"><span data-stu-id="efad0-156">It doesn't cover `arm` or `corert` values.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="efad0-157">Windows RID</span><span class="sxs-lookup"><span data-stu-id="efad0-157">Windows RIDs</span></span>

- <span data-ttu-id="efad0-158">可攜式</span><span class="sxs-lookup"><span data-stu-id="efad0-158">Portable</span></span>
  - `win-x86`
  - `win-x64`
- <span data-ttu-id="efad0-159">Windows 7/Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="efad0-159">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="efad0-160">Windows 8/Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="efad0-160">Windows 8 / Windows Server 2012</span></span>
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- <span data-ttu-id="efad0-161">Windows 8.1/Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="efad0-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="efad0-162">Windows 10/Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="efad0-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="efad0-163">如需詳細資訊，請參閱 [Windows 上 .NET Core 的必要條件](windows-prerequisites.md)。</span><span class="sxs-lookup"><span data-stu-id="efad0-163">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="efad0-164">Linux RID</span><span class="sxs-lookup"><span data-stu-id="efad0-164">Linux RIDs</span></span>

- <span data-ttu-id="efad0-165">可攜式</span><span class="sxs-lookup"><span data-stu-id="efad0-165">Portable</span></span>
  - `linux-x64`
- <span data-ttu-id="efad0-166">CentOS</span><span class="sxs-lookup"><span data-stu-id="efad0-166">CentOS</span></span>
  - `centos-x64`
  - `centos.7-x64`
- <span data-ttu-id="efad0-167">Debian</span><span class="sxs-lookup"><span data-stu-id="efad0-167">Debian</span></span>
  - `debian-x64`
  - `debian.8-x64`
  - <span data-ttu-id="efad0-168">`debian.9-x64` (.NET Core 1.1 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-168">`debian.9-x64` (.NET Core 1.1 or later versions)</span></span>
- <span data-ttu-id="efad0-169">Fedora</span><span class="sxs-lookup"><span data-stu-id="efad0-169">Fedora</span></span>
  - `fedora-x64`
  - `fedora.27-x64`
  - <span data-ttu-id="efad0-170">`fedora.28-x64` (.NET Core 1.1 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-170">`fedora.28-x64` (.NET Core 1.1 or later versions)</span></span>
- <span data-ttu-id="efad0-171">Gentoo (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-171">Gentoo (.NET Core 2.0 or later versions)</span></span>
  - `gentoo-x64`
- <span data-ttu-id="efad0-172">openSUSE</span><span class="sxs-lookup"><span data-stu-id="efad0-172">openSUSE</span></span>
  - `opensuse-x64`
  - `opensuse.42.3-x64`
- <span data-ttu-id="efad0-173">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="efad0-173">Oracle Linux</span></span>
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
  - `ol.7.3-x64`
  - `ol.7.4-x64`
- <span data-ttu-id="efad0-174">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="efad0-174">Red Hat Enterprise Linux</span></span>
  - `rhel-x64`
  - <span data-ttu-id="efad0-175">`rhel.6-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - <span data-ttu-id="efad0-176">`rhel.7.3-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-176">`rhel.7.3-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="efad0-177">`rhel.7.4-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-177">`rhel.7.4-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="efad0-178">Tizen (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-178">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`
- <span data-ttu-id="efad0-179">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="efad0-179">Ubuntu</span></span>
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.17.10-x64`
  - `ubuntu.18.04-x64`
- <span data-ttu-id="efad0-180">Ubuntu 衍生版</span><span class="sxs-lookup"><span data-stu-id="efad0-180">Ubuntu derivatives</span></span>
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - <span data-ttu-id="efad0-181">`linuxmint.18-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-181">`linuxmint.18-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="efad0-182">`linuxmint.18.1-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-182">`linuxmint.18.1-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="efad0-183">`linuxmint.18.2-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-183">`linuxmint.18.2-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="efad0-184">`linuxmint.18.3-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-184">`linuxmint.18.3-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="efad0-185">SUSE Enterprise Linux (SLES) (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-185">SUSE Enterprise Linux (SLES) (.NET Core 2.0 or later versions)</span></span>
  - `sles-x64`
  - `sles.12-x64`
  - `sles.12.1-x64`
  - `sles.12.2-x64`
  - `sles.12.3-x64`
- <span data-ttu-id="efad0-186">Alpine Linux (.NET Core 2.1 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-186">Alpine Linux (.NET Core 2.1 or later versions)</span></span>
  - `alpine-x64`
  - `alpine.3.7-x64`

<span data-ttu-id="efad0-187">如需詳細資訊，請參閱 [Linux 上 .NET Core 的必要條件](linux-prerequisites.md)。</span><span class="sxs-lookup"><span data-stu-id="efad0-187">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="efad0-188">macOS RID</span><span class="sxs-lookup"><span data-stu-id="efad0-188">macOS RIDs</span></span>

<span data-ttu-id="efad0-189">macOS RID 使用較舊的 "OSX" 商標。</span><span class="sxs-lookup"><span data-stu-id="efad0-189">macOS RIDs use the older "OSX" branding.</span></span>

- <span data-ttu-id="efad0-190">`osx-x64` (.NET Core 2.0 或更新版本，最小版本為 `osx.10.12-x64`)</span><span class="sxs-lookup"><span data-stu-id="efad0-190">`osx-x64` (.NET Core 2.0 or later versions, minimum version is `osx.10.12-x64`)</span></span>
- `osx.10.10-x64`
- `osx.10.11-x64`
- <span data-ttu-id="efad0-191">`osx.10.12-x64` (.NET Core 1.1 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-191">`osx.10.12-x64` (.NET Core 1.1 or later versions)</span></span>
- `osx.10.13-x64`

<span data-ttu-id="efad0-192">如需詳細資訊，請參閱 [macOS 上 .NET Core 的必要條件](macos-prerequisites.md)。</span><span class="sxs-lookup"><span data-stu-id="efad0-192">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="android-rids-net-core-20-or-later-versions"></a><span data-ttu-id="efad0-193">Android RID (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="efad0-193">Android RIDs (.NET Core 2.0 or later versions)</span></span>

- `android`
- `android.21`

## <a name="see-also"></a><span data-ttu-id="efad0-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efad0-194">See also</span></span>

* [<span data-ttu-id="efad0-195">執行階段識別碼</span><span class="sxs-lookup"><span data-stu-id="efad0-195">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
