---
title: "Private (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Private"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Private keyword"
  - "Private keyword, syntax"
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Private (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定一或多個宣告的程式設計項目只能從其宣告內容中進行存取 \(包括從任何內含的型別中\)。  
  
## 備註  
 如果程式設計項目表示專屬功能或包含機密資料，則您通常要盡可能地限制存取程式設計項目。  您可以設定最大的限制，方法是只允許定義該功能或資料的模組、類別或結構才能存取它。  若要用這種方法來限制項目的存取，則可使用 `Private` 來宣告它。  
  
## 規則  
  
-   **宣告內容：** 只能在模組層級使用 `Private`。  這表示 `Private` 項目的宣告內容必須是模組、類別或結構，且不能是原始程式檔、命名空間、介面或程序。  
  
## 行為  
  
-   **存取層級** 宣告內容中的所有程式碼都可存取其 `Private` 項目。  這包含內含型別內部的程式碼，例如，列舉型別中的巢狀類別或指派運算式。  宣告內容外部的程式碼都不能存取該 `Private` 項目。  
  
-   **存取修飾詞。** 表示存取層級的關鍵字稱為「*存取修飾詞*」\(Access Modifier\)。  如需存取修飾詞的比較，請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `Private` 修飾詞可用於以下內容中：  
  
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
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)