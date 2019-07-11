---
title: 匿名類型定義 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 5f6486965d9e44524420975523e10ded32a135b7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755210"
---
# <a name="anonymous-type-definition-visual-basic"></a>匿名類型定義 (Visual Basic)

為了回應執行個體的匿名型別宣告，編譯器會建立新的類別定義，其中包含指定的屬性類型。

## <a name="compiler-generated-code"></a>編譯器產生的程式碼

下列定義`product`，編譯器會建立新的類別定義，其中包含屬性`Name`， `Price`，和`OnHand`。

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

類別定義包含屬性定義如下所示。 請注意，有沒有`Set`索引鍵屬性的方法。 索引鍵屬性的值是唯讀的。

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

此外，匿名型別定義包含的無參數建構函式。 不允許使用需要參數的建構函式。

匿名類型宣告包含至少一個索引鍵屬性，如果型別定義會覆寫三個成員繼承自<xref:System.Object>: <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。 如果沒有索引鍵的屬性宣告，只<xref:System.Object.ToString%2A>會覆寫。 覆寫提供下列功能：

- `Equals` 傳回`True`兩個匿名型別執行個體是否相同的執行個體，或符合下列條件：

  - 它們有相同數目的屬性。

  - 屬性的宣告順序相同，具有相同名稱和相同推斷的型別。 名稱比較不區分大小寫。

  - 至少其中一個屬性是索引鍵的屬性，而`Key`關鍵字是否套用至相同的屬性。

  - 每個對應的配對的索引鍵屬性的比較會傳回`True`。

    例如，在下列範例中，`Equals`會傳回`True`僅適用於`employee01`和`employee08`。 之前每一行指定為什麼不相符的新執行個體的原因的註解`employee01`。

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode` 提供適當的唯一的 GetHashCode 演算法。 此演算法會使用索引鍵的屬性，來計算雜湊碼。

- `ToString` 傳回串連的屬性值的字串，如下列範例所示。 會包含索引鍵和非索引鍵屬性。

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

明確命名的匿名型別屬性不能與這些產生的方法衝突。 也就是說，您無法使用`.Equals`， `.GetHashCode`，或`.ToString`命名屬性。

匿名類型定義，在包含至少一個索引鍵屬性也實作<xref:System.IEquatable%601?displayProperty=nameWithType>介面，其中`T`是匿名型別的型別。

> [!NOTE]
> 匿名類型宣告在它們出現在相同的組件、 其屬性具有相同名稱和相同推斷的型別、 屬性的宣告以相同的順序，和相同的屬性會標示為索引鍵屬性時，才可以建立相同匿名型別。

## <a name="see-also"></a>另請參閱

- [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [如何：推斷屬性名稱和匿名類型宣告中的類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
