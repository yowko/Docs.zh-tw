---
title: 程式碼樣式命名規則
description: 瞭解適用于命名程式碼專案的 .NET 程式碼樣式規則。
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE1006
- naming rules
helpviewer_keywords:
- IDE1006
- naming code style rules [EditorConfig]
- naming rules
- EditorConfig naming conventions
ms.openlocfilehash: 1fce275204b729b4d23729ca432e06a5a249620d
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065131"
---
# <a name="naming-rules"></a>命名規則

在您的檔案中 `.editorconfig` ，您可以定義 .net 程式設計語言程式碼專案 &mdash; （例如類別、屬性和方法）如何命名的命名規則 &mdash; 。 例如，您可以指定公用成員必須為大寫，或私用欄位必須以開頭 `_` 。

命名規則有三個元件：

* **符號群組** &mdash; 規則套用的符號群組。
* 要與規則相關聯的 **命名樣式** 。
* 強制慣例的嚴重性。

## <a name="general-syntax"></a>一般語法

若要定義命名規則、符號群組或命名樣式，請使用下列語法來設定一或多個屬性：

```ini
<kind>.<title>.<propertyName> = <propertyValue>
```

每個屬性只能設定一次，但某些設定允許多個逗號分隔值。

屬性的順序不重要。

### \<kind>

**\<kind>** 指定要定義的專案類型為 &mdash; 命名規則、符號群組或命名樣式， &mdash; 而且必須是下列其中一項：

| 若要設定的屬性 | 使用 \<kind> 值 | 範例 |
| --- | --- | -- |
| 命名規則 | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| 符號群組 | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| 命名樣式 | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

