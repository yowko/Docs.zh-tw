---
title: interface - C# 參考
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 473f5f8e226f0a144746ac943afcffdccd4777c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625848"
---
# <a name="no-loc-textinterface-c-reference"></a>:::no-loc text="interface":::（C# 參考）

介面定義協定。 任何[`class`](class.md)或[`struct`](../builtin-types/struct.md)實現該協定都必須提供介面中定義的成員的實現。 從 C# 8.0 開始，介面可以定義成員的預設實現。 它還可以定義[`static`](static.md)成員，以便為通用功能提供單個實現。

在下列範例中，類別 `ImplementationClass` 必須實作名為 `SampleMethod` 的方法，該方法沒有參數並會傳回 `void`。

如需詳細資訊與範例，請參閱[介面](../../programming-guide/interfaces/index.md)。

## <a name="example"></a>範例

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

介面可以是命名空間或類的成員。 介面聲明可以包含以下成員的聲明（沒有任何實現的簽名）：

- [方法](../../programming-guide/classes-and-structs/methods.md)
- [屬性](../../programming-guide/classes-and-structs/using-properties.md)
- [索引子](../../programming-guide/indexers/using-indexers.md)
- [事件](event.md)

上述成員聲明通常不包含正文。 從 C# 8.0 開始，介面成員可以聲明正文。 這稱為*預設實現*。 具有正文的成員允許介面為不提供重寫實現的類和結構提供"預設"實現。 此外，從 C# 8.0 開始，介面可能包括：

- [常數](const.md)
- [運營商](../operators/operator-overloading.md)
- [靜態建構函式](../../programming-guide/classes-and-structs/constructors.md#static-constructors).
- [巢狀型別](../../programming-guide/classes-and-structs/nested-types.md)
- [靜態欄位、方法、屬性、索引子和事件](static.md)
- 使用明確介面實作語法的成員聲明。
- 顯式訪問修改器（預設訪問為[`public`](access-modifiers.md)）。

介面可能不包含實例狀態。 雖然現在允許靜態欄位，但介面中不允許實例欄位。 [介面中不支援實例自動屬性](../../programming-guide/classes-and-structs/auto-implemented-properties.md)，因為它們會隱式聲明隱藏欄位。 此規則對屬性聲明有微妙的影響。 在介面聲明中，以下代碼不聲明自動實現的屬性，就像它在`class`或 中`struct`那樣。 相反，它聲明一個屬性，該屬性沒有預設實現，但必須以實現介面的任何類型的實現：

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

介面可以繼承一或多個基底介面。 當介面重寫在基介面中實現[的方法時](override.md)，它必須使用[明確介面實作](../../programming-guide/interfaces/explicit-interface-implementation.md)語法。

當基底類型清單包含基底類別和介面時，基底類別一定會排在清單的第一個。

實作介面的類別能夠明確實作該介面的成員。 明確實作的成員不能經由類別執行個體存取，只能經由介面的執行個體來存取。 此外，預設介面成員只能通過介面的實例進行訪問。

有關明確介面實作的詳細資訊，請參閱[明確介面實作](../../programming-guide/interfaces/explicit-interface-implementation.md)。

## <a name="example"></a>範例

下列範例示範介面實作。 在此範例中，介面包含屬性宣告，而類別包含實作。 實作 `IPoint` 的任何類別執行個體都有整數屬性 `x` 和 `y`。

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>C# 語言規格

有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[介面](~/_csharplang/spec/interfaces.md)部分和預設介面成員的功能規格[- C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [參考類型](reference-types.md)
- [介面](../../programming-guide/interfaces/index.md)
- [使用屬性](../../programming-guide/classes-and-structs/using-properties.md)
- [使用索引子](../../programming-guide/indexers/using-indexers.md)
- [介面](../../programming-guide/interfaces/index.md)
