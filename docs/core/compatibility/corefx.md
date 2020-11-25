---
title: .NET 程式庫的重大變更
description: 列出 .NET Core 1.0-3.0 版核心 .NET 程式庫中的重大變更。
ms.date: 07/27/2020
ms.openlocfilehash: 0f42429e44776fc70bb99ed3bdf346f0d5dbc9eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "96031981"
---
# <a name="core-net-libraries-breaking-changes-in-net-core-10-30"></a><span data-ttu-id="4b1b6-103">.NET Core 1.0-3.0 中的核心 .NET 程式庫重大變更</span><span class="sxs-lookup"><span data-stu-id="4b1b6-103">Core .NET libraries breaking changes in .NET Core 1.0-3.0</span></span>

<span data-ttu-id="4b1b6-104">核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般類型。</span><span class="sxs-lookup"><span data-stu-id="4b1b6-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="4b1b6-105">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="4b1b6-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="4b1b6-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="4b1b6-106">Breaking change</span></span> | <span data-ttu-id="4b1b6-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="4b1b6-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="4b1b6-108">報表版本現在會回報產品而非檔案版本的 Api</span><span class="sxs-lookup"><span data-stu-id="4b1b6-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="4b1b6-109">3.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-109">3.0</span></span> |
| [<span data-ttu-id="4b1b6-110">自訂 >encoderfallbackbuffer 實例無法遞迴地切換</span><span class="sxs-lookup"><span data-stu-id="4b1b6-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="4b1b6-111">3.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-111">3.0</span></span> |
| [<span data-ttu-id="4b1b6-112">浮點數格式化和剖析行為變更</span><span class="sxs-lookup"><span data-stu-id="4b1b6-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="4b1b6-113">3.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-113">3.0</span></span> |
| [<span data-ttu-id="4b1b6-114">浮點數剖析作業不再失敗或擲回 >overflowexception</span><span class="sxs-lookup"><span data-stu-id="4b1b6-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="4b1b6-115">3.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-115">3.0</span></span> |
| [<span data-ttu-id="4b1b6-116">System.componentmodel.invalidasynchronousstateexception 移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="4b1b6-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="4b1b6-117">3.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-117">3.0</span></span> |
| [<span data-ttu-id="4b1b6-118">取代格式不正確的 UTF-8 位元組序列遵循 Unicode 指導方針</span><span class="sxs-lookup"><span data-stu-id="4b1b6-118">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="4b1b6-119">3.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-119">3.0</span></span> |
| [<span data-ttu-id="4b1b6-120">TypeDescriptionProviderAttribute 移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="4b1b6-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="4b1b6-121">3.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-121">3.0</span></span> |
| [<span data-ttu-id="4b1b6-122">ZipArchiveEntry 不再以不一致的專案大小處理封存</span><span class="sxs-lookup"><span data-stu-id="4b1b6-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="4b1b6-123">3.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-123">3.0</span></span> |
| [<span data-ttu-id="4b1b6-124">FieldInfo 會針對靜態、僅限初始欄位擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="4b1b6-124">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="4b1b6-125">3.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-125">3.0</span></span> |
| [<span data-ttu-id="4b1b6-126">加入至內建結構類型的私用欄位</span><span class="sxs-lookup"><span data-stu-id="4b1b6-126">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="4b1b6-127">2.1</span><span class="sxs-lookup"><span data-stu-id="4b1b6-127">2.1</span></span> |
| [<span data-ttu-id="4b1b6-128">UseShellExecute 預設值的變更</span><span class="sxs-lookup"><span data-stu-id="4b1b6-128">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="4b1b6-129">2.1</span><span class="sxs-lookup"><span data-stu-id="4b1b6-129">2.1</span></span> |
| [<span data-ttu-id="4b1b6-130">MacOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="4b1b6-130">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="4b1b6-131">2.1</span><span class="sxs-lookup"><span data-stu-id="4b1b6-131">2.1</span></span> |
| [<span data-ttu-id="4b1b6-132">FileSystemInfo 擲回的 System.unauthorizedaccessexception。屬性</span><span class="sxs-lookup"><span data-stu-id="4b1b6-132">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="4b1b6-133">1.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-133">1.0</span></span> |
| [<span data-ttu-id="4b1b6-134">不支援處理損毀的進程狀態例外狀況</span><span class="sxs-lookup"><span data-stu-id="4b1b6-134">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="4b1b6-135">1.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-135">1.0</span></span> |
| [<span data-ttu-id="4b1b6-136">UriBuilder 屬性不再加上前置字元</span><span class="sxs-lookup"><span data-stu-id="4b1b6-136">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="4b1b6-137">1.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-137">1.0</span></span> |
| [<span data-ttu-id="4b1b6-138">StartInfo 會針對您未啟動的進程擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="4b1b6-138">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="4b1b6-139">1.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-139">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="4b1b6-140">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-140">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

<span data-ttu-id="4b1b6-141">\*\*_</span><span class="sxs-lookup"><span data-stu-id="4b1b6-141">\*\*_</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="4b1b6-142">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4b1b6-142">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a><span data-ttu-id="4b1b6-143">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="4b1b6-143">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

<span data-ttu-id="4b1b6-144">_\*\*</span><span class="sxs-lookup"><span data-stu-id="4b1b6-144">_\*\*</span></span>
