---
title: 基類庫的重大變更
description: 列出核心 .NET 程式庫中的重大變更。
ms.date: 09/20/2019
ms.openlocfilehash: 841003fdb114042466cc15b4846e133cf37de85c
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135642"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="6f795-103">核心 .NET 程式庫的重大變更</span><span class="sxs-lookup"><span data-stu-id="6f795-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="6f795-104">核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般型別。</span><span class="sxs-lookup"><span data-stu-id="6f795-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="6f795-105">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="6f795-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="6f795-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="6f795-106">Breaking change</span></span> | <span data-ttu-id="6f795-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6f795-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="6f795-108">報告版本的 Api 現在會報告產品，而不是檔案版本</span><span class="sxs-lookup"><span data-stu-id="6f795-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="6f795-109">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-109">3.0</span></span> |
| [<span data-ttu-id="6f795-110">自訂 EncoderFallbackBuffer 實例無法遞迴切換</span><span class="sxs-lookup"><span data-stu-id="6f795-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="6f795-111">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-111">3.0</span></span> |
| [<span data-ttu-id="6f795-112">浮點格式設定和剖析行為變更</span><span class="sxs-lookup"><span data-stu-id="6f795-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="6f795-113">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-113">3.0</span></span> |
| [<span data-ttu-id="6f795-114">浮點剖析作業不再失敗或擲回 OverflowException</span><span class="sxs-lookup"><span data-stu-id="6f795-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="6f795-115">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-115">3.0</span></span> |
| [<span data-ttu-id="6f795-116">System.componentmodel.invalidasynchronousstateexception 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="6f795-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="6f795-117">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-117">3.0</span></span> |
| [<span data-ttu-id="6f795-118">NET Core 3.0 在取代格式不正確的 UTF-8 位元組序列時，遵循 Unicode 最佳做法</span><span class="sxs-lookup"><span data-stu-id="6f795-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="6f795-119">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-119">3.0</span></span> |
| [<span data-ttu-id="6f795-120">TypeDescriptionProviderAttribute 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="6f795-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="6f795-121">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-121">3.0</span></span> |
| [<span data-ttu-id="6f795-122">Ziparchiveentry 中不再處理具有不一致專案大小的封存</span><span class="sxs-lookup"><span data-stu-id="6f795-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="6f795-123">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-123">3.0</span></span> |
| [<span data-ttu-id="6f795-124">JSON 序列化程式例外狀況類型已從 JsonException 變更為 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="6f795-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="6f795-125">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-125">3.0</span></span> |
| [<span data-ttu-id="6f795-126">在 Utf8JsonWriter 中變更（string） null 的語義</span><span class="sxs-lookup"><span data-stu-id="6f795-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="6f795-127">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-127">3.0</span></span> |
| [<span data-ttu-id="6f795-128">JsonEncodedText 方法有額外的 JavaScriptEncoder 引數</span><span class="sxs-lookup"><span data-stu-id="6f795-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="6f795-129">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-129">3.0</span></span> |
| [<span data-ttu-id="6f795-130">JsonFactoryConverter. CreateConverter 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="6f795-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="6f795-131">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-131">3.0</span></span> |
| [<span data-ttu-id="6f795-132">JsonElement API 變更</span><span class="sxs-lookup"><span data-stu-id="6f795-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="6f795-133">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-133">3.0</span></span> |
| [<span data-ttu-id="6f795-134">FieldInfo。 SetValue 會擲回靜態、僅限初始欄位的例外狀況</span><span class="sxs-lookup"><span data-stu-id="6f795-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="6f795-135">3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-135">3.0</span></span> |
| [<span data-ttu-id="6f795-136">加入至內建結構類型的私用欄位</span><span class="sxs-lookup"><span data-stu-id="6f795-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="6f795-137">2.1</span><span class="sxs-lookup"><span data-stu-id="6f795-137">2.1</span></span> |
| [<span data-ttu-id="6f795-138">預設值為 UseShellExecute 的變更</span><span class="sxs-lookup"><span data-stu-id="6f795-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="6f795-139">2.1</span><span class="sxs-lookup"><span data-stu-id="6f795-139">2.1</span></span> |
| [<span data-ttu-id="6f795-140">MacOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="6f795-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="6f795-141">2.1</span><span class="sxs-lookup"><span data-stu-id="6f795-141">2.1</span></span> |
| [<span data-ttu-id="6f795-142">FileSystemInfo 擲回的 System.unauthorizedaccessexception</span><span class="sxs-lookup"><span data-stu-id="6f795-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="6f795-143">1.0</span><span class="sxs-lookup"><span data-stu-id="6f795-143">1.0</span></span> |
| [<span data-ttu-id="6f795-144">不支援處理損毀的進程狀態例外狀況</span><span class="sxs-lookup"><span data-stu-id="6f795-144">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="6f795-145">1.0</span><span class="sxs-lookup"><span data-stu-id="6f795-145">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="6f795-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6f795-146">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="6f795-147">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6f795-147">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="6f795-148">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="6f795-148">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***
