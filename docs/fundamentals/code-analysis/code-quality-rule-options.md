---
title: 程式碼品質規則設定選項
description: 瞭解如何指定程式碼品質規則的其他設定選項。
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: af2984e73c554e8a1e1b32df9460933f86cc41be
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "96585291"
---
# <a name="code-quality-rule-configuration-options"></a>程式碼品質規則設定選項

除了設定 [嚴重性](configuration-options.md#severity-level)以外，程式 *代碼品質* 規則還有其他設定選項。 例如，每個程式碼品質分析器都可以設定為僅套用至程式碼基底的特定部分。 您可以藉由將機碼/值組新增至 [EditorConfig](https://editorconfig.org) 您指定規則嚴重性和一般編輯器喜好設定的相同檔案，來指定這些選項。

## <a name="option-scopes"></a>選項範圍

您可以針對規則類別 (（例如，安全性或設計) ）或特定規則，設定所有規則的每個精簡選項。

### <a name="all-rules"></a>所有規則

設定 *所有* 規則選項的語法如下：

|語法|範例|
|-|-|
| dotnet_code_quality。選項名稱 = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>規則類別

為規則 *類別* 設定選項的語法 (例如 [命名]、[設計] 或 [效能) ]，如下所示：

|語法|範例|
|-|-|
| dotnet_code_quality。RuleCategory. 選項名稱 = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>特定規則

設定 *特定* 規則選項的語法如下：

|語法|範例|
|-|-|
| dotnet_code_quality。RuleId. 選項名稱 = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="options"></a>選項。

本節列出一些可用的選項。 若要查看可用選項的完整清單，請參閱 [分析器](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)設定。

### <a name="api_surface"></a>api_surface

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 要分析的 API 介面的哪個部分 | `public`<br/>`internal` 或 `friend`<br/>`private`<br/>`all`<br/><br/>以逗號 ( 分隔多個值，)  | `public` | [CA1000](quality-rules/ca1000.md) [ca1003 必須](quality-rules/ca1003.md) [CA1008](quality-rules/ca1008.md) [CA1010](quality-rules/ca1010.md)<br/>[CA1012](quality-rules/ca1012.md) [ca1024 建議](quality-rules/ca1024.md) [ca1027 必須](quality-rules/ca1027.md) [CA1028](quality-rules/ca1028.md)<br/>[Ca1030 建議](quality-rules/ca1030.md) [ca1036 必須](quality-rules/ca1036.md) [CA1040](quality-rules/ca1040.md) [CA1041](quality-rules/ca1041.md)<br/>[Ca1043 必須](quality-rules/ca1043.md) [CA1044](quality-rules/ca1044.md) [CA1051](quality-rules/ca1051.md) [CA1052](quality-rules/ca1052.md)<br/>[CA1054](quality-rules/ca1054.md) [CA1055](quality-rules/ca1055.md) [CA1056](quality-rules/ca1056.md) [CA1058](quality-rules/ca1058.md)<br/>[Ca1063 必須](quality-rules/ca1063.md) [CA1708](quality-rules/ca1708.md) [CA1710](quality-rules/ca1710.md) [CA1711](quality-rules/ca1711.md)<br/>[CA1714](quality-rules/ca1714.md) [CA1715](quality-rules/ca1715.md) [CA1716](quality-rules/ca1716.md) [CA1717](quality-rules/ca1717.md)<br/>[CA1720](quality-rules/ca1720.md) [CA1721](quality-rules/ca1721.md) [CA1725](quality-rules/ca1725.md) [ca1801 必須](quality-rules/ca1801.md)<br/>[Ca1802 建議](quality-rules/ca1802.md) [>ca1815](quality-rules/ca1815.md) [CA1819](quality-rules/ca1819.md) [CA2217](quality-rules/ca2217.md)<br/>[CA2225](quality-rules/ca2225.md) [CA2226](quality-rules/ca2226.md) [CA2231](quality-rules/ca2231.md) [ca2234 必須](quality-rules/ca2234.md)<br/>|

### <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 是否忽略不會傳回值的非同步方法 | `true`<br/>`false` | `false` | [CA2007](quality-rules/ca2007.md) |

> [!NOTE]
> 此選項是 `skip_async_void_methods` 以較早的版本命名。

### <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 是否要排除規則中的單一字元 [類型參數](../../csharp/programming-guide/generics/generic-type-parameters.md) ， `S` 例如： `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](quality-rules/ca1715.md) |

> [!NOTE]
> 此選項是 `allow_single_letter_type_parameters` 以較早的版本命名。

### <a name="output_kind"></a>output_kind

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 指定應分析產生此類型元件之專案中的程式碼 | 列舉的一或多個欄位 <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>以逗號 ( 分隔多個值，)  | 所有輸出種類 | [CA2007](quality-rules/ca2007.md) |

### <a name="required_modifiers"></a>required_modifiers

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 指定應分析之 Api 的必要修飾詞 | 下列允許的修飾詞資料表中有一或多個值<br/><br/>以逗號 ( 分隔多個值，)  | 相依于每個規則 | [CA1802](quality-rules/ca1802.md) |

| 允許的修飾詞 | 摘要 |
| --- | --- |
| `none` | 無修飾元需求 |
| `static` 或 `Shared` | 必須 `static` `Shared` 在 Visual Basic 中宣告為 ()  |
| `const` | 必須宣告為 `const` |
| `readonly` | 必須宣告為 `readonly` |
| `abstract` | 必須宣告為 `abstract` |
| `virtual` | 必須宣告為 `virtual` |
| `override` | 必須宣告為 `override` |
| `sealed` | 必須宣告為 `sealed` |
| `extern` | 必須宣告為 `extern` |
| `async` | 必須宣告為 `async` |

### <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 是否要跳過 `this` 擴充方法的參數分析 | `true`<br/>`false` | `false` | [CA1062](quality-rules/ca1062.md) |

### <a name="null_check_validation_methods"></a>null_check_validation_methods

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 驗證傳遞給方法之引數的 null 檢查驗證方法名稱不是 null | 允許的方法名稱格式 (以 `|`) 分隔：<br/> -僅限方法名稱 (包含名稱的所有方法，不論包含的類型或命名空間為何) <br/> -符號 [檔識別碼格式](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)的完整名稱，具有選擇性的 `M:` 前置詞 | 無 | [CA1062](quality-rules/ca1062.md) |

### <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 其他字串格式化方法的名稱 | 允許的方法名稱格式 (以 `|`) 分隔：<br/> -僅限方法名稱 (包含名稱的所有方法，不論包含的類型或命名空間為何) <br/> -符號 [檔識別碼格式](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)的完整名稱，具有選擇性的 `M:` 前置詞 | 無 | [CA2241](quality-rules/ca2241.md) |

### <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 類型的名稱，因此會排除型別及其所有衍生型別以進行分析 | 允許的符號名稱格式 (以 `|`) 分隔：<br/> -僅限類型名稱 (包含名稱的所有類型，不論包含的類型或命名空間為何) <br/> -符號 [檔識別碼格式](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)的完整名稱，具有選擇性的 `T:` 前置詞 | 無 | [CA1303](quality-rules/ca1303.md) |

### <a name="excluded_symbol_names"></a>excluded_symbol_names

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 排除用於分析的符號名稱 | 允許的符號名稱格式 (以 `|`) 分隔：<br/> -僅限符號名稱 (包含名稱的所有符號，不論包含的類型或命名空間為何) <br/> -符號 [檔識別碼格式](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)的完整限定名稱。 每個符號名稱都需要符號類型前置詞，例如 `M:` 方法的前置詞、 `T:` 類型的前置詞，以及 `N:` 命名空間的前置詞。<br/> - `.ctor`針對函式和靜態函式 `.cctor` | 無 | [CA1062](quality-rules/ca1062.md) [CA1303](quality-rules/ca1303.md) [CA2000](quality-rules/ca2000.md) [ca2100 必須](quality-rules/ca2100.md) [CA2301](quality-rules/ca2301.md) [CA2302](quality-rules/ca2302.md)<br/>[CA2311](quality-rules/ca2311.md) [CA2312](quality-rules/ca2312.md) [CA2321](quality-rules/ca2321.md) [CA2322](quality-rules/ca2322.md) [CA2327](quality-rules/ca2327.md) [CA2328](quality-rules/ca2328.md)<br/>[CA2329](quality-rules/ca2329.md) [CA2330](quality-rules/ca2330.md) [CA3001](quality-rules/ca3001.md) [CA3002](quality-rules/ca3002.md) [CA3003](quality-rules/ca3003.md) [CA3004](quality-rules/ca3004.md)<br/>[CA3005](quality-rules/ca3005.md) [CA3006](quality-rules/ca3006.md) [CA3007](quality-rules/ca3007.md) [CA3008](quality-rules/ca3008.md) [CA3009](quality-rules/ca3009.md) [CA3010](quality-rules/ca3010.md)<br/>[CA3011](quality-rules/ca3011.md) [CA3012](quality-rules/ca3012.md) [CA5361](quality-rules/ca5361.md) CA5376 CA5377 [CA5378](quality-rules/ca5378.md)<br/>[CA5380](quality-rules/ca5380.md) [CA5381](quality-rules/ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](quality-rules/ca5389.md) CA5390 |

### <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| 描述 | 允許的值 | 預設值 | 可設定的規則 |
| - | - | - | - |
| 分析內容中不允許的符號名稱 | 允許的符號名稱格式 (以 `|`) 分隔：<br/> -僅限符號名稱 (包含名稱的所有符號，不論包含的類型或命名空間為何) <br/> -符號 [檔識別碼格式](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)的完整限定名稱。 每個符號名稱都需要符號類型前置詞，例如 `M:` 方法的前置詞、 `T:` 類型的前置詞，以及 `N:` 命名空間的前置詞。<br/> - `.ctor`針對函式和靜態函式 `.cctor` | 無 | [CA1031](quality-rules/ca1031.md) |
