---
title: 全球化 config 設定
description: 瞭解設定 .NET Core 應用程式全球化層面的執行時間設定，例如，它如何剖析日文日期。
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: 2561e66e6d18cb4036b0719f7e34ea66540fe095
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703123"
---
# <a name="run-time-configuration-options-for-globalization"></a>全球化的執行時間設定選項

## <a name="invariant-mode"></a>不變模式

- 判斷 .NET Core 應用程式是否以全球化不變模式執行，而不需要存取特定文化特性的資料和行為。
- 預設值：執行具有文化特性資料存取權的應用程式（ `false` ）。
- 如需詳細資訊，請參閱[.Net Core 全球化不變模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Globalization.Invariant` | `false`-文化特性資料的存取權<br/>`true`-在不變模式下執行 |
| **MSBuild 屬性** | `InvariantGlobalization` | `false`-文化特性資料的存取權<br/>`true`-在不變模式下執行 |
| **環境變數** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`-文化特性資料的存取權<br/>`1`-在不變模式下執行 |

### <a name="examples"></a>範例

*.runtimeconfig.json json*檔案：

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

## <a name="era-year-ranges"></a>紀元年份範圍

- 判斷支援多個紀元之行事曆的範圍檢查是否會放寬，或是否會擲回紀元日期範圍溢位的日期 <xref:System.ArgumentOutOfRangeException> 。
- 預設值：範圍檢查是寬鬆的（ `false` ）。
- 如需詳細資訊，請參閱行事[曆、紀元和日期範圍：寬鬆範圍檢查](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`-寬鬆範圍檢查<br/>`true`-溢位造成例外狀況 |
| **環境變數** | N/A | N/A |

## <a name="japanese-date-parsing"></a>日文日期剖析

- 判斷在年份中包含 "1" 或 "Gannen" 的字串是否已成功剖析，或是否只支援 "1"。
- 預設值：剖析包含 "1" 或 "Gannen" 做為年份（）的字串 `false` 。
- 如需詳細資訊，請參閱[代表具有多個紀元之行事曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`-支援 "Gannen" 或 "1"<br/>`true`-僅支援 "1" |
| **環境變數** | N/A | N/A |

## <a name="japanese-year-format"></a>日文年份格式

- 決定日本日曆紀元的第一年是否格式化為 "Gannen" 或數位。
- 預設值：將第一年格式化為 "Gannen" （ `false` ）。
- 如需詳細資訊，請參閱[代表具有多個紀元之行事曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`-格式為 "Gannen"<br/>`true`-格式為數字 |
| **環境變數** | N/A | N/A |

## <a name="nls"></a>NLS

- 判斷 .NET 是否針對 Windows 應用程式使用適用于 Unicode （ICU）全球化 Api 的國家語言支援（NLS）或國際元件。 根據預設，.NET 5.0 和更新版本會在 Windows 10 2019 更新和更新版本上使用 ICU 全球化 Api。
- 如果您省略此設定，.NET 預設會使用 ICU 全球化 Api。 這相當於將值設定為 `false` 。
- 如需詳細資訊，請參閱[全球化 api 在 Windows 上使用 ICU 程式庫](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows)。

| | 設定名稱 | 值 | 引導 |
| - | - | - | - |
| **.runtimeconfig.json json** | `System.Globalization.UseNls` | `false`-使用 ICU 全球化 Api<br/>`true`-使用 NLS 全球化 Api | .NET 5。0 |
| **環境變數** | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | `false`-使用 ICU 全球化 Api<br/>`true`-使用 NLS 全球化 Api | .NET 5。0 |
