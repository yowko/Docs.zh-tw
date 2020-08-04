---
title: 基類庫的重大變更
description: 列出核心 .NET 程式庫中的重大變更。
ms.date: 07/27/2020
ms.openlocfilehash: 558aa1d76831cd15e2028c17d2b0b2e82f64ef9a
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517319"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="3b9c7-103">核心 .NET 程式庫的重大變更</span><span class="sxs-lookup"><span data-stu-id="3b9c7-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="3b9c7-104">核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般型別。</span><span class="sxs-lookup"><span data-stu-id="3b9c7-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="3b9c7-105">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="3b9c7-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="3b9c7-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="3b9c7-106">Breaking change</span></span> | <span data-ttu-id="3b9c7-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3b9c7-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="3b9c7-108">ASP.NET 應用程式中的 BinaryFormatter 序列化方法已過時且禁止</span><span class="sxs-lookup"><span data-stu-id="3b9c7-108">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="3b9c7-109">5.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-109">5.0</span></span> |
| [<span data-ttu-id="3b9c7-110">UTF-7 程式碼路徑已過時</span><span class="sxs-lookup"><span data-stu-id="3b9c7-110">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="3b9c7-111">5.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-111">5.0</span></span> |
| [<span data-ttu-id="3b9c7-112">Vector 一律會擲回 \<T> 不支援之類型的 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="3b9c7-112">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="3b9c7-113">5.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-113">5.0</span></span> |
| [<span data-ttu-id="3b9c7-114">預設 ActivityIdFormat 為 W3C</span><span class="sxs-lookup"><span data-stu-id="3b9c7-114">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="3b9c7-115">5.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-115">5.0</span></span> |
| [<span data-ttu-id="3b9c7-116">Vector2 的行為變更。 Lerp 和 Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="3b9c7-116">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="3b9c7-117">5.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-117">5.0</span></span> |
| [<span data-ttu-id="3b9c7-118">SSE 和 SSE2 CompareGreaterThan 方法會適當地處理 NaN 輸入</span><span class="sxs-lookup"><span data-stu-id="3b9c7-118">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="3b9c7-119">5.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-119">5.0</span></span> |
| [<span data-ttu-id="3b9c7-120">如果實例已經存在，CreateCounterSetInstance 現在會擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="3b9c7-120">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="3b9c7-121">5.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-121">5.0</span></span> |
| [<span data-ttu-id="3b9c7-122">已移除 DotNet PlatformAbstractions 套件</span><span class="sxs-lookup"><span data-stu-id="3b9c7-122">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="3b9c7-123">5.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-123">5.0</span></span> |
| [<span data-ttu-id="3b9c7-124">報告版本的 Api 現在會報告產品，而不是檔案版本</span><span class="sxs-lookup"><span data-stu-id="3b9c7-124">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="3b9c7-125">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-125">3.0</span></span> |
| [<span data-ttu-id="3b9c7-126">自訂 EncoderFallbackBuffer 實例無法遞迴切換</span><span class="sxs-lookup"><span data-stu-id="3b9c7-126">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="3b9c7-127">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-127">3.0</span></span> |
| [<span data-ttu-id="3b9c7-128">浮點格式設定和剖析行為變更</span><span class="sxs-lookup"><span data-stu-id="3b9c7-128">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="3b9c7-129">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-129">3.0</span></span> |
| [<span data-ttu-id="3b9c7-130">浮點剖析作業不再失敗或擲回 OverflowException</span><span class="sxs-lookup"><span data-stu-id="3b9c7-130">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="3b9c7-131">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-131">3.0</span></span> |
| [<span data-ttu-id="3b9c7-132">System.componentmodel.invalidasynchronousstateexception 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="3b9c7-132">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="3b9c7-133">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-133">3.0</span></span> |
| [<span data-ttu-id="3b9c7-134">取代格式不正確的 UTF-8 位元組序列遵循 Unicode 方針</span><span class="sxs-lookup"><span data-stu-id="3b9c7-134">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="3b9c7-135">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-135">3.0</span></span> |
| [<span data-ttu-id="3b9c7-136">TypeDescriptionProviderAttribute 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="3b9c7-136">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="3b9c7-137">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-137">3.0</span></span> |
| [<span data-ttu-id="3b9c7-138">Ziparchiveentry 中不再處理具有不一致專案大小的封存</span><span class="sxs-lookup"><span data-stu-id="3b9c7-138">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="3b9c7-139">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-139">3.0</span></span> |
| [<span data-ttu-id="3b9c7-140">在 Utf8JsonWriter 中變更（string） null 的語義</span><span class="sxs-lookup"><span data-stu-id="3b9c7-140">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="3b9c7-141">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-141">3.0</span></span> |
| [<span data-ttu-id="3b9c7-142">JsonEncodedText 方法有額外的 JavaScriptEncoder 引數</span><span class="sxs-lookup"><span data-stu-id="3b9c7-142">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="3b9c7-143">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-143">3.0</span></span> |
| [<span data-ttu-id="3b9c7-144">JsonFactoryConverter. CreateConverter 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="3b9c7-144">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="3b9c7-145">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-145">3.0</span></span> |
| [<span data-ttu-id="3b9c7-146">JsonElement API 變更</span><span class="sxs-lookup"><span data-stu-id="3b9c7-146">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="3b9c7-147">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-147">3.0</span></span> |
| [<span data-ttu-id="3b9c7-148">FieldInfo。 SetValue 會擲回靜態、僅限初始欄位的例外狀況</span><span class="sxs-lookup"><span data-stu-id="3b9c7-148">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="3b9c7-149">3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-149">3.0</span></span> |
| [<span data-ttu-id="3b9c7-150">加入至內建結構類型的私用欄位</span><span class="sxs-lookup"><span data-stu-id="3b9c7-150">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="3b9c7-151">2.1</span><span class="sxs-lookup"><span data-stu-id="3b9c7-151">2.1</span></span> |
| [<span data-ttu-id="3b9c7-152">預設值為 UseShellExecute 的變更</span><span class="sxs-lookup"><span data-stu-id="3b9c7-152">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="3b9c7-153">2.1</span><span class="sxs-lookup"><span data-stu-id="3b9c7-153">2.1</span></span> |
| [<span data-ttu-id="3b9c7-154">MacOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="3b9c7-154">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="3b9c7-155">2.1</span><span class="sxs-lookup"><span data-stu-id="3b9c7-155">2.1</span></span> |
| [<span data-ttu-id="3b9c7-156">FileSystemInfo 擲回的 System.unauthorizedaccessexception</span><span class="sxs-lookup"><span data-stu-id="3b9c7-156">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="3b9c7-157">1.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-157">1.0</span></span> |
| [<span data-ttu-id="3b9c7-158">不支援處理損毀的進程狀態例外狀況</span><span class="sxs-lookup"><span data-stu-id="3b9c7-158">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="3b9c7-159">1.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-159">1.0</span></span> |
| [<span data-ttu-id="3b9c7-160">UriBuilder 屬性不再前面加上前置字元</span><span class="sxs-lookup"><span data-stu-id="3b9c7-160">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="3b9c7-161">1.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-161">1.0</span></span> |
| [<span data-ttu-id="3b9c7-162">StartInfo 會針對您未啟動的進程擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="3b9c7-162">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="3b9c7-163">1.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-163">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="3b9c7-164">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-164">.NET 5.0</span></span>

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

## <a name="net-core-30"></a><span data-ttu-id="3b9c7-165">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-165">.NET Core 3.0</span></span>

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

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="3b9c7-166">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3b9c7-166">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="3b9c7-167">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3b9c7-167">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
