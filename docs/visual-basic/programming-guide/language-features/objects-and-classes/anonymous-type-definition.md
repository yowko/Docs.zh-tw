---
title: "Anonymous Type Definition (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "anonymous types [Visual Basic], type definition"
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Anonymous Type Definition (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

遇到匿名型別執行個體 \(Instance\) 的宣告時，編譯器 \(Compiler\) 會建立新的類別定義，其中含有指定給該型別的屬性。  
  
## 編譯器產生的程式碼  
 根據下列 `product` 的定義，編譯器會建立新的類別定義，其中含有 `Name`、`Price` 和 `OnHand` 屬性。  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
 類別定義所含的屬性定義與下面類似。  請注意，索引鍵屬性沒有 `Set` 方法。  索引鍵屬性的值是唯讀的。  
  
```vb#  
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
  
 此外，匿名型別定義中也包含預設建構函式 \(Constructor\)。  不允許有需要使用參數的建構函式。  
  
 如果匿名型別宣告至少含有一個索引鍵屬性，則型別定義會覆寫三個繼承自 <xref:System.Object> 的成員：<xref:System.Object.Equals%2A>、<xref:System.Object.GetHashCode%2A> 和 <xref:System.Object.ToString%2A>。  如果未宣告索引鍵屬性，則只會覆寫 <xref:System.Object.ToString%2A>。  覆寫提供的功能如下：  
  
-   如果兩個匿名型別執行個體是同一個執行個體，或符合下列條件，則 `Equals` 會傳回 `True`：  
  
    -   具有相同數目的屬性。  
  
    -   宣告的屬性順序相同，而且名稱和推斷的型別也相同。  名稱比較不區分大小寫。  
  
    -   至少有一個屬性是索引鍵屬性，而且套用 `Key` 關鍵字的是相同的屬性。  
  
    -   比較每對索引鍵屬性都傳回 `True`。  
  
     例如，下列範例中的 `Equals` 只有在遇到 `employee01` 和 `employee08` 時才傳回 `True`。  每行前面的註解會指出新執行個體不符合 `employee01` 的原因。  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   `GetHashcode` 適當提供了唯一的 GetHashCode 演算法。  這個演算法只會使用索引鍵屬性來計算雜湊程式碼。  
  
-   `ToString` 會傳回由屬性值串連而成的字串，如下列範例所示。  索引鍵屬性和非索引鍵屬性都會加至其中。  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 匿名型別中明確命名的屬性不能與這些產生的方法衝突。  換句話說，您不能使用 `.Equals`、`.GetHashCode` 或 `.ToString` 來命名屬性。  
  
 至少含有一個索引鍵屬性的匿名型別同時也會實作 <xref:System.IEquatable%601?displayProperty=fullName> 介面，其中 `T` 是匿名型別的類型。  
  
> [!NOTE]
>  匿名型別宣告只有在下列情況下才會建立相同的匿名型別：在同一個組件 \(Assembly\) 中宣告、其屬性具有相同的名稱和推斷型別、屬性的宣告順序相同，以及將相同的屬性標記為索引鍵屬性。  
  
## 請參閱  
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)