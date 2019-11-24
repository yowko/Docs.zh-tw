---
title: 使用結構 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 491ee0224ffa39262992f7f42d20e5f97560b73f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429491"
---
# <a name="using-structs-c-programming-guide"></a>Using structs (C# Programming Guide)

`struct` 類型很適合用於代表輕量型物件，例如 `Point`、 `Rectangle`和 `Color`。 雖然使用 [自動實作的屬性](../../language-reference/keywords/class.md) 可以輕鬆地將一個點表示為一個 [類別](./auto-implemented-properties.md)，但是在某些情節中 [結構](../../language-reference/keywords/struct.md) 可能會更有效率。 例如，如果您宣告含有 1000 個 `Point` 物件的陣列，您會配置額外的記憶體來參考每個物件；在此案例下，結構所耗用的記憶體會較少。 Because .NET already contains an object called <xref:System.Drawing.Point>, the struct in this example is named `Coords` instead.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

It is an error to define a parameterless constructor for a struct. 初始化結構主體中的執行個體欄位時也會發生錯誤。 您只能透過使用參數化建構函式、隱含的無參數建構函式、[物件初始設定式](object-and-collection-initializers.md)，或在宣告結構後個別存取成員，初始化可外部存取的結構成員。 任何私用或無法以其他方式存取的成員都需要建構函式的專屬使用。

當您使用 [new](../../language-reference/operators/new-operator.md) 運算子建立結構物件時，不僅會建立物件，還會根據[建構函式的簽章](constructors.md#constructor-syntax)呼叫適當的建構函式。 不同於類別，結構不需要使用 `new` 運算子就能具現化。 在此案例下，不會有建構函式呼叫，因此配置會更有效率。 不過，欄位會維持未指派狀態，而且必須等到所有欄位都初始化後才能使用物件。 這包括無法透過屬性取得或設定值。

If you instantiate a struct object using the parameterless constructor, all members are assigned according to their [default values](../../language-reference/keywords/default-values-table.md).

When writing a constructor with parameters for a struct, you must explicitly initialize all members; otherwise one or more members remain unassigned and the struct cannot be used, producing compiler error [CS0171](../../misc/cs0171.md).

不同於類別，結構沒有繼承。 結構無法繼承自另一個結構或類別，而且不能作為類別的基底。 不過，結構可以繼承自基底類別 <xref:System.Object>。 結構可以實作介面，而且其作法就跟類別一樣。

您無法使用關鍵字 `struct`宣告類別。 在 C# 中，類別和結構在語意上是不同的。 結構是實值類型，而類別是參考類型。 For more information, see [Value types](../../language-reference/keywords/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).

除非您需要參考類型語意，否則系統處理小型類別可能會更有效率 (如果您改為將其宣告為結構)。

## <a name="example-1"></a>範例 1

This example demonstrates `struct` initialization using both parameterless and parameterized constructors.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]

## <a name="example-2"></a>範例 2

此範例示範結構特有的功能。 其無須使用 `new` 運算子就能建立 Coords 物件。 如果您以 `class` 一字取代 `struct` 一字，將不會編譯程式。

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]

## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](index.md)
- [結構](structs.md)
