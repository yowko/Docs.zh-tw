---
title: 在 Alpine 上安裝 .NET-.NET
description: 示範在 Alpine 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 6adaa905c400b45526ebbc3d8e2606522863eec3
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970846"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="b5bfd-103">在 Alpine 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="b5bfd-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="b5bfd-104">本文說明如何在 Alpine 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="b5bfd-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="b5bfd-105">當 Alpine 版本不受支援時，就不再支援該版本的 .NET。</span><span class="sxs-lookup"><span data-stu-id="b5bfd-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="b5bfd-106">不過，這些指示可協助您讓 .NET 在這些版本上執行，即使它不受支援也是一樣。</span><span class="sxs-lookup"><span data-stu-id="b5bfd-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install"></a><span data-ttu-id="b5bfd-107">安裝</span><span class="sxs-lookup"><span data-stu-id="b5bfd-107">Install</span></span>

<span data-ttu-id="b5bfd-108">安裝程式不適用於 Alpine Linux。</span><span class="sxs-lookup"><span data-stu-id="b5bfd-108">Installers aren't available for Alpine Linux.</span></span> <span data-ttu-id="b5bfd-109">您必須以下列其中一種方式安裝 .NET：</span><span class="sxs-lookup"><span data-stu-id="b5bfd-109">You must install .NET in one of the following ways:</span></span>

