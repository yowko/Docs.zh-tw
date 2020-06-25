---
title: 在 RHEL-.NET Core 上安裝 .NET Core
description: 示範在 RHEL 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 4a406fe1834c16bab9a5548b69206b51270b33fa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324717"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-rhel"></a><span data-ttu-id="cba2e-103">在 RHEL 上安裝 .NET Core SDK 或 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="cba2e-103">Install .NET Core SDK or .NET Core Runtime on RHEL</span></span>

<span data-ttu-id="cba2e-104">RHEL 支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="cba2e-104">.NET Core is supported on RHEL.</span></span> <span data-ttu-id="cba2e-105">本文說明如何在 RHEL 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="cba2e-105">This article describes how to install .NET Core on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="cba2e-106">註冊您的 Red Hat 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="cba2e-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="cba2e-107">若要從 RHEL 上的 Red Hat 安裝 .NET Core，您必須先使用 Red Hat 訂用帳戶管理員進行註冊。</span><span class="sxs-lookup"><span data-stu-id="cba2e-107">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="cba2e-108">如果未在您的系統上完成此動作，或您不確定，請參閱[.Net Core 的 Red Hat 產品檔](https://access.redhat.com/documentation/net_core/)。</span><span class="sxs-lookup"><span data-stu-id="cba2e-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="cba2e-109">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="cba2e-109">Supported distributions</span></span>

