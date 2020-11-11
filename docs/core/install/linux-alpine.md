---
title: 在 Alpine 上安裝 .NET-.NET
description: 示範在 Alpine 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 29901cc24ddd4bbe8200a36765ddd29f501394c0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506814"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="c4845-103">在 Alpine 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="c4845-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="c4845-104">本文說明如何在 Alpine 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="c4845-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="c4845-105">當 Alpine 版本不受支援時，就不再支援該版本的 .NET。</span><span class="sxs-lookup"><span data-stu-id="c4845-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="c4845-106">不過，這些指示可協助您讓 .NET 在這些版本上執行，即使它不受支援也是一樣。</span><span class="sxs-lookup"><span data-stu-id="c4845-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="c4845-107">沒有適用于 Alpine 的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="c4845-107">There are no installers for Alpine.</span></span> <span data-ttu-id="c4845-108">您必須使用 [安裝腳本](#scripted-install) ，或遵循 [手動安裝](#manual-install) 指示。</span><span class="sxs-lookup"><span data-stu-id="c4845-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="c4845-109">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="c4845-109">Supported distributions</span></span>

<span data-ttu-id="c4845-110">下表列出目前支援的 .NET 版本，以及其支援的 Alpine 版本。</span><span class="sxs-lookup"><span data-stu-id="c4845-110">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="c4845-111">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Alpine 的版本 [達到生命週期結束](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="c4845-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="c4845-112">✔️表示仍支援 Alpine 或 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="c4845-112">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="c4845-113">❌指出該 Alpine 版本不支援 Alpine 或 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="c4845-113">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="c4845-114">當版本的 Alpine 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="c4845-114">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="c4845-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="c4845-115">Alpine</span></span>  | <span data-ttu-id="c4845-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c4845-116">.NET Core 2.1</span></span> | <span data-ttu-id="c4845-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c4845-117">.NET Core 3.1</span></span> | <span data-ttu-id="c4845-118">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="c4845-118">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="c4845-119">✔️3.12</span><span class="sxs-lookup"><span data-stu-id="c4845-119">✔️ 3.12</span></span> | <span data-ttu-id="c4845-120">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="c4845-120">✔️ 2.1</span></span>        | <span data-ttu-id="c4845-121">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="c4845-121">✔️ 3.1</span></span>        | <span data-ttu-id="c4845-122">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="c4845-122">✔️ 5.0</span></span> |
| <span data-ttu-id="c4845-123">✔️3.11</span><span class="sxs-lookup"><span data-stu-id="c4845-123">✔️ 3.11</span></span> | <span data-ttu-id="c4845-124">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="c4845-124">✔️ 2.1</span></span>        | <span data-ttu-id="c4845-125">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="c4845-125">✔️ 3.1</span></span>        | <span data-ttu-id="c4845-126">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="c4845-126">✔️ 5.0</span></span> |
| <span data-ttu-id="c4845-127">✔️3.10</span><span class="sxs-lookup"><span data-stu-id="c4845-127">✔️ 3.10</span></span> | <span data-ttu-id="c4845-128">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="c4845-128">✔️ 2.1</span></span>        | <span data-ttu-id="c4845-129">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="c4845-129">✔️ 3.1</span></span>        | <span data-ttu-id="c4845-130">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="c4845-130">❌ 5.0</span></span> |
| <span data-ttu-id="c4845-131">❌ 3.9</span><span class="sxs-lookup"><span data-stu-id="c4845-131">❌ 3.9</span></span>  | <span data-ttu-id="c4845-132">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="c4845-132">✔️ 2.1</span></span>        | <span data-ttu-id="c4845-133">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="c4845-133">✔️ 3.1</span></span>        | <span data-ttu-id="c4845-134">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="c4845-134">❌ 5.0</span></span> |
| <span data-ttu-id="c4845-135">❌ 3.8</span><span class="sxs-lookup"><span data-stu-id="c4845-135">❌ 3.8</span></span>  | <span data-ttu-id="c4845-136">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="c4845-136">✔️ 2.1</span></span>        | <span data-ttu-id="c4845-137">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="c4845-137">✔️ 3.1</span></span>        | <span data-ttu-id="c4845-138">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="c4845-138">❌ 5.0</span></span> |

<span data-ttu-id="c4845-139">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="c4845-139">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="c4845-140">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="c4845-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="c4845-141">3.0</span><span class="sxs-lookup"><span data-stu-id="c4845-141">3.0</span></span>
- <span data-ttu-id="c4845-142">2.2</span><span class="sxs-lookup"><span data-stu-id="c4845-142">2.2</span></span>
- <span data-ttu-id="c4845-143">2.0</span><span class="sxs-lookup"><span data-stu-id="c4845-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="c4845-144">相依性</span><span class="sxs-lookup"><span data-stu-id="c4845-144">Dependencies</span></span>

<span data-ttu-id="c4845-145">Alpine Linux 上的 .NET 需要安裝下列相依性：</span><span class="sxs-lookup"><span data-stu-id="c4845-145">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="c4845-146">icu-程式庫</span><span class="sxs-lookup"><span data-stu-id="c4845-146">icu-libs</span></span>
- <span data-ttu-id="c4845-147">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="c4845-147">krb5-libs</span></span>
- <span data-ttu-id="c4845-148">libgcc</span><span class="sxs-lookup"><span data-stu-id="c4845-148">libgcc</span></span>
- <span data-ttu-id="c4845-149">libintl</span><span class="sxs-lookup"><span data-stu-id="c4845-149">libintl</span></span>
- <span data-ttu-id="c4845-150">libssl1.0.0 1.1 (Alpine 3.9 或更高版本) </span><span class="sxs-lookup"><span data-stu-id="c4845-150">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="c4845-151">libssl1.0.0 1.0 (Alpine 3.8 或更低) </span><span class="sxs-lookup"><span data-stu-id="c4845-151">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="c4845-152">libstdc++</span><span class="sxs-lookup"><span data-stu-id="c4845-152">libstdc++</span></span>
- <span data-ttu-id="c4845-153">zlib</span><span class="sxs-lookup"><span data-stu-id="c4845-153">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="c4845-154">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="c4845-154">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="c4845-155">手動安裝</span><span class="sxs-lookup"><span data-stu-id="c4845-155">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="c4845-156">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c4845-156">Next steps</span></span>

- [<span data-ttu-id="c4845-157">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c4845-157">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