- [<span data-ttu-id="b5bfd-110">貼齊套件</span><span class="sxs-lookup"><span data-stu-id="b5bfd-110">Snap package</span></span>](linux-snap.md)
- [<span data-ttu-id="b5bfd-111">使用 _install-dotnet.sh_ 編寫腳本的安裝</span><span class="sxs-lookup"><span data-stu-id="b5bfd-111">Scripted install with _install-dotnet.sh_</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="b5bfd-112">手動二進位解壓縮</span><span class="sxs-lookup"><span data-stu-id="b5bfd-112">Manual binary extraction</span></span>](linux-scripted-manual.md#manual-install)

## <a name="supported-distributions"></a><span data-ttu-id="b5bfd-113">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="b5bfd-113">Supported distributions</span></span>

<span data-ttu-id="b5bfd-114">下表列出目前支援的 .NET 版本，以及其支援的 Alpine 版本。</span><span class="sxs-lookup"><span data-stu-id="b5bfd-114">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="b5bfd-115">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Alpine 的版本 [達到生命週期結束](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="b5bfd-115">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="b5bfd-116">✔️表示仍支援 Alpine 或 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="b5bfd-116">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="b5bfd-117">❌指出該 Alpine 版本不支援 Alpine 或 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="b5bfd-117">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="b5bfd-118">當版本的 Alpine 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="b5bfd-118">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="b5bfd-119">Alpine</span><span class="sxs-lookup"><span data-stu-id="b5bfd-119">Alpine</span></span>  | <span data-ttu-id="b5bfd-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b5bfd-120">.NET Core 2.1</span></span> | <span data-ttu-id="b5bfd-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="b5bfd-121">.NET Core 3.1</span></span> | <span data-ttu-id="b5bfd-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b5bfd-122">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="b5bfd-123">✔️3.12</span><span class="sxs-lookup"><span data-stu-id="b5bfd-123">✔️ 3.12</span></span> | <span data-ttu-id="b5bfd-124">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="b5bfd-124">✔️ 2.1</span></span>        | <span data-ttu-id="b5bfd-125">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="b5bfd-125">✔️ 3.1</span></span>        | <span data-ttu-id="b5bfd-126">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="b5bfd-126">✔️ 5.0</span></span> |
| <span data-ttu-id="b5bfd-127">✔️3.11</span><span class="sxs-lookup"><span data-stu-id="b5bfd-127">✔️ 3.11</span></span> | <span data-ttu-id="b5bfd-128">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="b5bfd-128">✔️ 2.1</span></span>        | <span data-ttu-id="b5bfd-129">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="b5bfd-129">✔️ 3.1</span></span>        | <span data-ttu-id="b5bfd-130">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="b5bfd-130">✔️ 5.0</span></span> |
| <span data-ttu-id="b5bfd-131">✔️3.10</span><span class="sxs-lookup"><span data-stu-id="b5bfd-131">✔️ 3.10</span></span> | <span data-ttu-id="b5bfd-132">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="b5bfd-132">✔️ 2.1</span></span>        | <span data-ttu-id="b5bfd-133">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="b5bfd-133">✔️ 3.1</span></span>        | <span data-ttu-id="b5bfd-134">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="b5bfd-134">❌ 5.0</span></span> |
| <span data-ttu-id="b5bfd-135">❌ 3.9</span><span class="sxs-lookup"><span data-stu-id="b5bfd-135">❌ 3.9</span></span>  | <span data-ttu-id="b5bfd-136">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="b5bfd-136">✔️ 2.1</span></span>        | <span data-ttu-id="b5bfd-137">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="b5bfd-137">✔️ 3.1</span></span>        | <span data-ttu-id="b5bfd-138">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="b5bfd-138">❌ 5.0</span></span> |
| <span data-ttu-id="b5bfd-139">❌ 3.8</span><span class="sxs-lookup"><span data-stu-id="b5bfd-139">❌ 3.8</span></span>  | <span data-ttu-id="b5bfd-140">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="b5bfd-140">✔️ 2.1</span></span>        | <span data-ttu-id="b5bfd-141">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="b5bfd-141">✔️ 3.1</span></span>        | <span data-ttu-id="b5bfd-142">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="b5bfd-142">❌ 5.0</span></span> |

<span data-ttu-id="b5bfd-143">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="b5bfd-143">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="b5bfd-144">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="b5bfd-144">The downloads for these still remain published:</span></span>

- <span data-ttu-id="b5bfd-145">3.0</span><span class="sxs-lookup"><span data-stu-id="b5bfd-145">3.0</span></span>
- <span data-ttu-id="b5bfd-146">2.2</span><span class="sxs-lookup"><span data-stu-id="b5bfd-146">2.2</span></span>
- <span data-ttu-id="b5bfd-147">2.0</span><span class="sxs-lookup"><span data-stu-id="b5bfd-147">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="b5bfd-148">相依性</span><span class="sxs-lookup"><span data-stu-id="b5bfd-148">Dependencies</span></span>

<span data-ttu-id="b5bfd-149">Alpine Linux 上的 .NET 需要安裝下列相依性：</span><span class="sxs-lookup"><span data-stu-id="b5bfd-149">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="b5bfd-150">icu-程式庫</span><span class="sxs-lookup"><span data-stu-id="b5bfd-150">icu-libs</span></span>
- <span data-ttu-id="b5bfd-151">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="b5bfd-151">krb5-libs</span></span>
- <span data-ttu-id="b5bfd-152">libgcc</span><span class="sxs-lookup"><span data-stu-id="b5bfd-152">libgcc</span></span>
- <span data-ttu-id="b5bfd-153">libintl</span><span class="sxs-lookup"><span data-stu-id="b5bfd-153">libintl</span></span>
- <span data-ttu-id="b5bfd-154">libssl1.0.0 1.1 (Alpine 3.9 或更高版本) </span><span class="sxs-lookup"><span data-stu-id="b5bfd-154">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="b5bfd-155">libssl1.0.0 1.0 (Alpine 3.8 或更低) </span><span class="sxs-lookup"><span data-stu-id="b5bfd-155">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="b5bfd-156">libstdc++</span><span class="sxs-lookup"><span data-stu-id="b5bfd-156">libstdc++</span></span>
- <span data-ttu-id="b5bfd-157">zlib</span><span class="sxs-lookup"><span data-stu-id="b5bfd-157">zlib</span></span>

## <a name="next-steps"></a><span data-ttu-id="b5bfd-158">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b5bfd-158">Next steps</span></span>

- [<span data-ttu-id="b5bfd-159">如何啟用 .NET CLI 的 TAB 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="b5bfd-159">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="b5bfd-160">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b5bfd-160">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
