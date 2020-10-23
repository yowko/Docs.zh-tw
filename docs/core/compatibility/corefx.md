---
title: 基礎類別庫的重大變更
description: 列出核心 .NET 程式庫中的重大變更。
ms.date: 07/27/2020
ms.openlocfilehash: 900fd4e0e071f19aa286dec84632006870822f26
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434955"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="6c438-103">核心 .NET 程式庫的重大變更</span><span class="sxs-lookup"><span data-stu-id="6c438-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="6c438-104">核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般類型。</span><span class="sxs-lookup"><span data-stu-id="6c438-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="6c438-105">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="6c438-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="6c438-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="6c438-106">Breaking change</span></span> | <span data-ttu-id="6c438-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6c438-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="6c438-108">全域組件快取 Api 已淘汰</span><span class="sxs-lookup"><span data-stu-id="6c438-108">Global assembly cache APIs are obsolete</span></span>](#global-assembly-cache-apis-are-obsolete) | <span data-ttu-id="6c438-109">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-109">5.0</span></span> |
| [<span data-ttu-id="6c438-110">遠端 Api 已淘汰</span><span class="sxs-lookup"><span data-stu-id="6c438-110">Remoting APIs are obsolete</span></span>](#remoting-apis-are-obsolete) | <span data-ttu-id="6c438-111">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-111">5.0</span></span> |
| [<span data-ttu-id="6c438-112">大部分的代碼啟用安全性 Api 已淘汰</span><span class="sxs-lookup"><span data-stu-id="6c438-112">Most code access security APIs are obsolete</span></span>](#most-code-access-security-apis-are-obsolete) | <span data-ttu-id="6c438-113">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-113">5.0</span></span> |
| [<span data-ttu-id="6c438-114">使用非預設診斷識別碼的 API obsoletions</span><span class="sxs-lookup"><span data-stu-id="6c438-114">API obsoletions with non-default diagnostic IDs</span></span>](#api-obsoletions-with-non-default-diagnostic-ids) | <span data-ttu-id="6c438-115">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-115">5.0</span></span> |
| [<span data-ttu-id="6c438-116">FrameworkDescription 的值是 .NET 而不是 .NET Core</span><span class="sxs-lookup"><span data-stu-id="6c438-116">FrameworkDescription's value is .NET instead of .NET Core</span></span>](#frameworkdescriptions-value-is-net-instead-of-net-core) | <span data-ttu-id="6c438-117">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-117">5.0</span></span> |
| [<span data-ttu-id="6c438-118">單一檔案發佈格式的元件相關 API 行為變更</span><span class="sxs-lookup"><span data-stu-id="6c438-118">Assembly-related API behavior changes for single-file publishing format</span></span>](#assembly-related-api-behavior-changes-for-single-file-publishing-format) | <span data-ttu-id="6c438-119">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-119">5.0</span></span> |
| [<span data-ttu-id="6c438-120">活動中標記的順序。標記會反轉</span><span class="sxs-lookup"><span data-stu-id="6c438-120">Order of tags in Activity.Tags is reversed</span></span>](#order-of-tags-in-activitytags-is-reversed) | <span data-ttu-id="6c438-121">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-121">5.0</span></span> |
| [<span data-ttu-id="6c438-122">RC1 中的參數名稱已變更</span><span class="sxs-lookup"><span data-stu-id="6c438-122">Parameter names changed in RC1</span></span>](#parameter-names-changed-in-rc1) | <span data-ttu-id="6c438-123">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-123">5.0</span></span> |
| [<span data-ttu-id="6c438-124">OSPlatform 屬性已重新命名或移除</span><span class="sxs-lookup"><span data-stu-id="6c438-124">OSPlatform attributes renamed or removed</span></span>](#osplatform-attributes-renamed-or-removed) | <span data-ttu-id="6c438-125">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-125">5.0</span></span> |
| [<span data-ttu-id="6c438-126">執行緒。中止已淘汰</span><span class="sxs-lookup"><span data-stu-id="6c438-126">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="6c438-127">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-127">5.0</span></span> |
| [<span data-ttu-id="6c438-128">ConsoleLoggerOptions 上的過時屬性</span><span class="sxs-lookup"><span data-stu-id="6c438-128">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="6c438-129">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-129">5.0</span></span> |
| [<span data-ttu-id="6c438-130">巢狀型別的硬體內部 IsSupported 檢查可能不同</span><span class="sxs-lookup"><span data-stu-id="6c438-130">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="6c438-131">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-131">5.0</span></span> |
| [<span data-ttu-id="6c438-132">參考元件中的參數名稱變更</span><span class="sxs-lookup"><span data-stu-id="6c438-132">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="6c438-133">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-133">5.0</span></span> |
| [<span data-ttu-id="6c438-134">在 Unix 上正確剖析非 ASCII 字元的 URI 路徑</span><span class="sxs-lookup"><span data-stu-id="6c438-134">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="6c438-135">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-135">5.0</span></span> |
| [<span data-ttu-id="6c438-136">Unix 上 UNC 路徑的 Uri 識別</span><span class="sxs-lookup"><span data-stu-id="6c438-136">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="6c438-137">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-137">5.0</span></span> |
| [<span data-ttu-id="6c438-138">環境。 OSVersion 傳回正確的作業系統版本</span><span class="sxs-lookup"><span data-stu-id="6c438-138">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="6c438-139">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-139">5.0</span></span> |
| [<span data-ttu-id="6c438-140">LINQ OrderBy 的複雜度。前 {OrDefault} 增加了</span><span class="sxs-lookup"><span data-stu-id="6c438-140">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="6c438-141">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-141">5.0</span></span> |
| [<span data-ttu-id="6c438-142">IntPtr 和 UIntPtr 實 >iformattable</span><span class="sxs-lookup"><span data-stu-id="6c438-142">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="6c438-143">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-143">5.0</span></span> |
| [<span data-ttu-id="6c438-144">PrincipalPermissionAttribute 已淘汰為錯誤</span><span class="sxs-lookup"><span data-stu-id="6c438-144">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="6c438-145">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-145">5.0</span></span> |
| [<span data-ttu-id="6c438-146">ASP.NET apps 已淘汰且禁止 BinaryFormatter 序列化方法</span><span class="sxs-lookup"><span data-stu-id="6c438-146">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="6c438-147">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-147">5.0</span></span> |
| [<span data-ttu-id="6c438-148">UTF-7 程式碼路徑已淘汰</span><span class="sxs-lookup"><span data-stu-id="6c438-148">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="6c438-149">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-149">5.0</span></span> |
| [<span data-ttu-id="6c438-150">Vector \<T> 一律會針對不支援的類型擲回 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="6c438-150">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="6c438-151">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-151">5.0</span></span> |
| [<span data-ttu-id="6c438-152">預設 ActivityIdFormat 是 W3C</span><span class="sxs-lookup"><span data-stu-id="6c438-152">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="6c438-153">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-153">5.0</span></span> |
| [<span data-ttu-id="6c438-154">Vector2. Lerp 和 Vector4 的行為變更。 Lerp</span><span class="sxs-lookup"><span data-stu-id="6c438-154">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="6c438-155">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-155">5.0</span></span> |
| [<span data-ttu-id="6c438-156">SSE 和 SSE2 CompareGreaterThan 方法會正確處理 NaN 輸入</span><span class="sxs-lookup"><span data-stu-id="6c438-156">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="6c438-157">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-157">5.0</span></span> |
| [<span data-ttu-id="6c438-158">如果實例已經存在，則 CreateCounterSetInstance 現在會擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="6c438-158">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="6c438-159">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-159">5.0</span></span> |
| [<span data-ttu-id="6c438-160">已移除 DotNet PlatformAbstractions 套件</span><span class="sxs-lookup"><span data-stu-id="6c438-160">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="6c438-161">5.0</span><span class="sxs-lookup"><span data-stu-id="6c438-161">5.0</span></span> |
| [<span data-ttu-id="6c438-162">報表版本現在會回報產品而非檔案版本的 Api</span><span class="sxs-lookup"><span data-stu-id="6c438-162">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="6c438-163">3.0</span><span class="sxs-lookup"><span data-stu-id="6c438-163">3.0</span></span> |
| [<span data-ttu-id="6c438-164">自訂 >encoderfallbackbuffer 實例無法遞迴地切換</span><span class="sxs-lookup"><span data-stu-id="6c438-164">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="6c438-165">3.0</span><span class="sxs-lookup"><span data-stu-id="6c438-165">3.0</span></span> |
| [<span data-ttu-id="6c438-166">浮點數格式化和剖析行為變更</span><span class="sxs-lookup"><span data-stu-id="6c438-166">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="6c438-167">3.0</span><span class="sxs-lookup"><span data-stu-id="6c438-167">3.0</span></span> |
| [<span data-ttu-id="6c438-168">浮點數剖析作業不再失敗或擲回 >overflowexception</span><span class="sxs-lookup"><span data-stu-id="6c438-168">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="6c438-169">3.0</span><span class="sxs-lookup"><span data-stu-id="6c438-169">3.0</span></span> |
| [<span data-ttu-id="6c438-170">System.componentmodel.invalidasynchronousstateexception 移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="6c438-170">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="6c438-171">3.0</span><span class="sxs-lookup"><span data-stu-id="6c438-171">3.0</span></span> |
| [<span data-ttu-id="6c438-172">取代格式不正確的 UTF-8 位元組序列遵循 Unicode 指導方針</span><span class="sxs-lookup"><span data-stu-id="6c438-172">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="6c438-173">3.0</span><span class="sxs-lookup"><span data-stu-id="6c438-173">3.0</span></span> |
| [<span data-ttu-id="6c438-174">TypeDescriptionProviderAttribute 移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="6c438-174">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="6c438-175">3.0</span><span class="sxs-lookup"><span data-stu-id="6c438-175">3.0</span></span> |
| [<span data-ttu-id="6c438-176">ZipArchiveEntry 不再以不一致的專案大小處理封存</span><span class="sxs-lookup"><span data-stu-id="6c438-176">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="6c438-177">3.0</span><span class="sxs-lookup"><span data-stu-id="6c438-177">3.0</span></span> |
| [<span data-ttu-id="6c438-178">FieldInfo 會針對靜態、僅限初始欄位擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="6c438-178">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="6c438-179">3.0</span><span class="sxs-lookup"><span data-stu-id="6c438-179">3.0</span></span> |
| [<span data-ttu-id="6c438-180">加入至內建結構類型的私用欄位</span><span class="sxs-lookup"><span data-stu-id="6c438-180">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="6c438-181">2.1</span><span class="sxs-lookup"><span data-stu-id="6c438-181">2.1</span></span> |
| [<span data-ttu-id="6c438-182">UseShellExecute 預設值的變更</span><span class="sxs-lookup"><span data-stu-id="6c438-182">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="6c438-183">2.1</span><span class="sxs-lookup"><span data-stu-id="6c438-183">2.1</span></span> |
| [<span data-ttu-id="6c438-184">MacOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="6c438-184">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="6c438-185">2.1</span><span class="sxs-lookup"><span data-stu-id="6c438-185">2.1</span></span> |
| [<span data-ttu-id="6c438-186">FileSystemInfo 擲回的 System.unauthorizedaccessexception。屬性</span><span class="sxs-lookup"><span data-stu-id="6c438-186">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="6c438-187">1.0</span><span class="sxs-lookup"><span data-stu-id="6c438-187">1.0</span></span> |
| [<span data-ttu-id="6c438-188">不支援處理損毀的進程狀態例外狀況</span><span class="sxs-lookup"><span data-stu-id="6c438-188">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="6c438-189">1.0</span><span class="sxs-lookup"><span data-stu-id="6c438-189">1.0</span></span> |
| [<span data-ttu-id="6c438-190">UriBuilder 屬性不再加上前置字元</span><span class="sxs-lookup"><span data-stu-id="6c438-190">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="6c438-191">1.0</span><span class="sxs-lookup"><span data-stu-id="6c438-191">1.0</span></span> |
| [<span data-ttu-id="6c438-192">StartInfo 會針對您未啟動的進程擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="6c438-192">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="6c438-193">1.0</span><span class="sxs-lookup"><span data-stu-id="6c438-193">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="6c438-194">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="6c438-194">.NET 5.0</span></span>

[!INCLUDE [remoting-apis-obsolete](../../../includes/core-changes/corefx/5.0/remoting-apis-obsolete.md)]

***

[!INCLUDE [globalassemblycache-property-obsolete](../../../includes/core-changes/corefx/5.0/global-assembly-cache-apis-obsolete.md)]

<span data-ttu-id="6c438-195">\*\*_</span><span class="sxs-lookup"><span data-stu-id="6c438-195">\*\*_</span></span>

[!INCLUDE [code-access-security-apis-obsolete](../../../includes/core-changes/corefx/5.0/code-access-security-apis-obsolete.md)]

_*_

[!INCLUDE [obsolete-apis-with-custom-diagnostics](../../../includes/core-changes/corefx/5.0/obsolete-apis-with-custom-diagnostics.md)]

_*_

[!INCLUDE [frameworkdescription-returns-net-not-net-core](../../../includes/core-changes/corefx/5.0/frameworkdescription-returns-net-not-net-core.md)]

_*_

[!INCLUDE [assembly-api-behavior-changes-for-single-file-publish](../../../includes/core-changes/corefx/5.0/assembly-api-behavior-changes-for-single-file-publish.md)]

_*_

[!INCLUDE [reverse-order-of-tags-in-activity-property](../../../includes/core-changes/corefx/5.0/reverse-order-of-tags-in-activity-property.md)]

_*_

[!INCLUDE [reference-assembly-parameter-names-rc1](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names-rc1.md)]

_*_

[!INCLUDE [os-platform-attributes-renamed](../../../includes/core-changes/corefx/5.0/os-platform-attributes-renamed.md)]

_*_

[!INCLUDE [thread-abort-obsolete](../../../includes/core-changes/corefx/5.0/thread-abort-obsolete.md)]

_*_

[!INCLUDE [obsolete-consoleloggeroptions-properties](../../../includes/core-changes/corefx/5.0/obsolete-consoleloggeroptions-properties.md)]

_*_

[!INCLUDE [hardware-instrinsics-issupported-checks](../../../includes/core-changes/corefx/5.0/hardware-instrinsics-issupported-checks.md)]

_*_

[!INCLUDE [reference-assembly-parameter-names](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names.md)]

_*_

[!INCLUDE [non-ascii-chars-in-uri-parsed-correctly](../../../includes/core-changes/corefx/5.0/non-ascii-chars-in-uri-parsed-correctly.md)]

_*_

[!INCLUDE [unc-path-recognition-unix](../../../includes/core-changes/corefx/5.0/unc-path-recognition-unix.md)]

_*_

[!INCLUDE [environment-osversion-returns-correct-version](../../../includes/core-changes/corefx/5.0/environment-osversion-returns-correct-version.md)]

_*_

[!INCLUDE [orderby-firstordefault-complexity-increase](../../../includes/core-changes/corefx/5.0/orderby-firstordefault-complexity-increase.md)]

_*_

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

_*_

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

_*_

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

_*_

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

_*_

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

_*_

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

_*_

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

_*_

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

_*_

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

_*_

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

_*_

## <a name="net-core-30"></a><span data-ttu-id="6c438-196">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6c438-196">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

_*_

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

## <a name="net-core-21"></a><span data-ttu-id="6c438-197">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6c438-197">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a><span data-ttu-id="6c438-198">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="6c438-198">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

<span data-ttu-id="6c438-199">_\*\*</span><span class="sxs-lookup"><span data-stu-id="6c438-199">_\*\*</span></span>
