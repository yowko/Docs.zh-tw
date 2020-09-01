---
description: override 修飾詞 - C# 參考
title: override 修飾詞 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 51ca806310214981b7ff24a796fe078d902dca4d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134454"
---
# <a name="override-c-reference"></a>override (C# 參考)

需要 `override` 修飾詞才能夠擴充或修改繼承方法、屬性、索引子或事件的抽象或虛擬實作。

## <a name="example"></a>範例

在此範例中， `Square` 類別必須提供覆寫的實作為， `GetArea` 因為 `GetArea` 是繼承自抽象 `Shape` 類：

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

`override` 方法提供繼承自基底類別的成員新實作。 `override` 宣告覆寫的方法稱之為覆寫基底方法。 覆寫基底方法必須和 `override` 方法有相同的簽章。 如需繼承的資訊，請參閱[繼承](../../programming-guide/classes-and-structs/inheritance.md)。

您無法覆寫非虛擬或靜態方法。 覆寫基底方法必須是 `virtual`、`abstract` 或 `override`。

`override` 宣告不能變更 `virtual` 方法的存取範圍。 `override` 方法和 `virtual` 方法都必須具有相同的[存取層級修飾詞](access-modifiers.md)。

您不能使用 `new`、`static` 或 `virtual` 修飾詞來修改 `override` 方法。

要覆寫的屬性宣告必須指定和繼承屬性完全相同的存取修飾詞、型別和名稱，而覆寫的屬性必須是 `virtual`、`abstract` 或 `override`。

如需如何使用關鍵字的詳細資訊 `override` ，請參閱使用 [Override 和 new 關鍵字進行版本控制](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ，以及 [瞭解使用 override 和 new 關鍵字](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)的時機。

## <a name="example"></a>範例

本例會定義名為 `Employee` 的基底類別，以及名為 `SalesEmployee` 的衍生類別。 `SalesEmployee` 類別包含額外的欄位 `salesbonus`，並會覆寫方法 `CalculatePay` 以將其納入考量。

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [繼承](../../programming-guide/classes-and-structs/inheritance.md)
- [C # 關鍵字](index.md)
- [修飾詞](index.md)
- [抽象](abstract.md)
- [virtual](virtual.md)
- [新的 (修飾詞) ](new-modifier.md)
- [多型](../../programming-guide/classes-and-structs/polymorphism.md)
