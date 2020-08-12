---
title: 基類庫的重大變更
description: 列出核心 .NET 程式庫中的重大變更。
ms.date: 07/27/2020
ms.openlocfilehash: c8eb5ec7d2bb1879a38a18337463230c7b731d29
ms.sourcegitcommit: d3c09791297f0edc468a4849a5f11ef62e0e90fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2020
ms.locfileid: "88137484"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="9af08-103">核心 .NET 程式庫的重大變更</span><span class="sxs-lookup"><span data-stu-id="9af08-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="9af08-104">核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般型別。</span><span class="sxs-lookup"><span data-stu-id="9af08-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="9af08-105">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="9af08-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="9af08-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="9af08-106">Breaking change</span></span> | <span data-ttu-id="9af08-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9af08-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="9af08-108">LINQ OrderBy 的複雜性。第一個 {OrDefault} 已增加</span><span class="sxs-lookup"><span data-stu-id="9af08-108">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="9af08-109">5.0</span><span class="sxs-lookup"><span data-stu-id="9af08-109">5.0</span></span> |
| [<span data-ttu-id="9af08-110">IntPtr 和 UIntPtr 執行 IFormattable</span><span class="sxs-lookup"><span data-stu-id="9af08-110">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="9af08-111">5.0</span><span class="sxs-lookup"><span data-stu-id="9af08-111">5.0</span></span> |
| [<span data-ttu-id="9af08-112">PrincipalPermissionAttribute 已淘汰為錯誤</span><span class="sxs-lookup"><span data-stu-id="9af08-112">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="9af08-113">5.0</span><span class="sxs-lookup"><span data-stu-id="9af08-113">5.0</span></span> |
| [<span data-ttu-id="9af08-114">ASP.NET 應用程式中的 BinaryFormatter 序列化方法已過時且禁止</span><span class="sxs-lookup"><span data-stu-id="9af08-114">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="9af08-115">5.0</span><span class="sxs-lookup"><span data-stu-id="9af08-115">5.0</span></span> |
| [<span data-ttu-id="9af08-116">UTF-7 程式碼路徑已過時</span><span class="sxs-lookup"><span data-stu-id="9af08-116">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="9af08-117">5.0</span><span class="sxs-lookup"><span data-stu-id="9af08-117">5.0</span></span> |
| [<span data-ttu-id="9af08-118">Vector 一律會擲回 \<T> 不支援之類型的 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="9af08-118">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="9af08-119">5.0</span><span class="sxs-lookup"><span data-stu-id="9af08-119">5.0</span></span> |
| [<span data-ttu-id="9af08-120">預設 ActivityIdFormat 為 W3C</span><span class="sxs-lookup"><span data-stu-id="9af08-120">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="9af08-121">5.0</span><span class="sxs-lookup"><span data-stu-id="9af08-121">5.0</span></span> |
| [<span data-ttu-id="9af08-122">Vector2 的行為變更。 Lerp 和 Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="9af08-122">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="9af08-123">5.0</span><span class="sxs-lookup"><span data-stu-id="9af08-123">5.0</span></span> |
| [<span data-ttu-id="9af08-124">SSE 和 SSE2 CompareGreaterThan 方法會適當地處理 NaN 輸入</span><span class="sxs-lookup"><span data-stu-id="9af08-124">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="9af08-125">5.0</span><span class="sxs-lookup"><span data-stu-id="9af08-125">5.0</span></span> |
| [<span data-ttu-id="9af08-126">如果實例已經存在，CreateCounterSetInstance 現在會擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="9af08-126">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="9af08-127">5.0</span><span class="sxs-lookup"><span data-stu-id="9af08-127">5.0</span></span> |
| [<span data-ttu-id="9af08-128">已移除 DotNet PlatformAbstractions 套件</span><span class="sxs-lookup"><span data-stu-id="9af08-128">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="9af08-129">5.0</span><span class="sxs-lookup"><span data-stu-id="9af08-129">5.0</span></span> |
| [<span data-ttu-id="9af08-130">報告版本的 Api 現在會報告產品，而不是檔案版本</span><span class="sxs-lookup"><span data-stu-id="9af08-130">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="9af08-131">3.0</span><span class="sxs-lookup"><span data-stu-id="9af08-131">3.0</span></span> |
| [<span data-ttu-id="9af08-132">自訂 EncoderFallbackBuffer 實例無法遞迴切換</span><span class="sxs-lookup"><span data-stu-id="9af08-132">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="9af08-133">3.0</span><span class="sxs-lookup"><span data-stu-id="9af08-133">3.0</span></span> |
| [<span data-ttu-id="9af08-134">浮點格式設定和剖析行為變更</span><span class="sxs-lookup"><span data-stu-id="9af08-134">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="9af08-135">3.0</span><span class="sxs-lookup"><span data-stu-id="9af08-135">3.0</span></span> |
| [<span data-ttu-id="9af08-136">浮點剖析作業不再失敗或擲回 OverflowException</span><span class="sxs-lookup"><span data-stu-id="9af08-136">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="9af08-137">3.0</span><span class="sxs-lookup"><span data-stu-id="9af08-137">3.0</span></span> |
| [<span data-ttu-id="9af08-138">System.componentmodel.invalidasynchronousstateexception 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="9af08-138">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="9af08-139">3.0</span><span class="sxs-lookup"><span data-stu-id="9af08-139">3.0</span></span> |
| [<span data-ttu-id="9af08-140">取代格式不正確的 UTF-8 位元組序列遵循 Unicode 方針</span><span class="sxs-lookup"><span data-stu-id="9af08-140">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="9af08-141">3.0</span><span class="sxs-lookup"><span data-stu-id="9af08-141">3.0</span></span> |
| [<span data-ttu-id="9af08-142">TypeDescriptionProviderAttribute 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="9af08-142">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="9af08-143">3.0</span><span class="sxs-lookup"><span data-stu-id="9af08-143">3.0</span></span> |
| [<span data-ttu-id="9af08-144">Ziparchiveentry 中不再處理具有不一致專案大小的封存</span><span class="sxs-lookup"><span data-stu-id="9af08-144">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="9af08-145">3.0</span><span class="sxs-lookup"><span data-stu-id="9af08-145">3.0</span></span> |
| [<span data-ttu-id="9af08-146">FieldInfo。 SetValue 會擲回靜態、僅限初始欄位的例外狀況</span><span class="sxs-lookup"><span data-stu-id="9af08-146">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="9af08-147">3.0</span><span class="sxs-lookup"><span data-stu-id="9af08-147">3.0</span></span> |
| [<span data-ttu-id="9af08-148">加入至內建結構類型的私用欄位</span><span class="sxs-lookup"><span data-stu-id="9af08-148">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="9af08-149">2.1</span><span class="sxs-lookup"><span data-stu-id="9af08-149">2.1</span></span> |
| [<span data-ttu-id="9af08-150">預設值為 UseShellExecute 的變更</span><span class="sxs-lookup"><span data-stu-id="9af08-150">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="9af08-151">2.1</span><span class="sxs-lookup"><span data-stu-id="9af08-151">2.1</span></span> |
| [<span data-ttu-id="9af08-152">MacOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="9af08-152">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="9af08-153">2.1</span><span class="sxs-lookup"><span data-stu-id="9af08-153">2.1</span></span> |
| [<span data-ttu-id="9af08-154">FileSystemInfo 擲回的 System.unauthorizedaccessexception</span><span class="sxs-lookup"><span data-stu-id="9af08-154">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="9af08-155">1.0</span><span class="sxs-lookup"><span data-stu-id="9af08-155">1.0</span></span> |
| [<span data-ttu-id="9af08-156">不支援處理損毀的進程狀態例外狀況</span><span class="sxs-lookup"><span data-stu-id="9af08-156">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="9af08-157">1.0</span><span class="sxs-lookup"><span data-stu-id="9af08-157">1.0</span></span> |
| [<span data-ttu-id="9af08-158">UriBuilder 屬性不再前面加上前置字元</span><span class="sxs-lookup"><span data-stu-id="9af08-158">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="9af08-159">1.0</span><span class="sxs-lookup"><span data-stu-id="9af08-159">1.0</span></span> |
| [<span data-ttu-id="9af08-160">StartInfo 會針對您未啟動的進程擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="9af08-160">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="9af08-161">1.0</span><span class="sxs-lookup"><span data-stu-id="9af08-161">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="9af08-162">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="9af08-162">.NET 5.0</span></span>

[!INCLUDE [orderby-firstordefault-complexity-increase](../../../includes/core-changes/corefx/5.0/orderby-firstordefault-complexity-increase.md)]

***

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

***

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

***

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

***

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

***

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

***

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="9af08-163">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9af08-163">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="9af08-164">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9af08-164">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="9af08-165">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="9af08-165">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
