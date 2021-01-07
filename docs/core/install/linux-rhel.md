---
title: 在 RHEL 上安裝 .NET-.NET
description: 示範在 RHEL 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: d585017919507a8fdcbb24778a0ff3ab3d9049c2
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970794"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="1bc57-103">在 RHEL 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="1bc57-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="1bc57-104">RHEL 支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="1bc57-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="1bc57-105">本文說明如何在 RHEL 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="1bc57-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="1bc57-106">註冊您的 Red Hat 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="1bc57-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="1bc57-107">若要在 RHEL 上從 Red Hat 安裝 .NET，您必須先使用 Red Hat 訂用帳戶管理員進行註冊。</span><span class="sxs-lookup"><span data-stu-id="1bc57-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="1bc57-108">如果未在您的系統上完成此操作，或如果您不確定，請參閱 [.net 的 Red Hat 產品檔](https://access.redhat.com/documentation/net/5.0/)。</span><span class="sxs-lookup"><span data-stu-id="1bc57-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="1bc57-109">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="1bc57-109">Supported distributions</span></span>

<span data-ttu-id="1bc57-110">下表是 RHEL 7 和 RHEL 8 上目前支援的 .NET 版本清單。</span><span class="sxs-lookup"><span data-stu-id="1bc57-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="1bc57-111">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或已不再支援 RHEL 版本，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="1bc57-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="1bc57-112">✔️表示仍支援 RHEL 或 .NET 的版本。</span><span class="sxs-lookup"><span data-stu-id="1bc57-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="1bc57-113">❌表示該 rhel 版本不支援 rhel 或 .net 的版本。</span><span class="sxs-lookup"><span data-stu-id="1bc57-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="1bc57-114">當版本的 RHEL 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="1bc57-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="1bc57-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="1bc57-115">RHEL</span></span>                     | <span data-ttu-id="1bc57-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1bc57-116">.NET Core 2.1</span></span> | <span data-ttu-id="1bc57-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="1bc57-117">.NET Core 3.1</span></span> | <span data-ttu-id="1bc57-118">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1bc57-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="1bc57-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="1bc57-119">✔️ [8](#rhel-8-)</span></span>        | <span data-ttu-id="1bc57-120">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="1bc57-120">✔️ 2.1</span></span>        | <span data-ttu-id="1bc57-121">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="1bc57-121">✔️ 3.1</span></span>        | <span data-ttu-id="1bc57-122">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="1bc57-122">✔️ 5.0</span></span> |
| <span data-ttu-id="1bc57-123">✔️ [7](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="1bc57-123">✔️ [7](#rhel-7--net-50)</span></span> | <span data-ttu-id="1bc57-124">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="1bc57-124">✔️ 2.1</span></span>        | <span data-ttu-id="1bc57-125">✔️ [3.1](#rhel-7--net-core-31)</span><span class="sxs-lookup"><span data-stu-id="1bc57-125">✔️ [3.1](#rhel-7--net-core-31)</span></span>        | <span data-ttu-id="1bc57-126">✔️ [5.0](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="1bc57-126">✔️ [5.0](#rhel-7--net-50)</span></span> |

<span data-ttu-id="1bc57-127">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="1bc57-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="1bc57-128">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="1bc57-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="1bc57-129">3.0</span><span class="sxs-lookup"><span data-stu-id="1bc57-129">3.0</span></span>
- <span data-ttu-id="1bc57-130">2.2</span><span class="sxs-lookup"><span data-stu-id="1bc57-130">2.2</span></span>
- <span data-ttu-id="1bc57-131">2.0</span><span class="sxs-lookup"><span data-stu-id="1bc57-131">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="1bc57-132">移除預覽版本</span><span class="sxs-lookup"><span data-stu-id="1bc57-132">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="rhel-8-"></a><span data-ttu-id="1bc57-133">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="1bc57-133">RHEL 8 ✔️</span></span>

<span data-ttu-id="1bc57-134">.NET 包含在 RHEL 8 的應用程式資料流程存放庫中。</span><span class="sxs-lookup"><span data-stu-id="1bc57-134">.NET is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a><span data-ttu-id="1bc57-135">RHEL 7 ✔️ .NET 5。0</span><span class="sxs-lookup"><span data-stu-id="1bc57-135">RHEL 7 ✔️ .NET 5.0</span></span>

<span data-ttu-id="1bc57-136">下列命令會安裝 `scl-utils` 套件：</span><span class="sxs-lookup"><span data-stu-id="1bc57-136">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="1bc57-137">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="1bc57-137">Install the SDK</span></span>

<span data-ttu-id="1bc57-138">.NET SDK 可讓您使用 .NET 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="1bc57-138">The .NET SDK allows you to develop apps with .NET .</span></span> <span data-ttu-id="1bc57-139">如果您安裝 .NET SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="1bc57-139">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="1bc57-140">若要安裝 .NET SDK，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1bc57-140">To install .NET SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="1bc57-141">Red Hat 不建議永久啟用 `rh-dotnet50` ，因為它可能會影響其他程式。</span><span class="sxs-lookup"><span data-stu-id="1bc57-141">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="1bc57-142">如果您想要 `rh-dotnet` 永久啟用，請將下列這一行新增至 _~/.bashrc_ 檔案。</span><span class="sxs-lookup"><span data-stu-id="1bc57-142">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a><span data-ttu-id="1bc57-143">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="1bc57-143">Install the runtime</span></span>

<span data-ttu-id="1bc57-144">.NET 執行時間可讓您執行以 .NET 建立的應用程式，而這些應用程式不包含執行時間。</span><span class="sxs-lookup"><span data-stu-id="1bc57-144">The .NET Runtime allows you to run apps that were made with .NET that didn't include the runtime.</span></span> <span data-ttu-id="1bc57-145">下列命令會安裝 ASP.NET Core 執行時間，這是 .NET Core 最相容的執行時間。</span><span class="sxs-lookup"><span data-stu-id="1bc57-145">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="1bc57-146">在您的終端機中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="1bc57-146">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="1bc57-147">Red Hat 不建議永久啟用 `rh-dotnet50` ，因為它可能會影響其他程式。</span><span class="sxs-lookup"><span data-stu-id="1bc57-147">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="1bc57-148">如果您想要 `rh-dotnet50` 永久啟用，請將下列這一行新增至 _~/.bashrc_ 檔案。</span><span class="sxs-lookup"><span data-stu-id="1bc57-148">If you want to enable `rh-dotnet50` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

<span data-ttu-id="1bc57-149">除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET 執行時間： `rh-dotnet50-aspnetcore-runtime-5.0` 在上述命令中將取代為 `rh-dotnet50-dotnet-runtime-5.0` 。</span><span class="sxs-lookup"><span data-stu-id="1bc57-149">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet50-aspnetcore-runtime-5.0` in the commands above with `rh-dotnet50-dotnet-runtime-5.0`.</span></span>

## <a name="rhel-7--net-core-31"></a><span data-ttu-id="1bc57-150">RHEL 7 ✔️ .NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="1bc57-150">RHEL 7 ✔️ .NET Core 3.1</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="1bc57-151">下列命令會安裝 `scl-utils` 套件：</span><span class="sxs-lookup"><span data-stu-id="1bc57-151">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="1bc57-152">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="1bc57-152">Install the SDK</span></span>

<span data-ttu-id="1bc57-153">.NET Core SDK 可讓您使用 .NET Core 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="1bc57-153">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="1bc57-154">如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="1bc57-154">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="1bc57-155">若要安裝 .NET Core SDK，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1bc57-155">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="1bc57-156">Red Hat 不建議永久啟用 `rh-dotnet31` ，因為它可能會影響其他程式。</span><span class="sxs-lookup"><span data-stu-id="1bc57-156">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="1bc57-157">例如， `rh-dotnet31` 包含 `libcurl` 與基底 RHEL 版本不同的版本。</span><span class="sxs-lookup"><span data-stu-id="1bc57-157">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="1bc57-158">這可能會導致不預期不同版本的程式發生問題 `libcurl` 。</span><span class="sxs-lookup"><span data-stu-id="1bc57-158">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="1bc57-159">如果您想要 `rh-dotnet` 永久啟用，請將下列這一行新增至 _~/.bashrc_ 檔案。</span><span class="sxs-lookup"><span data-stu-id="1bc57-159">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="1bc57-160">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="1bc57-160">Install the runtime</span></span>

<span data-ttu-id="1bc57-161">.NET Core 執行時間可讓您執行未包含執行時間的 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1bc57-161">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="1bc57-162">下列命令會安裝 ASP.NET Core 執行時間，這是 .NET Core 最相容的執行時間。</span><span class="sxs-lookup"><span data-stu-id="1bc57-162">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="1bc57-163">在您的終端機中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="1bc57-163">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="1bc57-164">Red Hat 不建議永久啟用 `rh-dotnet31` ，因為它可能會影響其他程式。</span><span class="sxs-lookup"><span data-stu-id="1bc57-164">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="1bc57-165">例如， `rh-dotnet31` 包含 `libcurl` 與基底 RHEL 版本不同的版本。</span><span class="sxs-lookup"><span data-stu-id="1bc57-165">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="1bc57-166">這可能會導致不預期不同版本的程式發生問題 `libcurl` 。</span><span class="sxs-lookup"><span data-stu-id="1bc57-166">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="1bc57-167">如果您想要 `rh-dotnet31` 永久啟用，請將下列這一行新增至 _~/.bashrc_ 檔案。</span><span class="sxs-lookup"><span data-stu-id="1bc57-167">If you want to enable `rh-dotnet31` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

<span data-ttu-id="1bc57-168">除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間： `rh-dotnet31-aspnetcore-runtime-3.1` 在上述命令中將取代為 `rh-dotnet31-dotnet-runtime-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="1bc57-168">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="dependencies"></a><span data-ttu-id="1bc57-169">相依性</span><span class="sxs-lookup"><span data-stu-id="1bc57-169">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="1bc57-170">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="1bc57-170">How to install other versions</span></span>

<span data-ttu-id="1bc57-171">請參閱 [.net 的 Red Hat 檔](https://access.redhat.com/documentation/net/5.0/) ，以瞭解安裝其他 .net 版本所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="1bc57-171">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1bc57-172">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1bc57-172">Next steps</span></span>

- [<span data-ttu-id="1bc57-173">如何啟用 .NET CLI 的 TAB 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="1bc57-173">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="1bc57-174">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1bc57-174">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
