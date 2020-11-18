---
title: 基礎類別庫的重大變更
description: 列出核心 .NET 程式庫中的重大變更。
ms.date: 07/27/2020
ms.openlocfilehash: 8ea1cd995484c2930c8a9c2eb4c7419be57cf9c0
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440169"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="8b1be-103">核心 .NET 程式庫的重大變更</span><span class="sxs-lookup"><span data-stu-id="8b1be-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="8b1be-104">核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般類型。</span><span class="sxs-lookup"><span data-stu-id="8b1be-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="8b1be-105">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="8b1be-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="8b1be-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="8b1be-106">Breaking change</span></span> | <span data-ttu-id="8b1be-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="8b1be-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="8b1be-108">LastIndexOf 已改善空白搜尋字串的處理</span><span class="sxs-lookup"><span data-stu-id="8b1be-108">LastIndexOf has improved handling of empty search strings</span></span>](#lastindexof-has-improved-handling-of-empty-search-strings) | <span data-ttu-id="8b1be-109">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-109">5.0</span></span> |
| [<span data-ttu-id="8b1be-110">全域組件快取 Api 已淘汰</span><span class="sxs-lookup"><span data-stu-id="8b1be-110">Global assembly cache APIs are obsolete</span></span>](#global-assembly-cache-apis-are-obsolete) | <span data-ttu-id="8b1be-111">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-111">5.0</span></span> |
| [<span data-ttu-id="8b1be-112">遠端 Api 已淘汰</span><span class="sxs-lookup"><span data-stu-id="8b1be-112">Remoting APIs are obsolete</span></span>](#remoting-apis-are-obsolete) | <span data-ttu-id="8b1be-113">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-113">5.0</span></span> |
| [<span data-ttu-id="8b1be-114">大部分的代碼啟用安全性 Api 已淘汰</span><span class="sxs-lookup"><span data-stu-id="8b1be-114">Most code access security APIs are obsolete</span></span>](#most-code-access-security-apis-are-obsolete) | <span data-ttu-id="8b1be-115">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-115">5.0</span></span> |
| [<span data-ttu-id="8b1be-116">使用非預設診斷識別碼的 API obsoletions</span><span class="sxs-lookup"><span data-stu-id="8b1be-116">API obsoletions with non-default diagnostic IDs</span></span>](#api-obsoletions-with-non-default-diagnostic-ids) | <span data-ttu-id="8b1be-117">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-117">5.0</span></span> |
| [<span data-ttu-id="8b1be-118">FrameworkDescription 的值是 .NET 而不是 .NET Core</span><span class="sxs-lookup"><span data-stu-id="8b1be-118">FrameworkDescription's value is .NET instead of .NET Core</span></span>](#frameworkdescriptions-value-is-net-instead-of-net-core) | <span data-ttu-id="8b1be-119">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-119">5.0</span></span> |
| [<span data-ttu-id="8b1be-120">單一檔案發佈格式的元件相關 API 行為變更</span><span class="sxs-lookup"><span data-stu-id="8b1be-120">Assembly-related API behavior changes for single-file publishing format</span></span>](#assembly-related-api-behavior-changes-for-single-file-publishing-format) | <span data-ttu-id="8b1be-121">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-121">5.0</span></span> |
| [<span data-ttu-id="8b1be-122">活動中標記的順序。標記會反轉</span><span class="sxs-lookup"><span data-stu-id="8b1be-122">Order of tags in Activity.Tags is reversed</span></span>](#order-of-tags-in-activitytags-is-reversed) | <span data-ttu-id="8b1be-123">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-123">5.0</span></span> |
| [<span data-ttu-id="8b1be-124">RC1 中的參數名稱已變更</span><span class="sxs-lookup"><span data-stu-id="8b1be-124">Parameter names changed in RC1</span></span>](#parameter-names-changed-in-rc1) | <span data-ttu-id="8b1be-125">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-125">5.0</span></span> |
| [<span data-ttu-id="8b1be-126">OSPlatform 屬性已重新命名或移除</span><span class="sxs-lookup"><span data-stu-id="8b1be-126">OSPlatform attributes renamed or removed</span></span>](#osplatform-attributes-renamed-or-removed) | <span data-ttu-id="8b1be-127">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-127">5.0</span></span> |
| [<span data-ttu-id="8b1be-128">執行緒。中止已淘汰</span><span class="sxs-lookup"><span data-stu-id="8b1be-128">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="8b1be-129">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-129">5.0</span></span> |
| [<span data-ttu-id="8b1be-130">ConsoleLoggerOptions 上的過時屬性</span><span class="sxs-lookup"><span data-stu-id="8b1be-130">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="8b1be-131">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-131">5.0</span></span> |
| [<span data-ttu-id="8b1be-132">巢狀型別的硬體內部 IsSupported 檢查可能不同</span><span class="sxs-lookup"><span data-stu-id="8b1be-132">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="8b1be-133">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-133">5.0</span></span> |
| [<span data-ttu-id="8b1be-134">參考元件中的參數名稱變更</span><span class="sxs-lookup"><span data-stu-id="8b1be-134">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="8b1be-135">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-135">5.0</span></span> |
| [<span data-ttu-id="8b1be-136">在 Unix 上正確剖析非 ASCII 字元的 URI 路徑</span><span class="sxs-lookup"><span data-stu-id="8b1be-136">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="8b1be-137">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-137">5.0</span></span> |
| [<span data-ttu-id="8b1be-138">Unix 上 UNC 路徑的 Uri 識別</span><span class="sxs-lookup"><span data-stu-id="8b1be-138">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="8b1be-139">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-139">5.0</span></span> |
| [<span data-ttu-id="8b1be-140">環境。 OSVersion 傳回正確的作業系統版本</span><span class="sxs-lookup"><span data-stu-id="8b1be-140">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="8b1be-141">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-141">5.0</span></span> |
| [<span data-ttu-id="8b1be-142">LINQ OrderBy 的複雜度。前 {OrDefault} 增加了</span><span class="sxs-lookup"><span data-stu-id="8b1be-142">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="8b1be-143">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-143">5.0</span></span> |
| [<span data-ttu-id="8b1be-144">IntPtr 和 UIntPtr 實 >iformattable</span><span class="sxs-lookup"><span data-stu-id="8b1be-144">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="8b1be-145">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-145">5.0</span></span> |
| [<span data-ttu-id="8b1be-146">PrincipalPermissionAttribute 已淘汰為錯誤</span><span class="sxs-lookup"><span data-stu-id="8b1be-146">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="8b1be-147">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-147">5.0</span></span> |
| [<span data-ttu-id="8b1be-148">ASP.NET apps 已淘汰且禁止 BinaryFormatter 序列化方法</span><span class="sxs-lookup"><span data-stu-id="8b1be-148">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="8b1be-149">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-149">5.0</span></span> |
| [<span data-ttu-id="8b1be-150">UTF-7 程式碼路徑已淘汰</span><span class="sxs-lookup"><span data-stu-id="8b1be-150">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="8b1be-151">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-151">5.0</span></span> |
| [<span data-ttu-id="8b1be-152">Vector \<T> 一律會針對不支援的類型擲回 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="8b1be-152">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="8b1be-153">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-153">5.0</span></span> |
| [<span data-ttu-id="8b1be-154">預設 ActivityIdFormat 是 W3C</span><span class="sxs-lookup"><span data-stu-id="8b1be-154">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="8b1be-155">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-155">5.0</span></span> |
| [<span data-ttu-id="8b1be-156">Vector2. Lerp 和 Vector4 的行為變更。 Lerp</span><span class="sxs-lookup"><span data-stu-id="8b1be-156">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="8b1be-157">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-157">5.0</span></span> |
| [<span data-ttu-id="8b1be-158">SSE 和 SSE2 CompareGreaterThan 方法會正確處理 NaN 輸入</span><span class="sxs-lookup"><span data-stu-id="8b1be-158">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="8b1be-159">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-159">5.0</span></span> |
| [<span data-ttu-id="8b1be-160">如果實例已經存在，則 CreateCounterSetInstance 現在會擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="8b1be-160">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="8b1be-161">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-161">5.0</span></span> |
| [<span data-ttu-id="8b1be-162">已移除 DotNet PlatformAbstractions 套件</span><span class="sxs-lookup"><span data-stu-id="8b1be-162">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="8b1be-163">5.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-163">5.0</span></span> |
| [<span data-ttu-id="8b1be-164">報表版本現在會回報產品而非檔案版本的 Api</span><span class="sxs-lookup"><span data-stu-id="8b1be-164">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="8b1be-165">3.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-165">3.0</span></span> |
| [<span data-ttu-id="8b1be-166">自訂 >encoderfallbackbuffer 實例無法遞迴地切換</span><span class="sxs-lookup"><span data-stu-id="8b1be-166">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="8b1be-167">3.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-167">3.0</span></span> |
| [<span data-ttu-id="8b1be-168">浮點數格式化和剖析行為變更</span><span class="sxs-lookup"><span data-stu-id="8b1be-168">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="8b1be-169">3.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-169">3.0</span></span> |
| [<span data-ttu-id="8b1be-170">浮點數剖析作業不再失敗或擲回 >overflowexception</span><span class="sxs-lookup"><span data-stu-id="8b1be-170">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="8b1be-171">3.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-171">3.0</span></span> |
| [<span data-ttu-id="8b1be-172">System.componentmodel.invalidasynchronousstateexception 移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="8b1be-172">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="8b1be-173">3.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-173">3.0</span></span> |
| [<span data-ttu-id="8b1be-174">取代格式不正確的 UTF-8 位元組序列遵循 Unicode 指導方針</span><span class="sxs-lookup"><span data-stu-id="8b1be-174">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="8b1be-175">3.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-175">3.0</span></span> |
| [<span data-ttu-id="8b1be-176">TypeDescriptionProviderAttribute 移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="8b1be-176">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="8b1be-177">3.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-177">3.0</span></span> |
| [<span data-ttu-id="8b1be-178">ZipArchiveEntry 不再以不一致的專案大小處理封存</span><span class="sxs-lookup"><span data-stu-id="8b1be-178">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="8b1be-179">3.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-179">3.0</span></span> |
| [<span data-ttu-id="8b1be-180">FieldInfo 會針對靜態、僅限初始欄位擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="8b1be-180">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="8b1be-181">3.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-181">3.0</span></span> |
| [<span data-ttu-id="8b1be-182">加入至內建結構類型的私用欄位</span><span class="sxs-lookup"><span data-stu-id="8b1be-182">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="8b1be-183">2.1</span><span class="sxs-lookup"><span data-stu-id="8b1be-183">2.1</span></span> |
| [<span data-ttu-id="8b1be-184">UseShellExecute 預設值的變更</span><span class="sxs-lookup"><span data-stu-id="8b1be-184">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="8b1be-185">2.1</span><span class="sxs-lookup"><span data-stu-id="8b1be-185">2.1</span></span> |
| [<span data-ttu-id="8b1be-186">MacOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="8b1be-186">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="8b1be-187">2.1</span><span class="sxs-lookup"><span data-stu-id="8b1be-187">2.1</span></span> |
| [<span data-ttu-id="8b1be-188">FileSystemInfo 擲回的 System.unauthorizedaccessexception。屬性</span><span class="sxs-lookup"><span data-stu-id="8b1be-188">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="8b1be-189">1.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-189">1.0</span></span> |
| [<span data-ttu-id="8b1be-190">不支援處理損毀的進程狀態例外狀況</span><span class="sxs-lookup"><span data-stu-id="8b1be-190">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="8b1be-191">1.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-191">1.0</span></span> |
| [<span data-ttu-id="8b1be-192">UriBuilder 屬性不再加上前置字元</span><span class="sxs-lookup"><span data-stu-id="8b1be-192">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="8b1be-193">1.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-193">1.0</span></span> |
| [<span data-ttu-id="8b1be-194">StartInfo 會針對您未啟動的進程擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="8b1be-194">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="8b1be-195">1.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-195">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="8b1be-196">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="8b1be-196">.NET 5.0</span></span>

[!INCLUDE [lastindexof-improved-handling-of-empty-values](../../../includes/core-changes/corefx/5.0/lastindexof-improved-handling-of-empty-values.md)]

***

[!INCLUDE [remoting-apis-obsolete](../../../includes/core-changes/corefx/5.0/remoting-apis-obsolete.md)]

***

[!INCLUDE [globalassemblycache-property-obsolete](../../../includes/core-changes/corefx/5.0/global-assembly-cache-apis-obsolete.md)]

***

[!INCLUDE [code-access-security-apis-obsolete](../../../includes/core-changes/corefx/5.0/code-access-security-apis-obsolete.md)]

***

[!INCLUDE [obsolete-apis-with-custom-diagnostics](../../../includes/core-changes/corefx/5.0/obsolete-apis-with-custom-diagnostics.md)]

***

[!INCLUDE [frameworkdescription-returns-net-not-net-core](../../../includes/core-changes/corefx/5.0/frameworkdescription-returns-net-not-net-core.md)]

***

[!INCLUDE [assembly-api-behavior-changes-for-single-file-publish](../../../includes/core-changes/corefx/5.0/assembly-api-behavior-changes-for-single-file-publish.md)]

***

[!INCLUDE [reverse-order-of-tags-in-activity-property](../../../includes/core-changes/corefx/5.0/reverse-order-of-tags-in-activity-property.md)]

***

[!INCLUDE [reference-assembly-parameter-names-rc1](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names-rc1.md)]

***

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

## <a name="net-core-30"></a><span data-ttu-id="8b1be-198">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-198">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="8b1be-199">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8b1be-199">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="8b1be-200">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b1be-200">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
