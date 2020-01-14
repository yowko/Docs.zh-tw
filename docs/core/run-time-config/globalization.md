---
title: 全球化 config 設定
description: 瞭解設定 .NET Core 應用程式全球化層面的執行時間設定，例如，它如何剖析日文日期。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 76cd4a0a0f93f4df3ff243c6024b952576e8e6cb
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740536"
---
# <a name="run-time-configuration-options-for-globalization"></a>全球化的執行時間設定選項

## <a name="invariant-mode"></a>不變模式

- 判斷 .NET Core 應用程式是否以全球化不變模式執行，而不需要存取特定文化特性的資料和行為，或是否可存取文化特性資料。
- 預設值：執行可存取文化特性資料的應用程式（`false`）。
- 如需詳細資訊，請參閱[.Net Core 全球化不變模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Globalization.Invariant` | `false`-文化特性資料的存取權<br/>`true`-在不變模式下執行 |
| **環境變數** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`-文化特性資料的存取權<br/>`1`-在不變模式下執行 |

## <a name="era-year-ranges"></a>紀元年份範圍

- 判斷支援多個紀元之行事曆的範圍檢查是否會被放寬，或是否會擲回 <xref:System.ArgumentOutOfRangeException>的日期。
- 預設值：範圍檢查是寬鬆的（`false`）。
- 如需詳細資訊，請參閱行事[曆、紀元和日期範圍：寬鬆範圍檢查](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false` 寬鬆的範圍檢查<br/>`true`-溢位造成例外狀況 |
| **環境變數** | N/A | N/A |

## <a name="japanese-date-parsing"></a>日文日期剖析

- 判斷在年份中包含 "1" 或 "Gannen" 的字串是否已成功剖析，或是否只支援 "1"。
- 預設值：剖析包含 "1" 或 "Gannen" 做為年份的字串（`false`）。
- 如需詳細資訊，請參閱[代表具有多個紀元之行事曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`-支援 "Gannen" 或 "1"<br/>僅支援 `true` "1" |
| **環境變數** | N/A | N/A |

## <a name="japanese-year-format"></a>日文年份格式

- 決定日本日曆紀元的第一年是否格式化為 "Gannen" 或數位。
- 預設值：將第一年份格式化為 "Gannen" （`false`）。
- 如需詳細資訊，請參閱[代表具有多個紀元之行事曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false` 格式為 "Gannen"<br/>`true` 格式為數字 |
| **環境變數** | N/A | N/A |
