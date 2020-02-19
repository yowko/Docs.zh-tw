---
title: 列舉類型- C#參考
description: 瞭解代表C#選擇或選擇組合的列舉類型
ms.date: 12/13/2019
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
- enum type [C#]
- enumeration type [C#]
- bit flags [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 4377d113a18d23c8a0f9a669e6112f1a8223cc79
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450865"
---
# <a name="enumeration-types-c-reference"></a>列舉類型（C#參考）

*列舉型*別（或*列舉型*別）是由基礎[整數數值](integral-numeric-types.md)類型的一組命名常數所定義的實[值型](value-types.md)別。 若要定義列舉類型，請使用 `enum` 關鍵字，並指定*列舉成員*的名稱：

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

根據預設，列舉成員的相關聯常數值是 `int`的類型;開頭為零，並依照定義文字順序增加一個。 您可以明確地指定任何其他[整數數值](integral-numeric-types.md)類型做為列舉類型的基礎類型。 您也可以明確指定相關聯的常數值，如下列範例所示：

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

您無法在列舉類型的定義內定義方法。 若要將功能加入至列舉類型，請建立[擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。

列舉型別的預設值 `E` 是運算式 `(E)0`所產生的值，即使零沒有對應的列舉成員也一樣。

您可以使用列舉類型，從一組互斥值或選擇組合來表示選擇。 若要代表選擇的組合，請將列舉類型定義為位旗標。

## <a name="enumeration-types-as-bit-flags"></a>作為位元旗標的列舉類型

如果您想要列舉類型來代表選擇的組合，請針對這些選擇定義列舉成員，讓個別的選擇是位欄位。 也就是說，這些列舉成員的相關聯值應該是兩個的乘冪。 然後，您可以使用[位邏輯運算子 `|` 或 `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) ，分別結合選擇或交集的選擇組合。 若要指出列舉類型會宣告位欄位，請將[Flags](xref:System.FlagsAttribute)屬性套用至其中。 如下列範例所示，您也可以在列舉類型的定義中包含一些一般組合。

[!code-csharp[enum flags](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Flags)]

如需詳細資訊和範例，請參閱 <xref:System.Enum?displayProperty=nameWithType> API 參考頁面的 <xref:System.FlagsAttribute?displayProperty=nameWithType> API 參考頁面和[非獨佔成員和 Flags 屬性](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute)一節。

## <a name="the-systemenum-type-and-enum-constraint"></a>System.string 類型和 enum 條件約束

<xref:System.Enum?displayProperty=nameWithType> 類型是所有列舉類型的抽象基類。 它提供了數種方法來取得列舉型別和其值的相關資訊。 如需詳細資訊和範例，請參閱 <xref:System.Enum?displayProperty=nameWithType> API 參考頁面。

從C# 7.3 開始，您可以在基類條件約束（也稱為[列舉條件約束](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)）中使用 `System.Enum`，以指定類型參數是列舉類型。

## <a name="conversions"></a>轉換

針對任何列舉型別，列舉型別與其基礎整數型別之間存在明確轉換。 如果您將列舉值[轉換](../operators/type-testing-and-cast.md#cast-operator-)為其基礎類型，則結果會是列舉成員的相關整數值。

[!code-csharp[enum conversions](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Conversions)]

使用 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 方法來判斷列舉類型是否包含具有特定相關聯值的列舉成員。

針對任何列舉類型，會分別存在與 <xref:System.Enum?displayProperty=nameWithType> 類型之間的[裝箱和取消裝箱](../../programming-guide/types/boxing-and-unboxing.md)轉換。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [列舉](~/_csharplang/spec/enums.md)
- [列舉值和作業](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [列舉邏輯運算子](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [列舉比較運算子](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [明確列舉轉換](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [隱含列舉轉換](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [列舉格式字串](../../../standard/base-types/enumeration-format-strings.md)
- [設計方針-列舉設計](../../../standard/design-guidelines/enum.md)
- [設計方針-列舉命名慣例](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [switch 陳述式](../keywords/switch.md)
