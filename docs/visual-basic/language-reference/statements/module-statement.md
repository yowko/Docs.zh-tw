---
title: "Module Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Module"
  - "vb.Module"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "modules, classes"
  - "modules"
  - "Module statement"
  - "modules, declaring"
  - "standard modules"
  - "classes [Visual Basic], vs. modules"
  - "declarations, modules"
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# Module Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

宣告模組的名稱，並引入組成模組之變數、屬性、事件和程序的定義。  
  
## 語法  
  
```  
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## 組件  
 `attributelist`  
 選擇項。  請參閱 [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
 `accessmodifier`  
 選擇項。  可以是下列其中一項：  
  
-   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `name`  
 必要項。  這個模組的名稱。  請參閱[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 `statements`  
 選擇項。  定義這個模組之變數、屬性、事件、程序和巢狀型別的陳述式。  
  
 `End Module`  
 結束 `Module` 定義。  
  
## 備註  
 `Module` 陳述式定義可以在命名空間中使用的參考型別 \(Reference Type\)。  「*模組*」\(有時稱為「*標準模組*」\) 與類別 \(Class\) 類似，但有一些重要區別。  每個模組都只可有一個執行個體，且不需要建立或指派給變數。  模組不支援繼承 \(Inheritance\) 或實作介面。  請注意，就這種意義而言，模組不是類別或結構的「*型別*」。不可將程式設計項目宣告成具有模組的資料型別。  
  
 只可以在命名空間層級使用 `Module`。  這表示模組的「*宣告內容*」必須是原始程式檔或命名空間，且不可以是類別、結構、模組、介面、程序或區塊。  不可在另一個模組內或任何型別內巢狀化模組。  如需詳細資訊，請參閱[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 模組的存留期 \(Lifetime\) 與程式相同。  因為它的成員都是 `Shared`，所以它們的存留期也等於程式的存留期。  
  
 模組預設值為 [Friend](../../../visual-basic/language-reference/modifiers/friend.md) 存取。  您可以使用存取修飾詞調整存取層級。  如需詳細資訊，請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 模組的所有成員都是隱含 `Shared`。  
  
## 類別和模組  
 這些項目有許多相似點，但也有一些重要的差異。  
  
-   **用語** 舊版的 Visual Basic 可以辨認兩種模組：「*類別模組*」\(Class Module，.cls 檔案\) 和「*標準模組*」\(Standard Module，.bas 檔案\)。  目前的版本會分別呼叫這些「*類別*」和「*模組*」。  
  
-   **共用成員** ：您可以控制類別成員是共用成員或執行個體成員。  
  
-   **物件導向** ：類別為物件導向，但模組不是。  所以只有類別可具現化 \(Instantiated\) 為物件。  如需詳細資訊，請參閱 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## 規則  
  
-   **修飾詞。** 所有模組成員都是隱含 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)。  宣告成員時，不可使用 `Shared` 關鍵字，且不可改變任何成員的共用狀態。  
  
-   **繼承** 模組無法繼承非 <xref:System.Object> 的其他任何型別，所有模組都是從該型別繼承。  特別地是，某個模組不可繼承另一個模組。  
  
     即使指定 <xref:System.Object>，也不可在模組定義中使用 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)。  
  
-   **預設屬性** 您無法在模組中定義任何預設屬性。  如需詳細資訊，請參閱[Default](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## 行為  
  
-   **存取層級** ：在模組內，可宣告每個成員都具有它自己的存取層級。  模組成員預設值為 [Public](../../../visual-basic/language-reference/modifiers/public.md) 存取，但不包含變數和常數，它們是預設值為 [Private](../../../visual-basic/language-reference/modifiers/private.md) 存取。  模組的存取比它的任何一個成員還受限制時，則所指定的模組存取層級的優先順序較高。  
  
-   **範圍。** ：模組是位在命名空間中的範圍內。  
  
     每個模組成員的範圍是整個模組。  請注意，所有成員接受「*型別提升*」，會讓它們的範圍提升成內含模組的命名空間。  如需詳細資訊，請參閱 [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)。  
  
-   **限定性條件。** ：在專案中可以有多個模組，且可以在兩個以上的模組中宣告同名的成員。  然而，如果這類具有適當模組名稱之成員的任何參考是來自該模組的外部，則必須限定該參考。  如需詳細資訊，請參閱 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
## 範例  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/module-statement_1.vb)]  
  
## 請參閱  
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)