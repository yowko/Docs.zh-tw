---
description: override 修飾詞 - C# 參考
title: override 修飾詞 - C# 參考
ms.date: 10/22/2020
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 618200183348e68a4600adb9592a635f61f6a875
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434883"
---
# <a name="override-c-reference"></a>覆寫 (c # 參考) 

需要 `override` 修飾詞才能夠擴充或修改繼承方法、屬性、索引子或事件的抽象或虛擬實作。

在下列範例中， `Square` 類別必須提供的覆寫實作為， `GetArea` 因為 `GetArea` 是繼承自抽象 `Shape` 類：

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

`override`方法會提供繼承自基類之方法的新實作為。 `override` 宣告覆寫的方法稱之為覆寫基底方法。 方法的簽章必須與覆 `override` 寫基底方法的簽章相同。 從 c # 9.0 開始，方法支援協變數傳回型別 `override` 。 尤其是，方法的傳回型別 `override` 可以衍生自對應基底方法的傳回型別。 在 c # 8.0 及更早版本中，方法的傳回類型 `override` 和覆寫的基底方法必須相同。

您無法覆寫非虛擬或靜態方法。 覆寫基底方法必須是 `virtual`、`abstract` 或 `override`。

`override` 宣告不能變更 `virtual` 方法的存取範圍。 `override` 方法和 `virtual` 方法都必須具有相同的[存取層級修飾詞](access-modifiers.md)。

您不能使用 `new`、`static` 或 `virtual` 修飾詞來修改 `override` 方法。

覆寫屬性宣告必須指定與繼承的屬性完全相同的存取修飾詞、型別和名稱。 從 c # 9.0 開始，唯讀的覆寫屬性支援協變數傳回型別。 覆寫的屬性必須是 `virtual` 、 `abstract` 或 `override` 。

如需如何使用關鍵字的詳細資訊 `override` ，請參閱使用 [Override 和 new 關鍵字進行版本控制](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ，以及 [瞭解使用 override 和 new 關鍵字](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)的時機。 如需繼承的資訊，請參閱[繼承](../../programming-guide/classes-and-structs/inheritance.md)。

## <a name="example"></a>範例

本例會定義名為 `Employee` 的基底類別，以及名為 `SalesEmployee` 的衍生類別。 `SalesEmployee` 類別包含額外的欄位 `salesbonus`，並會覆寫方法 `CalculatePay` 以將其納入考量。

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的覆[寫方法](~/_csharplang/spec/classes.md#override-methods)一節。

如需有關協變數傳回類型的詳細資訊，請參閱 [功能提案注意事項](~/_csharplang/proposals/csharp-9.0/covariant-returns.md)。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [繼承](../../programming-guide/classes-and-structs/inheritance.md)
- [C # 關鍵字](index.md)
- [修飾詞](index.md)
- [抽象](abstract.md)
- [virtual](virtual.md)
- [新的 (修飾詞) ](new-modifier.md)
- [多型](../../programming-guide/classes-and-structs/polymorphism.md)
