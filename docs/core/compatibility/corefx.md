---
title: 基類庫突破更改
description: 列出 .NET CoreFx（基類庫）中的重大更改。
ms.date: 09/20/2019
ms.openlocfilehash: 56a3cf4f4c00a79752d5a98bb086bb9f8c0614b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147571"
---
# <a name="corefx-breaking-changes"></a><span data-ttu-id="b373d-103">酷睿突破更改</span><span class="sxs-lookup"><span data-stu-id="b373d-103">CoreFx breaking changes</span></span>

<span data-ttu-id="b373d-104">CoreFx 提供 .NET Core 使用的基元和其他常規類型。</span><span class="sxs-lookup"><span data-stu-id="b373d-104">CoreFx provides the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="b373d-105">此頁面將記錄以下重大更改：</span><span class="sxs-lookup"><span data-stu-id="b373d-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="b373d-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="b373d-106">Breaking change</span></span> | <span data-ttu-id="b373d-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="b373d-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="b373d-108">報表版本的 API 現在報告產品，而不是檔版本</span><span class="sxs-lookup"><span data-stu-id="b373d-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="b373d-109">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-109">3.0</span></span> |
| [<span data-ttu-id="b373d-110">自訂編碼器回退緩衝區實例不能遞迴</span><span class="sxs-lookup"><span data-stu-id="b373d-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="b373d-111">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-111">3.0</span></span> |
| [<span data-ttu-id="b373d-112">浮點格式設置和分析行為更改</span><span class="sxs-lookup"><span data-stu-id="b373d-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="b373d-113">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-113">3.0</span></span> |
| [<span data-ttu-id="b373d-114">浮點分析操作不再失敗或引發溢出異常</span><span class="sxs-lookup"><span data-stu-id="b373d-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="b373d-115">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-115">3.0</span></span> |
| [<span data-ttu-id="b373d-116">不正確非同步狀態異常移動到另一個程式集</span><span class="sxs-lookup"><span data-stu-id="b373d-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="b373d-117">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-117">3.0</span></span> |
| [<span data-ttu-id="b373d-118">NET Core 3.0 在替換格式錯誤的 UTF-8 位元組序列時遵循 Unicode 最佳實踐</span><span class="sxs-lookup"><span data-stu-id="b373d-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="b373d-119">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-119">3.0</span></span> |
| [<span data-ttu-id="b373d-120">類型描述提供程式屬性移動到另一個程式集</span><span class="sxs-lookup"><span data-stu-id="b373d-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="b373d-121">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-121">3.0</span></span> |
| [<span data-ttu-id="b373d-122">ZipArchiveEntry 不再處理條目大小不一致的存檔</span><span class="sxs-lookup"><span data-stu-id="b373d-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="b373d-123">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-123">3.0</span></span> |
| [<span data-ttu-id="b373d-124">JSON 序列化器異常類型從 JsonException 更改為"不支援例外"</span><span class="sxs-lookup"><span data-stu-id="b373d-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="b373d-125">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-125">3.0</span></span> |
| [<span data-ttu-id="b373d-126">Utf8JonWriter 中（字串）空語義的更改</span><span class="sxs-lookup"><span data-stu-id="b373d-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="b373d-127">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-127">3.0</span></span> |
| [<span data-ttu-id="b373d-128">JsonEncodedText.編碼方法具有額外的JavaScriptEncoder參數</span><span class="sxs-lookup"><span data-stu-id="b373d-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="b373d-129">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-129">3.0</span></span> |
| [<span data-ttu-id="b373d-130">JsonFactory轉換器.創建轉換器簽名已更改</span><span class="sxs-lookup"><span data-stu-id="b373d-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="b373d-131">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-131">3.0</span></span> |
| [<span data-ttu-id="b373d-132">JsonElement API 更改</span><span class="sxs-lookup"><span data-stu-id="b373d-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="b373d-133">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-133">3.0</span></span> |
| [<span data-ttu-id="b373d-134">欄位資訊.SetValue 引發靜態、僅 it 欄位的異常</span><span class="sxs-lookup"><span data-stu-id="b373d-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="b373d-135">3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-135">3.0</span></span> |
| [<span data-ttu-id="b373d-136">添加到內置結構類型的私有欄位</span><span class="sxs-lookup"><span data-stu-id="b373d-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="b373d-137">2.1</span><span class="sxs-lookup"><span data-stu-id="b373d-137">2.1</span></span> |
| [<span data-ttu-id="b373d-138">使用殼牌執行的預設值更改</span><span class="sxs-lookup"><span data-stu-id="b373d-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="b373d-139">2.1</span><span class="sxs-lookup"><span data-stu-id="b373d-139">2.1</span></span> |
| [<span data-ttu-id="b373d-140">macOS 上的打開 SSL 版本</span><span class="sxs-lookup"><span data-stu-id="b373d-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="b373d-141">2.1</span><span class="sxs-lookup"><span data-stu-id="b373d-141">2.1</span></span> |
| [<span data-ttu-id="b373d-142">檔案系統資訊.屬性引發的未經授權的訪問異常</span><span class="sxs-lookup"><span data-stu-id="b373d-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="b373d-143">1.0</span><span class="sxs-lookup"><span data-stu-id="b373d-143">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="b373d-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b373d-144">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="b373d-145">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b373d-145">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="b373d-146">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="b373d-146">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
