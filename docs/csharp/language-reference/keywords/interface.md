---
title: interface - C# 參考
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: b315d1f04c9e74700afba8ee7871b23ab4b2fd28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744687"
---
# <a name="no-loc-textinterface-c-reference"></a>:::no-loc text="interface"::: （C#參考）

介面會定義合約。 任何執行該合約的[`class`](class.md)或[`struct`](struct.md)都必須提供在介面中定義之成員的實作為。 從C# 8.0 開始，介面可能會定義成員的預設實值。 它也可以定義[`static`](static.md)成員，以便為一般功能提供單一的執行方式。

在下列範例中，類別 `ImplementationClass` 必須實作名為 `SampleMethod` 的方法，該方法沒有參數並會傳回 `void`。

如需詳細資訊與範例，請參閱[介面](../../programming-guide/interfaces/index.md)。

## <a name="example"></a>範例

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

介面可以是命名空間或類別的成員。 介面宣告可以包含下列成員的宣告（不含任何執行的簽章）：

- [方法](../../programming-guide/classes-and-structs/methods.md)
- [屬性](../../programming-guide/classes-and-structs/using-properties.md)
- [索引子](../../programming-guide/indexers/using-indexers.md)
- [事件](event.md)

這些前面的成員宣告通常不會包含主體。 從C# 8.0 開始，介面成員可以宣告主體。 這稱為「*預設實值*」。 具有主體的成員允許介面為不提供覆寫實作為的類別和結構提供「預設」的執行。 此外，從C# 8.0 開始，介面可能包括：

- [常數](const.md)
- [運算子](../operators/operator-overloading.md)
- [靜態](../../programming-guide/classes-and-structs/constructors.md#static-constructors)的函式。
- [巢狀類型](../../programming-guide/classes-and-structs/nested-types.md)
- [靜態欄位、方法、屬性、索引子和事件](static.md)
- 使用明確介面執行語法的成員宣告。
- 明確存取修飾詞（預設存取是[`public`](access-modifiers.md)）。

介面可能不包含實例狀態。 雖然現在允許靜態欄位，但介面中不允許實例欄位。 介面中不支援[實例 auto 屬性](../../programming-guide/classes-and-structs/auto-implemented-properties.md)，因為它們會隱含宣告隱藏的欄位。 此規則對屬性宣告有細微的影響。 在介面宣告中，下列程式碼不會宣告自動實作用的屬性，就像在 `class` 或 `struct`中的一樣。 相反地，它會宣告沒有預設值的屬性，但必須在任何實作為介面的型別中執行：

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

介面可以繼承一或多個基底介面。 當介面覆寫在基底介面中實[作為的方法](override.md)時，它必須使用[明確介面的實](../../programming-guide/interfaces/explicit-interface-implementation.md)語法。

當基底類型清單包含基底類別和介面時，基底類別一定會排在清單的第一個。

實作介面的類別能夠明確實作該介面的成員。 明確實作的成員不能經由類別執行個體存取，只能經由介面的執行個體來存取。 此外，預設介面成員只能透過介面的實例來存取。

如需明確介面執行的詳細資訊，請參閱[明確介面實](../../programming-guide/interfaces/explicit-interface-implementation.md)。

## <a name="example"></a>範例

下列範例示範介面實作。 在此範例中，介面包含屬性宣告，而類別包含實作。 實作 `IPoint` 的任何類別執行個體都有整數屬性 `x` 和 `y`。

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)的[介面](~/_csharplang/spec/interfaces.md)一節和[預設介面成員的功能規格- C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [參考型別](reference-types.md)
- [介面](../../programming-guide/interfaces/index.md)
- [使用屬性](../../programming-guide/classes-and-structs/using-properties.md)
- [使用索引子](../../programming-guide/indexers/using-indexers.md)
- [class](class.md)
- [struct](struct.md)
- [介面](../../programming-guide/interfaces/index.md)
