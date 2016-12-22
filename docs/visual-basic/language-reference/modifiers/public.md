---
title: "Public (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Public"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Public keyword"
  - "Public keyword, syntax"
  - "Public access modifier"
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Public (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定一或多個宣告的程式設計項目沒有存取限制。  
  
## 備註  
 如果您正在發行一個元件或一組元件，如類別庫，通常會希望任何與組件相互操作的程式碼能夠存取程式設計項目。  若要對項目授與此類無限制的存取，您可以利用 `Public` 宣告它。  
  
 當您不需要限制程式設計項目的存取時，公用 \(Public\) 存取是程式設計項目的一般層級。  請注意，如果您沒有以其他方式宣告項目，則在介面、模組、類別或結構內宣告的項目之存取層級會預設值為 `Public`。  
  
## 規則  
  
-   **宣告內容：** 您只能在模組、介面或命名空間層級使用 `Public`。  這表示 `Public` 項目的宣告內容必須是原始程式檔、命名空間、介面、模組、類別或結構，而不能是程序。  
  
## 行為  
  
-   **存取層級** 所有可以存取模組、類別或結構的程式碼都可以存取其 `Public` 項目。  
  
-   **預設存取。** 程序內的區域變數會預設為公用存取，因此您無法在其上使用任何存取修飾詞 \(Modifier\)。  
  
-   **存取修飾詞。** 表示存取層級的關鍵字稱為「*存取修飾詞*」\(Access Modifier\)。  如需存取修飾詞的比較，請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `Public` 修飾詞可用於以下內容中：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 請參閱  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/reference/command-line-compiler/index.md)