---
title: 全球化設定
description: 瞭解設定 .NET Core 應用程式全球化層面的執行時間設定，例如，如何剖析日文日期。
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: fc98e965093c28b75b9b66e4f1c9f147abd4680e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721905"
---
# <a name="run-time-configuration-options-for-globalization"></a>全球化的執行時間設定選項

## <a name="invariant-mode"></a>不變模式

- 判斷 .NET Core 應用程式是否以全球化非變異模式執行，而不需存取特定文化特性的資料和行為。
- 如果您省略此設定，則會執行應用程式並存取文化特性資料。 這相當於將值設定為 `false` 。
- 如需詳細資訊，請參閱 [.Net Core 全球化不變模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)。

| | 設定名稱 | 值 |
| - | - | - |
| **runtimeconfig.js開啟** | `System.Globalization.Invariant` | `false` -文化特性資料的存取權<br/>`true` -在不變模式中執行 |
| **MSBuild 屬性** | `InvariantGlobalization` | `false` -文化特性資料的存取權<br/>`true` -在不變模式中執行 |
| **環境變數** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0` -文化特性資料的存取權<br/>`1` -在不變模式中執行 |

### <a name="examples"></a>範例

*runtimeconfig.json* file：

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

- 決定是否要放寬支援多個紀元之行事曆的範圍檢查，或是否會擲回某紀元日期範圍溢位的日期 <xref:System.ArgumentOutOfRangeException> 。
- 如果您省略此設定，則會放寬範圍檢查。 這相當於將值設定為 `false` 。
- 如需詳細資訊，請參閱行事 [曆、紀元和日期範圍：寬鬆的範圍檢查](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)。

| | 設定名稱 | 值 |
| - | - | - |
| **runtimeconfig.js開啟** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false` -寬鬆範圍檢查<br/>`true` -溢位會造成例外狀況 |
| **環境變數** | N/A | N/A |

## <a name="japanese-date-parsing"></a>日文日期剖析

- 判斷是否成功剖析包含 "1" 或 "Gannen" 的字串，或是否只支援 "1"。
- 如果您省略此設定，則會成功剖析包含 "1" 或 "Gannen" 的字串。 這相當於將值設定為 `false` 。
- 如需詳細資訊，請參閱 [使用多個紀元表示日曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。

| | 設定名稱 | 值 |
| - | - | - |
| **runtimeconfig.js開啟** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false` -支援 "Gannen" 或 "1"<br/>`true` -只支援 "1" |
| **環境變數** | N/A | N/A |

## <a name="japanese-year-format"></a>日文年份格式

- 判斷日文日曆紀元的第一年是否格式化為 "Gannen" 或數位。
- 如果您省略此設定，則第一年的格式會是 "Gannen"。 這相當於將值設定為 `false` 。
- 如需詳細資訊，請參閱 [使用多個紀元表示日曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。

| | 設定名稱 | 值 |
| - | - | - |
| **runtimeconfig.js開啟** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false` -格式為 "Gannen"<br/>`true` -格式為數字 |
| **環境變數** | N/A | N/A |

## <a name="nls"></a>Nls

- 判斷 .NET 是否針對 Unicode (ICU) 適用于 Windows 應用程式的全球化 Api，使用國家語言支援 (NLS) 或國際元件。 .NET 5.0 和更新版本預設會在 Windows 10 2019 年5月更新和更新版本上使用 ICU 全球化 Api。
- 如果您省略此設定，.NET 預設會使用 ICU 全球化 Api。 這相當於將值設定為 `false` 。
- 如需詳細資訊，請參閱 [全球化 api 在 Windows 上使用 ICU 程式庫](../compatibility/globalization/5.0/icu-globalization-api.md)。

| | 設定名稱 | 值 | 推出的版本 |
| - | - | - | - |
| **runtimeconfig.js開啟** | `System.Globalization.UseNls` | `false` -使用 ICU 全球化 Api<br/>`true` -使用 NLS 全球化 Api | .NET 5。0 |
| **環境變數** | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | `false` -使用 ICU 全球化 Api<br/>`true` -使用 NLS 全球化 Api | .NET 5。0 |
