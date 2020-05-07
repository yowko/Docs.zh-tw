---
title: 基類庫的重大變更
description: 列出核心 .NET 程式庫中的重大變更。
ms.date: 09/20/2019
ms.openlocfilehash: a2eb4be89d78f50d201272f3449374bc27d8c785
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859937"
---
# <a name="core-net-libraries-breaking-changes"></a>核心 .NET 程式庫的重大變更

核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般型別。

下列重大變更記載于此頁面：

| 重大變更 | 引進的版本 |
| - | :-: |
| [SSE 和 SSE2 CompareGreaterThan 方法會適當地處理 NaN 輸入](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | 5.0 |
| [報告版本的 Api 現在會報告產品，而不是檔案版本](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [自訂 EncoderFallbackBuffer 實例無法遞迴切換](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [浮點格式設定和剖析行為變更](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [浮點剖析作業不再失敗或擲回 OverflowException](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [System.componentmodel.invalidasynchronousstateexception 已移至另一個元件](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [取代格式不正確的 UTF-8 位元組序列遵循 Unicode 方針](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | 3.0 |
| [TypeDescriptionProviderAttribute 已移至另一個元件](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [Ziparchiveentry 中不再處理具有不一致專案大小的封存](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [JSON 序列化程式例外狀況類型已從 JsonException 變更為 NotSupportedException](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | 3.0 |
| [在 Utf8JsonWriter 中變更（string） null 的語義](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | 3.0 |
| [JsonEncodedText 方法有額外的 JavaScriptEncoder 引數](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | 3.0 |
| [JsonFactoryConverter. CreateConverter 簽章已變更](#jsonfactoryconvertercreateconverter-signature-changed) | 3.0 |
| [JsonElement API 變更](#jsonelement-api-changes) | 3.0 |
| [FieldInfo。 SetValue 會擲回靜態、僅限初始欄位的例外狀況](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [加入至內建結構類型的私用欄位](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [預設值為 UseShellExecute 的變更](#change-in-default-value-of-useshellexecute) | 2.1 |
| [MacOS 上的 OpenSSL 版本](#openssl-versions-on-macos) | 2.1 |
| [FileSystemInfo 擲回的 System.unauthorizedaccessexception](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |
| [不支援處理損毀的進程狀態例外狀況](#handling-corrupted-state-exceptions-is-not-supported) | 1.0 |
| [UriBuilder 屬性不再前面加上前置字元](#uribuilder-properties-no-longer-prepend-leading-characters) | 1.0 |

## <a name="net-50"></a>.NET 5。0

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***
