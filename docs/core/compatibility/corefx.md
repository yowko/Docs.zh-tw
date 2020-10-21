---
title: 基礎類別庫的重大變更
description: 列出核心 .NET 程式庫中的重大變更。
ms.date: 07/27/2020
ms.openlocfilehash: 35192ae078c6025b9b399d6638ea8b4f426aceda
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332915"
---
# <a name="core-net-libraries-breaking-changes"></a>核心 .NET 程式庫的重大變更

核心 .NET 程式庫提供 .NET Core 所使用的基本類型和其他一般類型。

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | :-: |
| [使用非預設診斷識別碼的 API obsoletions](#api-obsoletions-with-non-default-diagnostic-ids) | 5.0 |
| [FrameworkDescription 的值是 .NET 而不是 .NET Core](#frameworkdescriptions-value-is-net-instead-of-net-core) | 5.0 |
| [單一檔案發佈格式的元件相關 API 行為變更](#assembly-related-api-behavior-changes-for-single-file-publishing-format) | 5.0 |
| [活動中標記的順序。標記會反轉](#order-of-tags-in-activitytags-is-reversed) | 5.0 |
| [RC1 中的參數名稱已變更](#parameter-names-changed-in-rc1) | 5.0 |
| [OSPlatform 屬性已重新命名或移除](#osplatform-attributes-renamed-or-removed) | 5.0 |
| [執行緒。中止已淘汰](#threadabort-is-obsolete) | 5.0 |
| [ConsoleLoggerOptions 上的過時屬性](#obsolete-properties-on-consoleloggeroptions) | 5.0 |
| [巢狀型別的硬體內部 IsSupported 檢查可能不同](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | 5.0 |
| [參考元件中的參數名稱變更](#parameter-names-changed-in-reference-assemblies) | 5.0 |
| [在 Unix 上正確剖析非 ASCII 字元的 URI 路徑](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | 5.0 |
| [Unix 上 UNC 路徑的 Uri 識別](#uri-recognition-of-unc-paths-on-unix) | 5.0 |
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

[!INCLUDE [obsolete-apis-with-custom-diagnostics](../../../includes/core-changes/corefx/5.0/obsolete-apis-with-custom-diagnostics.md)]

***

[!INCLUDE [frameworkdescription-returns-net-not-net-core](../../../includes/core-changes/corefx/5.0/frameworkdescription-returns-net-not-net-core.md)]

**_

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

## <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

_**
