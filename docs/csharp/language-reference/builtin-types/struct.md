---
title: 結構類型 - C# 引用
ms.date: 02/24/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: b85d0df086f3ca65ed995594dd374286e1c3ba5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847725"
---
# <a name="structure-types-c-reference"></a>結構類型（C# 參考）

*結構類型*（或*結構類型*）是一種可以封裝資料和相關功能[的數值型別](value-types.md)。 使用 關鍵字`struct`定義結構類型：

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

結構類型具有*值語義*。 也就是說，結構類型的變數包含類型的實例。 預設情況下，在賦值時複製變數值，將參數傳遞給方法，並返回方法結果。 對於結構類型變數，將複製類型的實例。 有關詳細資訊，請參閱[數值型別](value-types.md)。

通常，使用結構類型來設計提供很少或沒有行為的小型以資料為中心的類型。 例如，.NET 使用結構類型來表示數位（[整數](integral-numeric-types.md)和[實數](floating-point-numeric-types.md)）、[布林值](bool.md)[、Unicode 字元](char.md)、[時間實例](xref:System.DateTime)。 如果您專注于類型的行為，請考慮定義[類](../keywords/class.md)。 類類型具有*引用語義*。 也就是說，類類型的變數包含對類型實例的引用，而不是實例本身。

## <a name="limitations-with-the-design-of-a-structure-type"></a>結構類型設計的限制

設計結構類型時，具有與[類](../keywords/class.md)類型相同的功能，但以下情況除外：

- 不能聲明無參數建構函式。 每個結構類型都已提供一個隱式無參數建構函式，該建構函式組建類型的[預設值](default-values.md)。

- 不能在其聲明上初始化實例欄位或屬性。 但是，您可以在其聲明上初始化[靜態](../keywords/static.md)或[const](../keywords/const.md)欄位或靜態屬性。

- 結構類型的建構函式必須初始化類型的所有實例欄位。

- 結構類型不能從其他類或結構類型繼承，也不能是類的基礎。 但是，結構類型可以實現[介面](../keywords/interface.md)。

- 不能在結構類型中聲明[終端子](../../programming-guide/classes-and-structs/destructors.md)。

## <a name="instantiation-of-a-structure-type"></a>結構類型的具現化

在 C# 中，必須先初始化聲明變數，然後才能使用它。 因為結構類型變數不能`null`（除非它是可 null[數值型別的](nullable-value-types.md)變數），因此必須具現化相應類型的實例。 有幾種方法可以做到這一點。

通常，通過使用運算子調用適當的建構函式來[`new`](../operators/new-operator.md)具現化結構類型。 每個結構類型至少有一個建構函式。 這是一個隱式無參數建構函式，它組建類型的[預設值](default-values.md)。 您還可以使用[預設](../operators/default.md)運算子或文本組建類型的預設值。

如果結構類型的所有實例欄位都可訪問，也可以在沒有`new`運算子的情況下具現化它。 在這種情況下，您必須在首次使用實例之前初始化所有實例欄位。 下列範例顯示如何執行該項工作：

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

在[內置數值型別](value-types.md#built-in-value-types)的情況下，使用相應的文本指定類型的值。

## <a name="passing-structure-type-variables-by-reference"></a>通過引用傳遞結構類型變數

將結構類型變數作為參數傳遞給方法或從方法返回結構類型值時，將複製結構類型的整個實例。 這可能會影響代碼在涉及大型結構類型的高性能方案中的性能。 可以通過引用傳遞結構類型變數來避免值複製。 使用[`ref`](../keywords/ref.md#passing-an-argument-by-reference)、[`out`](../keywords/out-parameter-modifier.md)或[`in`](../keywords/in-parameter-modifier.md)方法參數修改器指示必須通過引用傳遞參數。 使用[ref 返回](../../programming-guide/classes-and-structs/ref-returns.md)通過引用返回方法結果。 有關詳細資訊，請參閱[編寫安全高效的 C# 代碼](../../write-safe-efficient-code.md)。

## <a name="conversions"></a>轉換

對於任何結構類型，都存在與 和<xref:System.ValueType?displayProperty=nameWithType><xref:System.Object?displayProperty=nameWithType>類型轉換的[裝箱和取消裝箱](../../programming-guide/types/boxing-and-unboxing.md)轉換。 結構類型和它實現的任何介面之間也存在裝箱和取消裝箱轉換。

## <a name="c-language-specification"></a>C# 語言規格

有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的["結構"](~/_csharplang/spec/structs.md)部分。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [設計指南 - 在類和結構之間進行選擇](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [設計指南 - 結構設計](../../../standard/design-guidelines/struct.md)
- [類和結構](../../programming-guide/classes-and-structs/index.md)
