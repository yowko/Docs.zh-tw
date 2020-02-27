---
title: 結構類型- C#參考
ms.date: 02/24/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 6113912f176d2d7b68c77ff2e78a361b373ca31a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634866"
---
# <a name="structure-types-c-reference"></a>結構類型（C#參考）

*結構型*別（或*結構型*別）是可以封裝資料和相關功能的實[值型](value-types.md)別。 您可以使用 `struct` 關鍵字來定義結構類型：

[!code-csharp[struct example](~/samples/csharp/language-reference/builtin-types/StructType.cs#StructExample)]

結構類型具有*值的語義*。 也就是說，結構類型的變數會包含類型的實例。 根據預設，變數值會在指派時複製、將引數傳遞至方法，並傳回方法結果。 在結構類型變數的情況下，會複製類型的實例。 如需詳細資訊，請參閱實[數值型別](value-types.md)。

一般來說，您會使用結構類型來設計以資料為中心的小型類型，以提供些許或無行為。 例如，.NET 會使用結構類型來代表數位（[整數](integral-numeric-types.md)和[實數](floating-point-numeric-types.md)）、[布林值](bool.md)、 [Unicode 字元](char.md)和[時間實例](xref:System.DateTime)。 如果您將焦點放在類型的行為，請考慮定義[類別](../keywords/class.md)。 類別類型具有*參考語義*。 也就是說，類別類型的變數包含類型實例的參考，而不是實例本身。

## <a name="limitations-with-the-design-of-a-structure-type"></a>結構類型設計的限制

當您設計結構類型時，您具有與[類別](../keywords/class.md)類型相同的功能，但有下列例外狀況：

- 您不能宣告無參數的函式。 每個結構類型已經提供隱含的無參數的函式，以產生類型的[預設值](default-values.md)。

- 您無法在其宣告中初始化實例欄位或屬性。 不過，您可以在其宣告中初始化[靜態](../keywords/static.md)或[常數](../keywords/const.md)欄位或靜態屬性。

- 結構類型的「構造函式」必須初始化該類型的所有實例欄位。

- 結構類型無法繼承自其他類別或結構類型，而且不能是類別的基底。 不過，結構類型可以執行[介面](../keywords/interface.md)。

- 您不[能在結構類型中宣告](../../programming-guide/classes-and-structs/destructors.md)完成項。

## <a name="instantiation-of-a-structure-type"></a>結構類型的具現化

在C#中，您必須先初始化已宣告的變數，才能使用它。 因為結構類型變數無法 `null` （除非它是[可為 null 的實數值型別](nullable-value-types.md)的變數），所以您必須具現化對應類型的實例。 有幾種方式可以這麼做。

通常，您可以使用[`new`](../operators/new-operator.md)運算子來呼叫適當的處理常式，以具現化結構類型。 每個結構類型都至少有一個函式。 這是隱含的無參數的函式，它會產生類型的[預設值](default-values.md)。 您也可以使用[預設](../operators/default.md)的運算子或常值來產生類型的預設值。

如果結構類型的所有實例欄位都可存取，您也可以在不使用 `new` 運算子的情況下將它具現化。 在此情況下，您必須在第一次使用實例之前，先初始化所有實例欄位。 下列範例顯示如何執行該項工作：

[!code-csharp[without new](~/samples/csharp/language-reference/builtin-types/StructType.cs#WithoutNew)]

在內[建實數值型別](value-types.md#built-in-value-types)的情況下，請使用對應的常值來指定類型的值。

## <a name="passing-structure-type-variables-by-reference"></a>以傳址方式傳遞結構型別變數

當您將結構型別變數當做引數傳遞至方法，或從方法傳回結構型別值時，會複製結構型別的整個實例。 這可能會影響您的程式碼在涉及大型結構類型的高效能案例中的效能。 您可以透過傳址方式傳遞結構型別變數，以避免值複製。 您可以使用[`ref`](../keywords/ref.md#passing-an-argument-by-reference)、 [`out`](../keywords/out-parameter-modifier.md)或[`in`](../keywords/in-parameter-modifier.md)方法參數修飾詞，來指出引數必須以傳址方式傳遞。 使用[ref](../../programming-guide/classes-and-structs/ref-returns.md) return 傳回以傳址方式傳回的方法結果。 如需詳細資訊，請參閱[撰寫安全C#且有效率](../../write-safe-efficient-code.md)的程式碼。

## <a name="conversions"></a>轉換

針對任何結構類型，會在 <xref:System.ValueType?displayProperty=nameWithType> 和 <xref:System.Object?displayProperty=nameWithType> 類型之間存在進行的[裝箱和取消裝箱](../../programming-guide/types/boxing-and-unboxing.md)轉換。 結構型別和它所執行的任何介面之間也有一個裝箱和取消裝箱轉換。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)的[結構](~/_csharplang/spec/structs.md)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [設計方針-在類別和結構之間選擇](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [設計方針-結構設計](../../../standard/design-guidelines/struct.md)
- [類別和結構](../../programming-guide/classes-and-structs/index.md)
