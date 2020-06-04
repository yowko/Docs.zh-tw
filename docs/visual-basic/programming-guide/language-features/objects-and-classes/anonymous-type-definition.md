---
title: 匿名型別定義
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 952eb295cc71eab5d0ad6e18f2b697a9b701b434
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404897"
---
# <a name="anonymous-type-definition-visual-basic"></a>匿名類型定義 (Visual Basic)

為了回應匿名型別的實例宣告，編譯器會建立新的類別定義，其中包含型別的指定屬性。

## <a name="compiler-generated-code"></a>編譯器產生的程式碼

針對的下列定義 `product` ，編譯器會建立新的類別定義，其中包含屬性 `Name` 、 `Price` 和 `OnHand` 。

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

類別定義包含如下所示的屬性定義。 請注意，沒有索引 `Set` 鍵屬性的方法。 索引鍵屬性的值是唯讀的。

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

此外，匿名型別定義包含無參數的函式。 不允許需要參數的函式。

如果匿名型別宣告至少包含一個索引鍵屬性，則型別定義會覆寫三個繼承自的成員 <xref:System.Object> ： <xref:System.Object.Equals%2A> 、 <xref:System.Object.GetHashCode%2A> 和 <xref:System.Object.ToString%2A> 。 如果未宣告任何索引鍵屬性， <xref:System.Object.ToString%2A> 則只會覆寫。 覆寫會提供下列功能：

- `Equals``True`如果兩個匿名型別實例是相同的實例，或如果符合下列條件，則傳回：

  - 它們具有相同數目的屬性。

  - 屬性會以相同的順序宣告，並具有相同的名稱和相同的推斷類型。 名稱比較不區分大小寫。

  - 至少其中一個屬性是索引鍵屬性，而且 `Key` 關鍵字會套用至相同的屬性。

  - 每個對應的索引鍵屬性的比較都會傳回 `True` 。

    例如，在下列範例中，只會傳回 `Equals` `True` `employee01` 和的 `employee08` 。 每一行的批註會指定新實例不相符的原因 `employee01` 。

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode`提供適當的唯一 GetHashCode 演算法。 演算法只會使用索引鍵屬性來計算雜湊碼。

- `ToString`傳回串連屬性值的字串，如下列範例所示。 同時包含索引鍵和非索引鍵屬性。

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

匿名型別的明確命名屬性不能與這些產生的方法衝突。 也就是說，您不能使用 `.Equals` 、 `.GetHashCode` 或 `.ToString` 來命名屬性。

包含至少一個索引鍵屬性的匿名型別定義也 <xref:System.IEquatable%601?displayProperty=nameWithType> 會執行介面，其中 `T` 是匿名型別的型別。

> [!NOTE]
> 匿名型別宣告只有在相同的元件中發生時，才會建立相同的匿名型別、其屬性具有相同的名稱和相同的推斷類型、屬性是以相同的順序宣告，而且相同的屬性會標示為索引鍵屬性。

## <a name="see-also"></a>另請參閱

- [匿名類型](anonymous-types.md)
- [如何：在匿名類型宣告中推斷屬性名稱和類型](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
