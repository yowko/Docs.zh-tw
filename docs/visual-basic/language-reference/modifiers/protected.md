---
title: "Protected (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Protected"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Protected Friend keyword combination"
  - "Protected keyword, and Friend"
  - "Protected keyword, syntax"
  - "Protected access modifier"
  - "Protected keyword"
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Protected (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定一個或多個已宣告的程式設計項目只可從自己的類別或從衍生類別中進行存取。  
  
## 備註  
 有時，在類別內宣告的程式設計項目包含敏感資料或限制的程式碼，而且您想要限制該項目的存取。  然而，如果該類別是可繼承的類別，而且您預期會有衍生類別的階層架構，則這些衍生類別可能需要存取資料或程式碼。  在這類情況下，您會想要從基底類別和所有衍生類別中都可存取該項目。  若要用這種方法來限制項目的存取，則可使用 `Protected` 來宣告它。  
  
## 規則  
  
-   **宣告內容：** 您只能在類別層級使用 `Protected`。  這表示 `Protected` 項目的宣告內容必須是類別，而不可以是原始程式檔、命名空間、介面、模組、結構或程序。  
  
-   **組合的修飾詞：** 您可在同一個宣告中，搭配使用 `Protected` 修飾詞與 [Friend](../../../visual-basic/language-reference/modifiers/friend.md) 修飾詞。  這個組合會使宣告的項目可從相同組件中的任意地方、其自己的類別和衍生類別進行存取。  您只能在類別成員上指定 `Protected Friend`。  
  
## 行為  
  
-   **存取層級** 類別內的所有程式碼都可存取其項目。  任何衍生自基底類別之類別的程式碼，都可存取該基底類別的所有 `Protected` 項目。  所有衍生層代都是如此。  這表示，類別可以存取基底類別之基底類別的 `Protected` 項目，依此類推。  
  
     受保護存取並不是 Friend 存取的超集或子集。  
  
-   **存取修飾詞。** 表示存取層級的關鍵字稱為「*存取修飾詞*」\(Access Modifier\)。  如需存取修飾詞的比較，請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `Protected` 修飾詞可用於以下內容中：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 請參閱  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)