<span data-ttu-id="cba2e-110">下表是 RHEL 7 和 RHEL 8 上目前支援的 .NET Core 版本清單。</span><span class="sxs-lookup"><span data-stu-id="cba2e-110">The following table is a list of currently supported .NET Core releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="cba2e-111">在[.Net Core 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或已不再支援 RHEL 版本之前，會持續支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="cba2e-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="cba2e-112">✔️表示仍然支援 RHEL 或 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="cba2e-112">A ✔️ indicates that the version of RHEL or .NET Core is still supported.</span></span>
- <span data-ttu-id="cba2e-113">A ❌ 表示該 rhel 版本不支援 rhel 或 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="cba2e-113">A ❌ indicates that the version of RHEL or .NET Core isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="cba2e-114">當 RHEL 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="cba2e-114">When both a version of RHEL and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="cba2e-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="cba2e-115">RHEL</span></span>                   | <span data-ttu-id="cba2e-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cba2e-116">.NET Core 2.1</span></span> | <span data-ttu-id="cba2e-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="cba2e-117">.NET Core 3.1</span></span> | <span data-ttu-id="cba2e-118">.NET 5 Preview （僅限手動安裝）</span><span class="sxs-lookup"><span data-stu-id="cba2e-118">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="cba2e-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="cba2e-119">✔️ [8](#rhel-8-)</span></span> | <span data-ttu-id="cba2e-120">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="cba2e-120">✔️ 2.1</span></span>        | <span data-ttu-id="cba2e-121">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="cba2e-121">✔️ 3.1</span></span>        | <span data-ttu-id="cba2e-122">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="cba2e-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cba2e-123">✔️ [7](#rhel-7-)</span><span class="sxs-lookup"><span data-stu-id="cba2e-123">✔️ [7](#rhel-7-)</span></span> | <span data-ttu-id="cba2e-124">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="cba2e-124">✔️ 2.1</span></span>        | <span data-ttu-id="cba2e-125">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="cba2e-125">✔️ 3.1</span></span>        | <span data-ttu-id="cba2e-126">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="cba2e-126">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="cba2e-127">已不再支援下列 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="cba2e-127">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="cba2e-128">這些下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="cba2e-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="cba2e-129">3.0</span><span class="sxs-lookup"><span data-stu-id="cba2e-129">3.0</span></span>
- <span data-ttu-id="cba2e-130">2.2</span><span class="sxs-lookup"><span data-stu-id="cba2e-130">2.2</span></span>
- <span data-ttu-id="cba2e-131">2.0</span><span class="sxs-lookup"><span data-stu-id="cba2e-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="cba2e-132">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="cba2e-132">How to install other versions</span></span>

<span data-ttu-id="cba2e-133">請參閱[.Net core 的 Red Hat 檔](https://access.redhat.com/documentation/net_core/)，以瞭解安裝其他版本的 .net core 所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="cba2e-133">Consult the [Red Hat documentation for .NET Core](https://access.redhat.com/documentation/net_core/) on the steps required to install other releases of .NET Core.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="cba2e-134">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="cba2e-134">RHEL 8 ✔️</span></span>

<span data-ttu-id="cba2e-135">.NET Core 包含在 RHEL 8 的應用程式資料流程存放庫中。</span><span class="sxs-lookup"><span data-stu-id="cba2e-135">.NET Core is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="rhel-7-"></a><span data-ttu-id="cba2e-136">RHEL 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="cba2e-136">RHEL 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="cba2e-137">下列命令會安裝 `scl-utils` 套件：</span><span class="sxs-lookup"><span data-stu-id="cba2e-137">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="cba2e-138">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="cba2e-138">Install the SDK</span></span>

<span data-ttu-id="cba2e-139">.NET Core SDK 可讓您使用 .NET Core 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="cba2e-139">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="cba2e-140">如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="cba2e-140">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="cba2e-141">若要安裝 .NET Core SDK，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="cba2e-141">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="cba2e-142">Red Hat 不建議永久啟用 `rh-dotnet31` ，因為它可能會影響其他程式。</span><span class="sxs-lookup"><span data-stu-id="cba2e-142">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="cba2e-143">例如， `rh-dotnet31` 包含 `libcurl` 不同于基底 RHEL 版本的版本。</span><span class="sxs-lookup"><span data-stu-id="cba2e-143">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="cba2e-144">這可能會導致未預期不同版本的程式發生問題 `libcurl` 。</span><span class="sxs-lookup"><span data-stu-id="cba2e-144">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="cba2e-145">如果您想要 `rh-dotnet` 永久啟用，請將下列程式程式碼新增至 _~/.bashrc_檔案。</span><span class="sxs-lookup"><span data-stu-id="cba2e-145">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="cba2e-146">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="cba2e-146">Install the runtime</span></span>

<span data-ttu-id="cba2e-147">.NET Core 執行時間可讓您執行使用 .NET Core 所建立且未包含執行時間的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cba2e-147">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="cba2e-148">下列命令會安裝 ASP.NET Core 執行時間，這是適用于 .NET Core 的最相容執行時間。</span><span class="sxs-lookup"><span data-stu-id="cba2e-148">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="cba2e-149">在您的終端機中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="cba2e-149">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="cba2e-150">Red Hat 不建議永久啟用 `rh-dotnet31-aspnetcore-runtime-3.1` ，因為它可能會影響其他程式。</span><span class="sxs-lookup"><span data-stu-id="cba2e-150">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="cba2e-151">例如， `rh-dotnet31-aspnetcore-runtime-3.1` 包含 `libcurl` 不同于基底 RHEL 版本的版本。</span><span class="sxs-lookup"><span data-stu-id="cba2e-151">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="cba2e-152">這可能會導致未預期不同版本的程式發生問題 `libcurl` 。</span><span class="sxs-lookup"><span data-stu-id="cba2e-152">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="cba2e-153">如果您想要 `rh-dotnet31-aspnetcore-runtime-3.1` 永久啟用，請將下列程式程式碼新增至 _~/.bashrc_檔案。</span><span class="sxs-lookup"><span data-stu-id="cba2e-153">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="cba2e-154">除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間： `rh-dotnet31-aspnetcore-runtime-3.1` 使用上述命令取代 `rh-dotnet31-dotnet-runtime-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="cba2e-154">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="cba2e-155">抓取</span><span class="sxs-lookup"><span data-stu-id="cba2e-155">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="cba2e-156">相依性</span><span class="sxs-lookup"><span data-stu-id="cba2e-156">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="cba2e-157">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="cba2e-157">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="cba2e-158">手動安裝</span><span class="sxs-lookup"><span data-stu-id="cba2e-158">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="cba2e-159">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cba2e-159">Next steps</span></span>

- [<span data-ttu-id="cba2e-160">教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="cba2e-160">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
