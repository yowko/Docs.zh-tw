---
title: 匿名類型定義 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 179fb9773fde2631666498d54894037b2bbfd087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="anonymous-type-definition-visual-basic"></a>匿名類型定義 (Visual Basic)
為了回應執行個體的匿名類型宣告，編譯器會建立新的類別定義，其中包含指定的屬性類型。  
  
## <a name="compiler-generated-code"></a>編譯器產生的程式碼  
 下列定義的`product`，編譯器會建立新的類別定義，其中包含屬性`Name`， `Price`，和`OnHand`。  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
 類別定義包含類似下列的屬性定義。 請注意，有任何`Set`索引鍵屬性的方法。 索引鍵屬性的值是唯讀的。  
  
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
  
 此外，匿名類型定義包含預設建構函式。 不允許使用需要參數的建構函式。  
  
 匿名類型宣告包含至少一個索引鍵內容，如果型別定義會覆寫繼承自的三個成員<xref:System.Object>: <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。 如果沒有索引鍵屬性宣告，只<xref:System.Object.ToString%2A>會覆寫。 覆寫中提供下列功能：  
  
-   `Equals` 傳回`True`兩個匿名型別執行個體是否相同的執行個體，或若符合下列條件：  
  
    -   它們有相同數目的屬性。  
  
    -   屬性的宣告以相同的順序，使用相同的名稱和相同推斷的型別。 名稱比較不區分大小寫。  
  
    -   至少其中一個屬性是索引鍵屬性，而`Key`關鍵字套用至相同的屬性。  
  
    -   比較每個對應的配對的索引鍵屬性會傳回`True`。  
  
     例如，在下列範例中，`Equals`傳回`True`僅適用於`employee01`和`employee08`。 之前的每一行指定為什麼不相符的新執行個體的原因的註解`employee01`。  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   `GetHashcode` 提供的適當唯一 GetHashCode 演算法。 此演算法會使用索引鍵的屬性，用來計算雜湊碼。  
  
-   `ToString` 傳回串連的屬性值的字串，如下列範例所示。 索引鍵和非索引鍵屬性會包含項目。  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 明確命名的匿名類型屬性不能與這些產生的方法衝突。 也就是說，您無法使用`.Equals`， `.GetHashCode`，或`.ToString`命名屬性。  
  
 在包含至少一個的匿名型別定義的索引鍵屬性也實作<xref:System.IEquatable%601?displayProperty=nameWithType>介面，其中`T`是匿名類型的類型。  
  
> [!NOTE]
>  匿名類型宣告在它們出現在相同的組件、 其屬性具有相同名稱和相同推斷的型別、 屬性的宣告以相同的順序，和相同的屬性會標示為索引鍵屬性時，才可以建立相同匿名類型。  
  
## <a name="see-also"></a>另請參閱  
 [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
