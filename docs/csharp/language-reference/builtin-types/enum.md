---
title: '列舉型別-c # 參考'
description: '瞭解代表選擇或組合選項的 c # 列舉類型'
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
ms.openlocfilehash: 930efdbdc6a20ea301331c1ce6fc664da43bfc5f
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471846"
---
# <a name="enumeration-types-c-reference"></a>列舉類型 (c # 參考) 

*列舉型*別 (或*列舉型*別) 是一組由基礎[整數數值](integral-numeric-types.md)型別之指定常數所定義的實[值型](value-types.md)別。 若要定義列舉型別，請使用 `enum` 關鍵字並指定 *列舉成員*的名稱：

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

根據預設，列舉成員的相關常數值為類型 `int` ; 它們是從零開始，並依照定義文字順序遞增一。 您可以明確地指定任何其他 [整數數值](integral-numeric-types.md) 類型作為列舉型別的基礎型別。 您也可以明確地指定相關聯的常數值，如下列範例所示：

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

您無法在列舉類型的定義內定義方法。 若要將功能加入至列舉型別，請建立 [擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。

列舉類型的預設值 `E` 是運算式所產生的值 `(E)0` ，即使零沒有對應的列舉成員。

您可以使用列舉類型來代表一組互斥值或選擇組合的選項。 若要表示選項的組合，請將列舉類型定義為位旗標。

## <a name="enumeration-types-as-bit-flags"></a>作為位元旗標的列舉類型

如果您想要列舉型別代表選項的組合，請定義這些選擇的列舉成員，讓個別的選擇是位欄位。 也就是說，這些列舉成員的關聯值應該是兩個的乘冪。 然後，您可以使用[位邏輯運算子， `|` 或 `&` ](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators)分別合併選項或交集組合的選項。 若要指出列舉型別會宣告位欄位，請將 [Flags](xref:System.FlagsAttribute) 屬性套用至其中。 如下列範例所示，您也可以在列舉類型的定義中包含一些典型的組合。

[!code-csharp[enum flags](snippets/shared/EnumType.cs#Flags)]

如需詳細資訊和範例，請參閱 [api 參考] 頁面的 [ <xref:System.FlagsAttribute?displayProperty=nameWithType> api 參考] 頁面和 [ [非獨佔成員] 和 [旗標屬性](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) ] 區段 <xref:System.Enum?displayProperty=nameWithType> 。

## <a name="the-systemenum-type-and-enum-constraint"></a>System.string 型別和列舉條件約束

此 <xref:System.Enum?displayProperty=nameWithType> 類型是所有列舉類型的抽象基類。 它會提供數種方法來取得列舉型別和其值的相關資訊。 如需詳細資訊和範例，請參閱 <xref:System.Enum?displayProperty=nameWithType> API 參考頁面。

從 c # 7.3 開始，您可以 `System.Enum` 在稱為 [列舉條件約束](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints) 的基類條件約束 (中使用，) 指定型別參數為列舉型別。

## <a name="conversions"></a>轉換

對於任何列舉型別，列舉型別與其基礎整數型別之間存在明確的轉換。 如果您將列舉值 [轉換](../operators/type-testing-and-cast.md#cast-expression) 為其基礎類型，結果會是列舉成員的相關整數值。

[!code-csharp[enum conversions](snippets/shared/EnumType.cs#Conversions)]

您 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 可以使用方法來判斷列舉型別是否包含具有特定關聯值的列舉成員。

針對任何列舉型別，會分別存在對類型的 [裝箱和取消](../../programming-guide/types/boxing-and-unboxing.md) 加入轉換 <xref:System.Enum?displayProperty=nameWithType> 。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [列舉](~/_csharplang/spec/enums.md)
- [列舉值和作業](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [列舉邏輯運算子](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [列舉比較運算子](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [明確列舉轉換](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [隱含列舉轉換](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [列舉格式字串](../../../standard/base-types/enumeration-format-strings.md)
- [設計指導方針-列舉設計](../../../standard/design-guidelines/enum.md)
- [設計指導方針-列舉命名慣例](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [switch 陳述式](../keywords/switch.md)
