---
title: 基礎類別庫的重大變更
description: 列出核心 .NET 程式庫中的重大變更。
ms.date: 07/27/2020
ms.openlocfilehash: 6a5cda5f5d21cf5349e4a3daaa0ed8b31196a78c
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720294"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="c2378-103">核心 .NET 程式庫的重大變更</span><span class="sxs-lookup"><span data-stu-id="c2378-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="c2378-104">核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般類型。</span><span class="sxs-lookup"><span data-stu-id="c2378-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="c2378-105">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="c2378-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="c2378-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="c2378-106">Breaking change</span></span> | <span data-ttu-id="c2378-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c2378-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="c2378-108">OSPlatform 屬性已重新命名或移除</span><span class="sxs-lookup"><span data-stu-id="c2378-108">OSPlatform attributes renamed or removed</span></span>](#osplatform-attributes-renamed-or-removed) | <span data-ttu-id="c2378-109">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-109">5.0</span></span> |
| [<span data-ttu-id="c2378-110">執行緒。中止已淘汰</span><span class="sxs-lookup"><span data-stu-id="c2378-110">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="c2378-111">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-111">5.0</span></span> |
| [<span data-ttu-id="c2378-112">ConsoleLoggerOptions 上的過時屬性</span><span class="sxs-lookup"><span data-stu-id="c2378-112">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="c2378-113">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-113">5.0</span></span> |
| [<span data-ttu-id="c2378-114">巢狀型別的硬體內部 IsSupported 檢查可能不同</span><span class="sxs-lookup"><span data-stu-id="c2378-114">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="c2378-115">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-115">5.0</span></span> |
| [<span data-ttu-id="c2378-116">參考元件中的參數名稱變更</span><span class="sxs-lookup"><span data-stu-id="c2378-116">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="c2378-117">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-117">5.0</span></span> |
| [<span data-ttu-id="c2378-118">在 Unix 上正確剖析非 ASCII 字元的 URI 路徑</span><span class="sxs-lookup"><span data-stu-id="c2378-118">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="c2378-119">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-119">5.0</span></span> |
| [<span data-ttu-id="c2378-120">Unix 上 UNC 路徑的 Uri 識別</span><span class="sxs-lookup"><span data-stu-id="c2378-120">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="c2378-121">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-121">5.0</span></span> |
| [<span data-ttu-id="c2378-122">環境。 OSVersion 傳回正確的作業系統版本</span><span class="sxs-lookup"><span data-stu-id="c2378-122">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="c2378-123">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-123">5.0</span></span> |
| [<span data-ttu-id="c2378-124">LINQ OrderBy 的複雜度。前 {OrDefault} 增加了</span><span class="sxs-lookup"><span data-stu-id="c2378-124">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="c2378-125">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-125">5.0</span></span> |
| [<span data-ttu-id="c2378-126">IntPtr 和 UIntPtr 實 >iformattable</span><span class="sxs-lookup"><span data-stu-id="c2378-126">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="c2378-127">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-127">5.0</span></span> |
| [<span data-ttu-id="c2378-128">PrincipalPermissionAttribute 已淘汰為錯誤</span><span class="sxs-lookup"><span data-stu-id="c2378-128">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="c2378-129">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-129">5.0</span></span> |
| [<span data-ttu-id="c2378-130">ASP.NET apps 已淘汰且禁止 BinaryFormatter 序列化方法</span><span class="sxs-lookup"><span data-stu-id="c2378-130">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="c2378-131">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-131">5.0</span></span> |
| [<span data-ttu-id="c2378-132">UTF-7 程式碼路徑已淘汰</span><span class="sxs-lookup"><span data-stu-id="c2378-132">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="c2378-133">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-133">5.0</span></span> |
| [<span data-ttu-id="c2378-134">Vector \<T> 一律會針對不支援的類型擲回 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="c2378-134">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="c2378-135">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-135">5.0</span></span> |
| [<span data-ttu-id="c2378-136">預設 ActivityIdFormat 是 W3C</span><span class="sxs-lookup"><span data-stu-id="c2378-136">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="c2378-137">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-137">5.0</span></span> |
| [<span data-ttu-id="c2378-138">Vector2. Lerp 和 Vector4 的行為變更。 Lerp</span><span class="sxs-lookup"><span data-stu-id="c2378-138">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="c2378-139">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-139">5.0</span></span> |
| [<span data-ttu-id="c2378-140">SSE 和 SSE2 CompareGreaterThan 方法會正確處理 NaN 輸入</span><span class="sxs-lookup"><span data-stu-id="c2378-140">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="c2378-141">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-141">5.0</span></span> |
| [<span data-ttu-id="c2378-142">如果實例已經存在，則 CreateCounterSetInstance 現在會擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="c2378-142">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="c2378-143">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-143">5.0</span></span> |
| [<span data-ttu-id="c2378-144">已移除 DotNet PlatformAbstractions 套件</span><span class="sxs-lookup"><span data-stu-id="c2378-144">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="c2378-145">5.0</span><span class="sxs-lookup"><span data-stu-id="c2378-145">5.0</span></span> |
| [<span data-ttu-id="c2378-146">報表版本現在會回報產品而非檔案版本的 Api</span><span class="sxs-lookup"><span data-stu-id="c2378-146">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="c2378-147">3.0</span><span class="sxs-lookup"><span data-stu-id="c2378-147">3.0</span></span> |
| [<span data-ttu-id="c2378-148">自訂 >encoderfallbackbuffer 實例無法遞迴地切換</span><span class="sxs-lookup"><span data-stu-id="c2378-148">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="c2378-149">3.0</span><span class="sxs-lookup"><span data-stu-id="c2378-149">3.0</span></span> |
| [<span data-ttu-id="c2378-150">浮點數格式化和剖析行為變更</span><span class="sxs-lookup"><span data-stu-id="c2378-150">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="c2378-151">3.0</span><span class="sxs-lookup"><span data-stu-id="c2378-151">3.0</span></span> |
| [<span data-ttu-id="c2378-152">浮點數剖析作業不再失敗或擲回 >overflowexception</span><span class="sxs-lookup"><span data-stu-id="c2378-152">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="c2378-153">3.0</span><span class="sxs-lookup"><span data-stu-id="c2378-153">3.0</span></span> |
| [<span data-ttu-id="c2378-154">System.componentmodel.invalidasynchronousstateexception 移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="c2378-154">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="c2378-155">3.0</span><span class="sxs-lookup"><span data-stu-id="c2378-155">3.0</span></span> |
| [<span data-ttu-id="c2378-156">取代格式不正確的 UTF-8 位元組序列遵循 Unicode 指導方針</span><span class="sxs-lookup"><span data-stu-id="c2378-156">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="c2378-157">3.0</span><span class="sxs-lookup"><span data-stu-id="c2378-157">3.0</span></span> |
| [<span data-ttu-id="c2378-158">TypeDescriptionProviderAttribute 移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="c2378-158">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="c2378-159">3.0</span><span class="sxs-lookup"><span data-stu-id="c2378-159">3.0</span></span> |
| [<span data-ttu-id="c2378-160">ZipArchiveEntry 不再以不一致的專案大小處理封存</span><span class="sxs-lookup"><span data-stu-id="c2378-160">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="c2378-161">3.0</span><span class="sxs-lookup"><span data-stu-id="c2378-161">3.0</span></span> |
| [<span data-ttu-id="c2378-162">FieldInfo 會針對靜態、僅限初始欄位擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="c2378-162">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="c2378-163">3.0</span><span class="sxs-lookup"><span data-stu-id="c2378-163">3.0</span></span> |
| [<span data-ttu-id="c2378-164">加入至內建結構類型的私用欄位</span><span class="sxs-lookup"><span data-stu-id="c2378-164">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="c2378-165">2.1</span><span class="sxs-lookup"><span data-stu-id="c2378-165">2.1</span></span> |
| [<span data-ttu-id="c2378-166">UseShellExecute 預設值的變更</span><span class="sxs-lookup"><span data-stu-id="c2378-166">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="c2378-167">2.1</span><span class="sxs-lookup"><span data-stu-id="c2378-167">2.1</span></span> |
| [<span data-ttu-id="c2378-168">MacOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="c2378-168">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="c2378-169">2.1</span><span class="sxs-lookup"><span data-stu-id="c2378-169">2.1</span></span> |
| [<span data-ttu-id="c2378-170">FileSystemInfo 擲回的 System.unauthorizedaccessexception。屬性</span><span class="sxs-lookup"><span data-stu-id="c2378-170">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="c2378-171">1.0</span><span class="sxs-lookup"><span data-stu-id="c2378-171">1.0</span></span> |
| [<span data-ttu-id="c2378-172">不支援處理損毀的進程狀態例外狀況</span><span class="sxs-lookup"><span data-stu-id="c2378-172">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="c2378-173">1.0</span><span class="sxs-lookup"><span data-stu-id="c2378-173">1.0</span></span> |
| [<span data-ttu-id="c2378-174">UriBuilder 屬性不再加上前置字元</span><span class="sxs-lookup"><span data-stu-id="c2378-174">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="c2378-175">1.0</span><span class="sxs-lookup"><span data-stu-id="c2378-175">1.0</span></span> |
| [<span data-ttu-id="c2378-176">StartInfo 會針對您未啟動的進程擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="c2378-176">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="c2378-177">1.0</span><span class="sxs-lookup"><span data-stu-id="c2378-177">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="c2378-178">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="c2378-178">.NET 5.0</span></span>

[!INCLUDE [os-platform-attributes-renamed](../../../includes/core-changes/corefx/5.0/os-platform-attributes-renamed.md)]

***

[!INCLUDE [thread-abort-obsolete](../../../includes/core-changes/corefx/5.0/thread-abort-obsolete.md)]

***

[!INCLUDE [obsolete-consoleloggeroptions-properties](../../../includes/core-changes/corefx/5.0/obsolete-consoleloggeroptions-properties.md)]

***

[!INCLUDE [hardware-instrinsics-issupported-checks](../../../includes/core-changes/corefx/5.0/hardware-instrinsics-issupported-checks.md)]

***

[!INCLUDE [reference-assembly-parameter-names](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names.md)]

***

[!INCLUDE [non-ascii-chars-in-uri-parsed-correctly](../../../includes/core-changes/corefx/5.0/non-ascii-chars-in-uri-parsed-correctly.md)]

***

[!INCLUDE [unc-path-recognition-unix](../../../includes/core-changes/corefx/5.0/unc-path-recognition-unix.md)]

***

[!INCLUDE [environment-osversion-returns-correct-version](../../../includes/core-changes/corefx/5.0/environment-osversion-returns-correct-version.md)]

***

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

## <a name="net-core-30"></a><span data-ttu-id="c2378-179">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2378-179">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="c2378-180">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c2378-180">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="c2378-181">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c2378-181">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
