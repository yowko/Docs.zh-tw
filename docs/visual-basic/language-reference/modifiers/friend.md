---
title: "Friend (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Friend"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Friend 關鍵字"
  - "Friend 存取修飾詞"
  - "Friend 關鍵字, 語法"
  - "Protected Friend 關鍵字組合"
  - "Friend 關鍵字, 和 Protected"
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# Friend (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定一或多個宣告的程式設計項目只能從包含其宣告的組件中存取。  
  
## 備註  
 在許多情況下，您可能想要整個組件都可使用程式設計項目 \(例如類別和結構\)，而不只是由宣告它們的元件使用。  不過，您可能不希望它們可由組件外部的程式碼 \(例如，因此，如果應用程式是私用的\)。  如果您要以這種方式限制項目的存取，您可以使用 `Friend` 修飾詞，您可以宣告它。  
  
 編譯成相同組件之其他類別、結構和模組的程式碼，都可以存取該組件中的所有 `Friend` 項目。  
  
 `Friend` 存取通常是應用程式項目的慣用層級，，且 `Friend` 是介面、模組、類別或結構的預設存取層級。  
  
 您只能使用 `Friend` 在模組、介面或命名空間層級。  因此， `Friend` 項目的宣告內容必須是原始程式檔、命名空間、介面、模組、類別或結構;它不能是程序。  
  
 您可在同一個宣告中搭配使用 `Friend` 修飾詞與 [Protected](../../../visual-basic/language-reference/modifiers/protected.md) 修飾詞。  這個組合在宣告項目授與兩個 `Friend` 存取和受保護的存取，因此，它們可從任何位置相同的組件時，從其類別和衍生類別。  您只能在類別成員上指定 `Protected Friend`。  
  
 對於 `Friend` 和其他的比較存取修飾詞，請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
> [!NOTE]
>  您可以指定另一個組件為 Friend 組件，讓它可以存取所有型別和成員標記為 `Friend`。  如需詳細資訊，請參閱[Friend 組件](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 範例  
 下列類別會使用 `Friend` 修飾詞，以允許相同組件內的其他程式設計項目存取某些成員。  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/friend_1.vb)]  
  
## 使用方式  
 您可以在這些內容使用 `Friend` 修飾詞:  
  
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
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)