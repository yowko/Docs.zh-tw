---
title: 基類庫的重大變更
description: 列出核心 .NET 程式庫中的重大變更。
ms.date: 09/20/2019
ms.openlocfilehash: 1c56358e69d0dd6e8572a41229c1b9edbcdad795
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365608"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="c0ff8-103">核心 .NET 程式庫的重大變更</span><span class="sxs-lookup"><span data-stu-id="c0ff8-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="c0ff8-104">核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般型別。</span><span class="sxs-lookup"><span data-stu-id="c0ff8-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="c0ff8-105">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="c0ff8-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="c0ff8-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="c0ff8-106">Breaking change</span></span> | <span data-ttu-id="c0ff8-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c0ff8-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="c0ff8-108">SSE 和 SSE2 CompareGreaterThan 方法會適當地處理 NaN 輸入</span><span class="sxs-lookup"><span data-stu-id="c0ff8-108">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="c0ff8-109">5.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-109">5.0</span></span> |
| [<span data-ttu-id="c0ff8-110">如果實例已經存在，CreateCounterSetInstance 現在會擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="c0ff8-110">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="c0ff8-111">5.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-111">5.0</span></span> |
| [<span data-ttu-id="c0ff8-112">已移除 DotNet PlatformAbstractions 套件</span><span class="sxs-lookup"><span data-stu-id="c0ff8-112">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="c0ff8-113">5.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-113">5.0</span></span> |
| [<span data-ttu-id="c0ff8-114">報告版本的 Api 現在會報告產品，而不是檔案版本</span><span class="sxs-lookup"><span data-stu-id="c0ff8-114">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="c0ff8-115">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-115">3.0</span></span> |
| [<span data-ttu-id="c0ff8-116">自訂 EncoderFallbackBuffer 實例無法遞迴切換</span><span class="sxs-lookup"><span data-stu-id="c0ff8-116">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="c0ff8-117">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-117">3.0</span></span> |
| [<span data-ttu-id="c0ff8-118">浮點格式設定和剖析行為變更</span><span class="sxs-lookup"><span data-stu-id="c0ff8-118">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="c0ff8-119">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-119">3.0</span></span> |
| [<span data-ttu-id="c0ff8-120">浮點剖析作業不再失敗或擲回 OverflowException</span><span class="sxs-lookup"><span data-stu-id="c0ff8-120">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="c0ff8-121">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-121">3.0</span></span> |
| [<span data-ttu-id="c0ff8-122">System.componentmodel.invalidasynchronousstateexception 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="c0ff8-122">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="c0ff8-123">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-123">3.0</span></span> |
| [<span data-ttu-id="c0ff8-124">取代格式不正確的 UTF-8 位元組序列遵循 Unicode 方針</span><span class="sxs-lookup"><span data-stu-id="c0ff8-124">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="c0ff8-125">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-125">3.0</span></span> |
| [<span data-ttu-id="c0ff8-126">TypeDescriptionProviderAttribute 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="c0ff8-126">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="c0ff8-127">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-127">3.0</span></span> |
| [<span data-ttu-id="c0ff8-128">Ziparchiveentry 中不再處理具有不一致專案大小的封存</span><span class="sxs-lookup"><span data-stu-id="c0ff8-128">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="c0ff8-129">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-129">3.0</span></span> |
| [<span data-ttu-id="c0ff8-130">JSON 序列化程式例外狀況類型已從 JsonException 變更為 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="c0ff8-130">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="c0ff8-131">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-131">3.0</span></span> |
| [<span data-ttu-id="c0ff8-132">在 Utf8JsonWriter 中變更（string） null 的語義</span><span class="sxs-lookup"><span data-stu-id="c0ff8-132">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="c0ff8-133">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-133">3.0</span></span> |
| [<span data-ttu-id="c0ff8-134">JsonEncodedText 方法有額外的 JavaScriptEncoder 引數</span><span class="sxs-lookup"><span data-stu-id="c0ff8-134">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="c0ff8-135">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-135">3.0</span></span> |
| [<span data-ttu-id="c0ff8-136">JsonFactoryConverter. CreateConverter 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="c0ff8-136">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="c0ff8-137">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-137">3.0</span></span> |
| [<span data-ttu-id="c0ff8-138">JsonElement API 變更</span><span class="sxs-lookup"><span data-stu-id="c0ff8-138">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="c0ff8-139">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-139">3.0</span></span> |
| [<span data-ttu-id="c0ff8-140">FieldInfo。 SetValue 會擲回靜態、僅限初始欄位的例外狀況</span><span class="sxs-lookup"><span data-stu-id="c0ff8-140">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="c0ff8-141">3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-141">3.0</span></span> |
| [<span data-ttu-id="c0ff8-142">加入至內建結構類型的私用欄位</span><span class="sxs-lookup"><span data-stu-id="c0ff8-142">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="c0ff8-143">2.1</span><span class="sxs-lookup"><span data-stu-id="c0ff8-143">2.1</span></span> |
| [<span data-ttu-id="c0ff8-144">預設值為 UseShellExecute 的變更</span><span class="sxs-lookup"><span data-stu-id="c0ff8-144">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="c0ff8-145">2.1</span><span class="sxs-lookup"><span data-stu-id="c0ff8-145">2.1</span></span> |
| [<span data-ttu-id="c0ff8-146">MacOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="c0ff8-146">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="c0ff8-147">2.1</span><span class="sxs-lookup"><span data-stu-id="c0ff8-147">2.1</span></span> |
| [<span data-ttu-id="c0ff8-148">FileSystemInfo 擲回的 System.unauthorizedaccessexception</span><span class="sxs-lookup"><span data-stu-id="c0ff8-148">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="c0ff8-149">1.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-149">1.0</span></span> |
| [<span data-ttu-id="c0ff8-150">不支援處理損毀的進程狀態例外狀況</span><span class="sxs-lookup"><span data-stu-id="c0ff8-150">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="c0ff8-151">1.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-151">1.0</span></span> |
| [<span data-ttu-id="c0ff8-152">UriBuilder 屬性不再前面加上前置字元</span><span class="sxs-lookup"><span data-stu-id="c0ff8-152">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="c0ff8-153">1.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-153">1.0</span></span> |
| [<span data-ttu-id="c0ff8-154">StartInfo 會針對您未啟動的進程擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="c0ff8-154">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="c0ff8-155">1.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-155">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="c0ff8-156">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-156">.NET 5.0</span></span>

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="c0ff8-157">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-157">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="c0ff8-158">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c0ff8-158">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="c0ff8-159">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="c0ff8-159">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
