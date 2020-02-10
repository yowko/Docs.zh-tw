---
title: 基類庫的重大變更
description: 列出 .NET CoreFx （基類庫）中的重大變更。
ms.date: 09/20/2019
ms.openlocfilehash: 9e8a00abfae8bf8f5301a4879cb5274492a2b6fd
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093080"
---
# <a name="corefx-breaking-changes"></a><span data-ttu-id="f7c1b-103">CoreFx 重大變更</span><span class="sxs-lookup"><span data-stu-id="f7c1b-103">CoreFx breaking changes</span></span>

<span data-ttu-id="f7c1b-104">CoreFx 提供 .NET Core 所使用的基本和其他一般類型。</span><span class="sxs-lookup"><span data-stu-id="f7c1b-104">CoreFx provides the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="f7c1b-105">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="f7c1b-105">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="f7c1b-106">報告版本的 Api 現在會報告產品，而不是檔案版本</span><span class="sxs-lookup"><span data-stu-id="f7c1b-106">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version)
- [<span data-ttu-id="f7c1b-107">自訂 EncoderFallbackBuffer 實例無法遞迴切換</span><span class="sxs-lookup"><span data-stu-id="f7c1b-107">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively)
- [<span data-ttu-id="f7c1b-108">浮點格式設定和剖析行為變更</span><span class="sxs-lookup"><span data-stu-id="f7c1b-108">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed)
- [<span data-ttu-id="f7c1b-109">浮點剖析作業不再失敗或擲回 OverflowException</span><span class="sxs-lookup"><span data-stu-id="f7c1b-109">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception)
- [<span data-ttu-id="f7c1b-110">System.componentmodel.invalidasynchronousstateexception 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="f7c1b-110">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly)
- [<span data-ttu-id="f7c1b-111">NET Core 3.0 在取代格式不正確的 UTF-8 位元組序列時，遵循 Unicode 最佳做法</span><span class="sxs-lookup"><span data-stu-id="f7c1b-111">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences)
- [<span data-ttu-id="f7c1b-112">TypeDescriptionProviderAttribute 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="f7c1b-112">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly)
- [<span data-ttu-id="f7c1b-113">Ziparchiveentry 中不再處理具有不一致專案大小的封存</span><span class="sxs-lookup"><span data-stu-id="f7c1b-113">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes)
- [<span data-ttu-id="f7c1b-114">JSON 序列化程式例外狀況類型已從 JsonException 變更為 NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="f7c1b-114">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception)
- [<span data-ttu-id="f7c1b-115">在 Utf8JsonWriter 中變更（string） null 的語義</span><span class="sxs-lookup"><span data-stu-id="f7c1b-115">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter)
- [<span data-ttu-id="f7c1b-116">JsonEncodedText 方法有額外的 JavaScriptEncoder 引數</span><span class="sxs-lookup"><span data-stu-id="f7c1b-116">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument)
- [<span data-ttu-id="f7c1b-117">JsonFactoryConverter. CreateConverter 簽章已變更</span><span class="sxs-lookup"><span data-stu-id="f7c1b-117">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed)
- [<span data-ttu-id="f7c1b-118">JsonElement API 變更</span><span class="sxs-lookup"><span data-stu-id="f7c1b-118">JsonElement API changes</span></span>](#jsonelement-api-changes)
- [<span data-ttu-id="f7c1b-119">加入至內建結構類型的私用欄位</span><span class="sxs-lookup"><span data-stu-id="f7c1b-119">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types)
- [<span data-ttu-id="f7c1b-120">預設值為 UseShellExecute 的變更</span><span class="sxs-lookup"><span data-stu-id="f7c1b-120">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)

## <a name="net-core-30"></a><span data-ttu-id="f7c1b-121">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f7c1b-121">.NET Core 3.0</span></span>

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

## <a name="net-core-30-preview-9"></a><span data-ttu-id="f7c1b-122">.NET Core 3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="f7c1b-122">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

## <a name="net-core-30-preview-8"></a><span data-ttu-id="f7c1b-123">.NET Core 3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="f7c1b-123">.NET Core 3.0 Preview 8</span></span>

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

## <a name="net-core-30-preview-7"></a><span data-ttu-id="f7c1b-124">.NET Core 3.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="f7c1b-124">.NET Core 3.0 Preview 7</span></span>

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="f7c1b-125">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f7c1b-125">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***
