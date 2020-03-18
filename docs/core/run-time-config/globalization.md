---
title: 全球化配置設置
description: 瞭解配置 .NET Core 應用的全球化方面的運行時設置，例如，它如何分析日語日期。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733461"
---
# <a name="run-time-configuration-options-for-globalization"></a>全球化的運行時配置選項

## <a name="invariant-mode"></a>不變模式

- 確定 .NET Core 應用是否以全球化不變模式運行，而不訪問特定于區域性的資料和行為，或者它是否有權訪問文化資料。
- 預設值：使用訪問文化資料 （）`false`運行應用。
- 有關詳細資訊，請參閱[.NET 核心全球化不變模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | `System.Globalization.Invariant` | `false`- 獲取文化資料<br/>`true`- 在不變模式下運行 |
| **MSBuild 屬性** | `InvariantGlobalization` | `false`- 獲取文化資料<br/>`true`- 在不變模式下運行 |
| **環境變數** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`- 獲取文化資料<br/>`1`- 在不變模式下運行 |

### <a name="examples"></a>範例

*運行時配置.json*檔：

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

專案檔：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a>時代年份範圍

- 確定是否放寬了對支援多個紀元日曆的日曆的範圍檢查，或者溢出一個時代日期範圍的日期是否引發 。 <xref:System.ArgumentOutOfRangeException>
- 預設值：放寬範圍檢查 （）。`false`
- 有關詳細資訊，請參閱[日曆、時數和日期範圍：放寬範圍檢查](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`- 輕鬆範圍檢查<br/>`true`- 溢出導致異常 |
| **環境變數** | N/A | N/A |

## <a name="japanese-date-parsing"></a>日語日期解析

- 確定在年份解析時包含"1"或"Gannen"的字串是否成功解析，或者是否僅支援"1"。
- 預設值：將包含"1"或"Gannen"作為年份 （）`false`的字串解析。
- 有關詳細資訊，請參閱[在具有多個時代曆的日曆中表示日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`- 支援"甘甯"或"1"<br/>`true`- 僅支援"1" |
| **環境變數** | N/A | N/A |

## <a name="japanese-year-format"></a>日語年格式

- 確定日本日曆時代的第一年是格式化為"Gannen"還是數位。
- 預設值：將第一年設置為"Gannen"`false`（） 。
- 有關詳細資訊，請參閱[在具有多個時代曆的日曆中表示日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`- 格式為"甘甯"<br/>`true`- 格式為數字 |
| **環境變數** | N/A | N/A |