每種類型的定義 &mdash; [命名規則](#naming-rule-properties)、[符號群組](#symbol-group-properties)或[命名樣式](#naming-style-properties) &mdash; 都有自己支援的屬性，如下列各節所述。

### \<title>

**\<title>** 是您選擇的描述性名稱，可將多個屬性設定與單一定義產生關聯。 例如，下列屬性會產生兩個符號群組定義， `interface` 而且 `types` 每個都有兩個屬性設定。

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a>命名規則屬性

所有命名規則屬性都必須要有規則才會生效。

| 屬性 | 描述 |
| -- | -- |
| `symbols` | 符號群組的標題;命名規則將套用至此群組中的符號 |
| `style` | 應與此規則相關聯之命名樣式的標題 |
| `severity` |  設定用來強制執行命名規則的嚴重性。 將相關聯的值設定為其中一個可用的 [嚴重性層級](../configuration-options.md#severity-level)。<sup>1</sup> |

**注意：**

1. 只有在開發 Ide （例如 Visual Studio）中才遵守命名規則內的嚴重性規格。 C # 或 VB 編譯器無法理解這項設定，因此不會在組建期間遵守。 若要在組建上強制執行命名樣式規則，您應該改為使用程式 [代碼規則嚴重性](#rule-id-ide1006-naming-rule-violation)設定來設定嚴重性。 如需詳細資訊，請參閱此 [GitHub 問題](https://github.com/dotnet/roslyn/issues/44201)。

## <a name="symbol-group-properties"></a>符號群組屬性

您可以設定符號群組的下列屬性，以限制要包含在群組中的符號。 若要為單一屬性指定多個值，請以逗號分隔這些值。

| 屬性 | 描述 | 允許的值 | 必要 |
| -- | -- | -- | -- |
| `applicable_kinds` | 群組<sup>1</sup>中的符號種類 | `*`(請使用此值來指定所有符號)<br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | 是 |
| `applicable_accessibilities` | 群組中符號的存取範圍層級 | `*` (請使用此值來指定所有存取層級)<br/>`public`<br/>`internal` 或 `friend`<br/>`private`<br/>`protected`<br/>`protected_internal` 或 `protected_friend`<br/>`private_protected`<br/>`local` 在方法內定義的符號 ()  | 是 |
| `required_modifiers` | 僅符合具有 _所有_ 指定修飾詞 <sup>2</sup>的符號 | `abstract` 或 `must_inherit`<br/>`async`<br/>`const`<br/>`readonly`<br/>`static` 或 `shared` <sup>3</sup> | 否 |

**注意：**

1. 目前不支援元組成員 `applicable_kinds` 。
2. 符號群組符合屬性中的 _所有_ 修飾詞 `required_modifiers` 。  如果您省略這個屬性，則不需要任何特定的修飾詞來進行比對。 這表示不論是否套用此規則，符號的修飾詞都不會造成影響。
3. 如果您的群組具有 `static` 或 `shared` 在 `required_modifiers` 屬性中，則群組也會包含 `const` 符號，因為它們是隱含的 `static` / `Shared` 。 但是，如果您不想要將 `static` 命名規則套用至 `const` 符號，可以使用的符號群組來建立新的命名規則 `const` 。

## <a name="naming-style-properties"></a>命名樣式屬性

命名樣式會定義您想要使用規則強制執行的慣例。 例如：

* 大寫 `PascalCase`
* 開頭為 `m_`
* 結尾為 `_g`
* 分隔單字和 `__`

您可以針對命名樣式來設定下列屬性：

| 屬性 | 描述 | 允許的值 | 必要 |
| -- | -- | -- | -- |
| `capitalization` | 符號內文字的大小寫樣式 | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | 是<sup>1</sup> |
| `required_prefix` | 必須以這些字元開頭 | | 否 |
| `required_suffix` | 必須以這些字元結尾 | | 否 |
| `word_separator` | 符號內的文字必須以這個字元分隔 | | 否 |

**注意：**

1. 您必須將大寫樣式指定為您命名樣式的一部分，否則您的命名樣式可能會遭到忽略。

## <a name="rule-order"></a>規則順序

在 EditorConfig 檔案中定義命名規則的順序並不重要。 系統會根據規則本身的定義自動排序命名規則。 [EditorConfig Language Service 延伸](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)模組可以分析 EditorConfig 檔和報表案例，其中的規則順序與編譯器將在執行時間使用的情況不同。

> [!NOTE]
>
> 如果您使用的 Visual Studio 版本早于 Visual Studio 2019 16.2 版，則在 EditorConfig 檔中，應將命名規則從最特定到最不明確的順序排序。 第一個遇到的可套用規則，會是唯一套用的規則。 但是，如果有多個具有相同名稱的規則 *屬性*，則最近找到具有該名稱的屬性優先。 如需詳細資訊，請參閱[檔案階層和優先順序](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence)。

## <a name="default-naming-styles"></a>預設命名樣式

如果您未指定任何自訂命名規則，則會使用下列預設樣式：

- 針對具有 `public`、`private`、`internal`、`protected` 或 `protected_internal` 存取範圍的類別、結構、列舉、屬性及事件，預設的命名樣式為 Pascal 命名法。

- 針對具有 `public`、`private`、`internal`、`protected` 或 `protected_internal` 存取範圍的介面，預設的命名樣式為 Pascal 命名法，且必須具有前置詞 **I**。

## <a name="code-rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a>程式碼規則識別碼： `IDE1006 (Naming rule violation)`

所有命名選項都有規則識別碼 `IDE1006` 和標題 `Naming rule violation` 。 您可以使用下列語法，在 EditorConfig 檔案中全域設定命名違規的嚴重性：

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

嚴重性值必須是 `warning` 或 `error` [在組建時強制執行](../overview.md#code-style-analysis)。 如需所有可能的嚴重性值，請參閱 [嚴重性層級](../configuration-options.md#severity-level)。

## <a name="example"></a>範例

下列 .editorconfig 檔案所包含的命名慣例指定公用屬性、方法、欄位、事件及委派必須為大寫。 請注意，此命名慣例指定了多種要套用規則的符號類型，並使用逗號分隔值。

```ini
[*.{cs,vb}]

# Defining the 'public_symbols' symbol group
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

# Defining the `first_word_upper_case_style` naming style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

# Defining the `public_members_must_be_capitalized` naming rule, by setting the symbol group to the 'public symbols' symbol group,
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
# setting the naming style to the `first_word_upper_case_style` naming style,
dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
# and setting the severity.
dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

## <a name="see-also"></a>另請參閱

- [語言規則](language-rules.md)
- [格式化規則](formatting-rules.md)
- [Roslyn 命名規則](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [.NET 程式碼樣式規則參考](index.md)
