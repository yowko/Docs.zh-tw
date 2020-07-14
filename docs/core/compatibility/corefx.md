---
title: 基類庫的重大變更
description: 列出核心 .NET 程式庫中的重大變更。
ms.date: 09/20/2019
ms.openlocfilehash: 64510809a1cf69ea0e4c4816eb2df54233e8eceb
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281292"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="b9a78-103">核心 .NET 程式庫的重大變更</span><span class="sxs-lookup"><span data-stu-id="b9a78-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="b9a78-104">核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般型別。</span><span class="sxs-lookup"><span data-stu-id="b9a78-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="b9a78-105">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="b9a78-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="b9a78-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="b9a78-106">Breaking change</span></span> | <span data-ttu-id="b9a78-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b9a78-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="b9a78-108">預設 ActivityIdFormat 為 W3C</span><span class="sxs-lookup"><span data-stu-id="b9a78-108">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="b9a78-109">5.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-109">5.0</span></span> |
| [<span data-ttu-id="b9a78-110">Vector2 的行為變更。 Lerp 和 Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="b9a78-110">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="b9a78-111">5.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-111">5.0</span></span> |
| [<span data-ttu-id="b9a78-112">SSE 和 SSE2 CompareGreaterThan 方法會適當地處理 NaN 輸入</span><span class="sxs-lookup"><span data-stu-id="b9a78-112">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="b9a78-113">5.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-113">5.0</span></span> |
| [<span data-ttu-id="b9a78-114">如果實例已經存在，CreateCounterSetInstance 現在會擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="b9a78-114">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="b9a78-115">5.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-115">5.0</span></span> |
| [<span data-ttu-id="b9a78-116">已移除 DotNet PlatformAbstractions 套件</span><span class="sxs-lookup"><span data-stu-id="b9a78-116">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="b9a78-117">5.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-117">5.0</span></span> |
| [<span data-ttu-id="b9a78-118">報告版本的 Api 現在會報告產品，而不是檔案版本</span><span class="sxs-lookup"><span data-stu-id="b9a78-118">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="b9a78-119">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-119">3.0</span></span> |
| [<span data-ttu-id="b9a78-120">自訂 EncoderFallbackBuffer 實例無法遞迴切換</span><span class="sxs-lookup"><span data-stu-id="b9a78-120">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="b9a78-121">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-121">3.0</span></span> |
| [<span data-ttu-id="b9a78-122">浮點格式設定和剖析行為變更</span><span class="sxs-lookup"><span data-stu-id="b9a78-122">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="b9a78-123">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-123">3.0</span></span> |
| [<span data-ttu-id="b9a78-124">浮點剖析作業不再失敗或擲回 OverflowException</span><span class="sxs-lookup"><span data-stu-id="b9a78-124">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="b9a78-125">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-125">3.0</span></span> |
| [<span data-ttu-id="b9a78-126">System.componentmodel.invalidasynchronousstateexception 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="b9a78-126">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="b9a78-127">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-127">3.0</span></span> |
| [<span data-ttu-id="b9a78-128">取代格式不正確的 UTF-8 位元組序列遵循 Unicode 方針</span><span class="sxs-lookup"><span data-stu-id="b9a78-128">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="b9a78-129">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-129">3.0</span></span> |
| [<span data-ttu-id="b9a78-130">TypeDescriptionProviderAttribute 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="b9a78-130">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="b9a78-131">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-131">3.0</span></span> |
| [<span data-ttu-id="b9a78-132">Ziparchiveentry 中不再處理具有不一致專案大小的封存</span><span class="sxs-lookup"><span data-stu-id="b9a78-132">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="b9a78-133">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-133">3.0</span></span> |
| [<span data-ttu-id="b9a78-134">JSON 序列化程式例外狀況類型已從 JsonException 變更為 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="b9a78-134">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="b9a78-135">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-135">3.0</span></span> |
| [<span data-ttu-id="b9a78-136">在 Utf8JsonWriter 中變更 (字串的語義) null</span><span class="sxs-lookup"><span data-stu-id="b9a78-136">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="b9a78-137">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-137">3.0</span></span> |
| [<span data-ttu-id="b9a78-138">JsonEncodedText 方法有額外的 JavaScriptEncoder 引數</span><span class="sxs-lookup"><span data-stu-id="b9a78-138">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="b9a78-139">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-139">3.0</span></span> |
| [<span data-ttu-id="b9a78-140">JsonFactoryConverter. CreateConverter 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="b9a78-140">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="b9a78-141">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-141">3.0</span></span> |
| [<span data-ttu-id="b9a78-142">JsonElement API 變更</span><span class="sxs-lookup"><span data-stu-id="b9a78-142">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="b9a78-143">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-143">3.0</span></span> |
| [<span data-ttu-id="b9a78-144">FieldInfo。 SetValue 會擲回靜態、僅限初始欄位的例外狀況</span><span class="sxs-lookup"><span data-stu-id="b9a78-144">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="b9a78-145">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-145">3.0</span></span> |
| [<span data-ttu-id="b9a78-146">加入至內建結構類型的私用欄位</span><span class="sxs-lookup"><span data-stu-id="b9a78-146">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="b9a78-147">2.1</span><span class="sxs-lookup"><span data-stu-id="b9a78-147">2.1</span></span> |
| [<span data-ttu-id="b9a78-148">預設值為 UseShellExecute 的變更</span><span class="sxs-lookup"><span data-stu-id="b9a78-148">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="b9a78-149">2.1</span><span class="sxs-lookup"><span data-stu-id="b9a78-149">2.1</span></span> |
| [<span data-ttu-id="b9a78-150">MacOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="b9a78-150">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="b9a78-151">2.1</span><span class="sxs-lookup"><span data-stu-id="b9a78-151">2.1</span></span> |
| [<span data-ttu-id="b9a78-152">FileSystemInfo 擲回的 System.unauthorizedaccessexception</span><span class="sxs-lookup"><span data-stu-id="b9a78-152">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="b9a78-153">1.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-153">1.0</span></span> |
| [<span data-ttu-id="b9a78-154">不支援處理損毀的進程狀態例外狀況</span><span class="sxs-lookup"><span data-stu-id="b9a78-154">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="b9a78-155">1.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-155">1.0</span></span> |
| [<span data-ttu-id="b9a78-156">UriBuilder 屬性不再前面加上前置字元</span><span class="sxs-lookup"><span data-stu-id="b9a78-156">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="b9a78-157">1.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-157">1.0</span></span> |
| [<span data-ttu-id="b9a78-158">StartInfo 會針對您未啟動的進程擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="b9a78-158">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="b9a78-159">1.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-159">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="b9a78-160">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="b9a78-160">.NET 5.0</span></span>

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

## <a name="net-core-30"></a><span data-ttu-id="b9a78-161">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-161">.NET Core 3.0</span></span>

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

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

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

## <a name="net-core-21"></a><span data-ttu-id="b9a78-162">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b9a78-162">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="b9a78-163">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b9a78-163">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
