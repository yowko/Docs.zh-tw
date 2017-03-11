---
title: "MustInherit (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "MustInherit"
  - "vb.MustInherit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes [Visual Basic], abstract"
  - "MustInherit classes, MustInherit keyword"
  - "abstract classes, MustInherit class"
  - "MustInherit keyword"
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# MustInherit (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定只能將類別當做基底類別，而且您無法從中直接建立物件。  
  
## 備註  
 「*基底類別*」\(也稱為「*抽象類別*」\(Abstract Class\)\) 的用途是定義功能，通用於從其衍生的所有功能。  這會根據必須重新定義通用項目來儲存衍生類別。  在某些情況下，這個通用功能的完成度並不足以製作可使用的物件，且每一個衍生類別都會定義遺漏的功能。  在這種情況下，您可能想要使用程式碼，只從衍生類別建立物件。  您可以在基底類別上使用 `MustInherit` 強制執行這個動作。  
  
 `MustInherit` 類別的另一個用途是，將變數限制為一組相關的類別。  您可以定義基底類別，再從中衍生所有相關類別。  基底類別不需要提供通用於所有衍生類別的任何功能，但它可以當做篩選條件來指派變數值。  如果使用的程式碼會將變數宣告為基底類別，Visual Basic 就能讓您只將其中一個衍生類別的物件，指派給該變數。  
  
 .NET Framework 定義了數個 `MustInherit` 類別，其中有 <xref:System.Array>、<xref:System.Enum> 和 <xref:System.ValueType>。  <xref:System.ValueType> 是限制變數的基底類別範例。  所有實值型別 \(Value Type\) 都衍生自 <xref:System.ValueType>。  若將變數宣告為 <xref:System.ValueType>，則可以只將實值型別指派給該變數。  
  
## 規則  
  
-   **宣告內容：** 您只能在 `Class` 陳述式中使用 `MustInherit`。  
  
-   **組合的修飾詞：** 您無法在同一個宣告中同時指定 `MustInherit` 和 `NotInheritable`。  
  
## 範例  
 下列範例會同時說明強制繼承和強制覆寫。  基底類別 `shape` 會定義變數 `acrossLine`。  類別 `circle` 和 `square` 衍生自 `shape`。  它們會繼承 `acrossLine` 的定義，但其必須定義函式 `area`，因為每種圖案都有不同的計算。  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/visualbasic/mustinherit_1.vb)]  
  
 您可以將 `shape1` 和 `shape2` 宣告成型別 `shape`。  然而，您無法從 `shape` 建立物件，因為它缺少函式 `area` 的功能，並已標記 `MustInherit`。  
  
 由於已將其宣告為 `shape`，因此會將變數 `shape1` 和 `shape2` 限制為來自衍生類別 `circle` 和 `square` 的物件。  Visual Basic 不允許您將任何其他物件指派給這些變數，因此能提供您高度的型別安全 \(Type Safety\)。  
  
## 使用方式  
 `MustInherit` 修飾詞可用於以下內容中：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## 請參閱  
 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)   
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)