---
title: 基礎類別庫的重大變更
description: 列出核心 .NET 程式庫中的重大變更。
ms.date: 07/27/2020
ms.openlocfilehash: 9190fc2fc8dddc4fb4be8409915cf24c92a97daf
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558168"
---
# <a name="core-net-libraries-breaking-changes"></a>核心 .NET 程式庫的重大變更

核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般類型。

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | :-: |
| [環境。 OSVersion 傳回正確的作業系統版本](#environmentosversion-returns-the-correct-operating-system-version) | 5.0 |
| [LINQ OrderBy 的複雜度。前 {OrDefault} 增加了](#complexity-of-linq-orderbyfirstordefault-increased) | 5.0 |
| [IntPtr 和 UIntPtr 實 >iformattable](#intptr-and-uintptr-implement-iformattable) | 5.0 |
| [PrincipalPermissionAttribute 已淘汰為錯誤](#principalpermissionattribute-is-obsolete-as-error) | 5.0 |
| [ASP.NET apps 已淘汰且禁止 BinaryFormatter 序列化方法](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | 5.0 |
| [UTF-7 程式碼路徑已淘汰](#utf-7-code-paths-are-obsolete) | 5.0 |
| [Vector \<T> 一律會針對不支援的類型擲回 NotSupportedException](#vectort-always-throws-notsupportedexception-for-unsupported-types) | 5.0 |
| [預設 ActivityIdFormat 是 W3C](#default-activityidformat-is-w3c) | 5.0 |
| [Vector2. Lerp 和 Vector4 的行為變更。 Lerp](#behavior-change-for-vector2lerp-and-vector4lerp) | 5.0 |
| [SSE 和 SSE2 CompareGreaterThan 方法會正確處理 NaN 輸入](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | 5.0 |
| [如果實例已經存在，則 CreateCounterSetInstance 現在會擲回 InvalidOperationException](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | 5.0 |
| [已移除 DotNet PlatformAbstractions 套件](#microsoftdotnetplatformabstractions-package-removed) | 5.0 |
| [報表版本現在會回報產品而非檔案版本的 Api](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [自訂 >encoderfallbackbuffer 實例無法遞迴地切換](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [浮點數格式化和剖析行為變更](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [浮點數剖析作業不再失敗或擲回 >overflowexception](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [System.componentmodel.invalidasynchronousstateexception 移至另一個元件](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [取代格式不正確的 UTF-8 位元組序列遵循 Unicode 指導方針](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | 3.0 |
| [TypeDescriptionProviderAttribute 移至另一個元件](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [ZipArchiveEntry 不再以不一致的專案大小處理封存](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [FieldInfo 會針對靜態、僅限初始欄位擲回例外狀況](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [加入至內建結構類型的私用欄位](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [UseShellExecute 預設值的變更](#change-in-default-value-of-useshellexecute) | 2.1 |
| [MacOS 上的 OpenSSL 版本](#openssl-versions-on-macos) | 2.1 |
| [FileSystemInfo 擲回的 System.unauthorizedaccessexception。屬性](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |
| [不支援處理損毀的進程狀態例外狀況](#handling-corrupted-state-exceptions-is-not-supported) | 1.0 |
| [UriBuilder 屬性不再加上前置字元](#uribuilder-properties-no-longer-prepend-leading-characters) | 1.0 |
| [StartInfo 會針對您未啟動的進程擲回 InvalidOperationException](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | 1.0 |

## <a name="net-50"></a>.NET 5。0

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

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
