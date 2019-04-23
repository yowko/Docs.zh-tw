---
title: C# 中的字串插補
description: 了解如何使用字串插補，在 C# 的結果字串中包含已格式化的運算式結果。
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 5a66ba9215579a459b543a24ece338ffbbfd9aea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58920710"
---
# <a name="string-interpolation-in-c"></a>C\# 中的字串插補

本教學課程會示範如何使用[字串插補](../language-reference/tokens/interpolated.md)進行格式化，並將運算式結果包含在結果字串中。 這些範例假設您熟悉 C# 基本概念和 .NET 類型格式設定。 如果您不熟悉字串插補或 .NET 類型格式設定，請先參閱[互動式字串插補教學課程](exploration/interpolated-strings.yml)。 如需在 .NET 中格式化類型的詳細資訊，請參閱[在 .NET 中格式化類型](../../standard/base-types/formatting-types.md)主題。

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>簡介

[字串插補](../language-reference/tokens/interpolated.md)功能是以[複合格式](../../standard/base-types/composite-formatting.md)功能為基礎建置而成，可提供更容易理解且方便的語法，在結果字串中包含已格式化的運算式結果。

若要將字串常值識別為插入字串，請在其前面加上 `$` 符號。 您可以內嵌任何有效的 C# 運算式，以在插入字串中傳回值。 在下列範例中，只要評估運算式，其結果即會轉換成字串，並包含在結果字串中：

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

如範例所示，藉由用括號括住運算式，即可在插入字串中包含運算式：

```
{<interpolatedExpression>}
```

在編譯時期，插入字串通常會轉換成 <xref:System.String.Format%2A?displayProperty=nameWithType> 方法呼叫。 這也可讓[字串複合格式](../../standard/base-types/composite-formatting.md)功能的所有功能供您與插入字串一起使用。

如果分析的行為相當於串連，編譯器可以用 <xref:System.String.Format%2A?displayProperty=nameWithType> 替換 <xref:System.String.Concat%2A?displayProperty=nameWithType>。

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a>如何指定插入運算式的格式字串

在插入運算式後面接著冒號 (":") 和格式字串，即可指定運算式結果類型所支援的格式字串：

```
{<interpolatedExpression>:<formatString>}
```

下列範例會示範如何針對產生日期與時間或數值結果的運算式，指定標準和自訂的格式字串：

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

如需詳細資訊，請參閱[複合格式](../../standard/base-types/composite-formatting.md)主題的[格式字串元件](../../standard/base-types/composite-formatting.md#format-string-component)一節。 該節中提供了一些主題連結，以描述 .NET 基底類型所支援的標準和自訂格式字串。

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a>如何控制已格式化之插入運算式的欄位寬度和對齊

在插入運算式後面接著逗號 (",") 和常數運算式，即可指定已格式化之運算式結果的最小欄位寬度和對齊：

```
{<interpolatedExpression>,<alignment>}
```

如果 *alignment* 值是正數，已格式化的運算式結果為靠右對齊；如果是負數，則是靠左對齊。

如果您需要指定對齊和格式字串，請從對齊元件開始：

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

下列範例會示範如何指定對齊，並使用管道字元 ("|") 來分隔文字欄位：

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

如範例輸出所示，如果已格式化的運算式結果長度超過指定的欄位寬度，則會忽略 *alignment* 值。

如需詳細資訊，請參閱[複合格式](../../standard/base-types/composite-formatting.md)主題的[對齊元件](../../standard/base-types/composite-formatting.md#alignment-component)一節。

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>如何在插入字串中使用逸出序列

插入字串支援可用於一般字串常值中所有逸出序列。 如需詳細資訊，請參閱[字串逸出序列](../programming-guide/strings/index.md#string-escape-sequences)。

若要逐字解譯逸出序列，請使用[逐字](../language-reference/tokens/verbatim.md)字串常值。 逐字插入字串以 `$` 字元為開頭，後面接著 `@` 字元。

若要在結果字串中包含大括號 "{" 或 "}"，請使用兩個大括號 "{{" 或 "}}"。 如需詳細資訊，請參閱[複合格式](../../standard/base-types/composite-formatting.md)主題的[逸出大括號](../../standard/base-types/composite-formatting.md#escaping-braces)一節。

下列範例會示範如何在結果字串中包含大括號，並建構逐字插入字串：

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a>如何在插入運算式中使用三元條件運算子 `?:`

因為冒號 (":") 在插入運算式的項目中具有特殊意義，為了在運算式中使用[條件運算子](../language-reference/operators/conditional-operator.md)，請用括號括住運算式，如下列範例所示：

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>如何使用字串插補建立文化特性特有的結果字串

根據預設，插入字串會使用 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> 屬性針對所有格式設定作業所定義的目前文化特性。 請使用插入字串到 <xref:System.FormattableString?displayProperty=nameWithType> 執行個體的隱含轉換，並呼叫其 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法來建立文化特性特有的結果字串。 下列範例顯示如何執行該項工作：

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

如範例所示，您可以使用一個 <xref:System.FormattableString> 執行個體，針對各種文化特性產生多個結果字串。

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>如何建立使用不因文化特性而異的結果字串

除了 <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> 方法之外，您還可以使用靜態 <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> 方法將插入字串解析為 <xref:System.Globalization.CultureInfo.InvariantCulture> 的結果字串。 下列範例顯示如何執行該項工作：

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>結論

本教學課程描述了使用字串插補的常見案例。 如需字串插補的詳細資訊，請參閱[字串插補](../language-reference/tokens/interpolated.md)主題。 如需在 .NET 中格式化類型的詳細資訊，請參閱[在 .NET 中格式化類型](../../standard/base-types/formatting-types.md)和[複合格式](../../standard/base-types/composite-formatting.md)主題。

## <a name="see-also"></a>另請參閱

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [字串](../programming-guide/strings/index.md)
