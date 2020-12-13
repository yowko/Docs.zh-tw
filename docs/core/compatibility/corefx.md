---
title: .NET 程式庫的重大變更
description: 列出 .NET Core 1.0-3.0 版核心 .NET 程式庫中的重大變更。
ms.date: 07/27/2020
ms.openlocfilehash: 092ff36a5e07c9e226fe2a67d5e7cfd391e9d16b
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366874"
---
# <a name="core-net-libraries-breaking-changes-in-net-core-10-30"></a><span data-ttu-id="06525-103">.NET Core 1.0-3.0 中的核心 .NET 程式庫重大變更</span><span class="sxs-lookup"><span data-stu-id="06525-103">Core .NET libraries breaking changes in .NET Core 1.0-3.0</span></span>

<span data-ttu-id="06525-104">核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般類型。</span><span class="sxs-lookup"><span data-stu-id="06525-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="06525-105">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="06525-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="06525-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="06525-106">Breaking change</span></span> | <span data-ttu-id="06525-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="06525-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="06525-108">將 GroupCollection 傳遞至採用 IEnumerable 的擴充方法需要去除混淆 \<T></span><span class="sxs-lookup"><span data-stu-id="06525-108">Passing GroupCollection to extension methods taking IEnumerable\<T> requires disambiguation</span></span>](#passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation) | <span data-ttu-id="06525-109">3.0</span><span class="sxs-lookup"><span data-stu-id="06525-109">3.0</span></span> |
| [<span data-ttu-id="06525-110">報表版本現在會回報產品而非檔案版本的 Api</span><span class="sxs-lookup"><span data-stu-id="06525-110">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="06525-111">3.0</span><span class="sxs-lookup"><span data-stu-id="06525-111">3.0</span></span> |
| [<span data-ttu-id="06525-112">自訂 >encoderfallbackbuffer 實例無法遞迴地切換</span><span class="sxs-lookup"><span data-stu-id="06525-112">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="06525-113">3.0</span><span class="sxs-lookup"><span data-stu-id="06525-113">3.0</span></span> |
| [<span data-ttu-id="06525-114">浮點數格式化和剖析行為變更</span><span class="sxs-lookup"><span data-stu-id="06525-114">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="06525-115">3.0</span><span class="sxs-lookup"><span data-stu-id="06525-115">3.0</span></span> |
| [<span data-ttu-id="06525-116">浮點數剖析作業不再失敗或擲回 >overflowexception</span><span class="sxs-lookup"><span data-stu-id="06525-116">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="06525-117">3.0</span><span class="sxs-lookup"><span data-stu-id="06525-117">3.0</span></span> |
| [<span data-ttu-id="06525-118">System.componentmodel.invalidasynchronousstateexception 移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="06525-118">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="06525-119">3.0</span><span class="sxs-lookup"><span data-stu-id="06525-119">3.0</span></span> |
| [<span data-ttu-id="06525-120">取代格式不正確的 UTF-8 位元組序列遵循 Unicode 指導方針</span><span class="sxs-lookup"><span data-stu-id="06525-120">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="06525-121">3.0</span><span class="sxs-lookup"><span data-stu-id="06525-121">3.0</span></span> |
| [<span data-ttu-id="06525-122">TypeDescriptionProviderAttribute 移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="06525-122">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="06525-123">3.0</span><span class="sxs-lookup"><span data-stu-id="06525-123">3.0</span></span> |
| [<span data-ttu-id="06525-124">ZipArchiveEntry 不再以不一致的專案大小處理封存</span><span class="sxs-lookup"><span data-stu-id="06525-124">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="06525-125">3.0</span><span class="sxs-lookup"><span data-stu-id="06525-125">3.0</span></span> |
| [<span data-ttu-id="06525-126">FieldInfo 會針對靜態、僅限初始欄位擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="06525-126">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="06525-127">3.0</span><span class="sxs-lookup"><span data-stu-id="06525-127">3.0</span></span> |
| [<span data-ttu-id="06525-128">加入至內建結構類型的私用欄位</span><span class="sxs-lookup"><span data-stu-id="06525-128">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="06525-129">2.1</span><span class="sxs-lookup"><span data-stu-id="06525-129">2.1</span></span> |
| [<span data-ttu-id="06525-130">UseShellExecute 預設值的變更</span><span class="sxs-lookup"><span data-stu-id="06525-130">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="06525-131">2.1</span><span class="sxs-lookup"><span data-stu-id="06525-131">2.1</span></span> |
| [<span data-ttu-id="06525-132">MacOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="06525-132">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="06525-133">2.1</span><span class="sxs-lookup"><span data-stu-id="06525-133">2.1</span></span> |
| [<span data-ttu-id="06525-134">FileSystemInfo 擲回的 System.unauthorizedaccessexception。屬性</span><span class="sxs-lookup"><span data-stu-id="06525-134">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="06525-135">1.0</span><span class="sxs-lookup"><span data-stu-id="06525-135">1.0</span></span> |
| [<span data-ttu-id="06525-136">不支援處理損毀的進程狀態例外狀況</span><span class="sxs-lookup"><span data-stu-id="06525-136">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="06525-137">1.0</span><span class="sxs-lookup"><span data-stu-id="06525-137">1.0</span></span> |
| [<span data-ttu-id="06525-138">UriBuilder 屬性不再加上前置字元</span><span class="sxs-lookup"><span data-stu-id="06525-138">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="06525-139">1.0</span><span class="sxs-lookup"><span data-stu-id="06525-139">1.0</span></span> |
| [<span data-ttu-id="06525-140">StartInfo 會針對您未啟動的進程擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="06525-140">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="06525-141">1.0</span><span class="sxs-lookup"><span data-stu-id="06525-141">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="06525-142">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="06525-142">.NET Core 3.0</span></span>

[!INCLUDE [disambiguate-generic-type-for-groupcollection](../../../includes/core-changes/corefx/3.0/disambiguate-generic-type-for-groupcollection.md)]

***

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

<span data-ttu-id="06525-143">\*\*_</span><span class="sxs-lookup"><span data-stu-id="06525-143">\*\*_</span></span>

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

_*_

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

_*_

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

_*_

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

_*_

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

_*_

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

_*_

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

_*_

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

_*_

## <a name="net-core-21"></a><span data-ttu-id="06525-144">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="06525-144">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a><span data-ttu-id="06525-145">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="06525-145">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

<span data-ttu-id="06525-146">_\*\*</span><span class="sxs-lookup"><span data-stu-id="06525-146">_\*\*</span></span>
