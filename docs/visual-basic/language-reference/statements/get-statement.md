---
title: "Get Statement | Microsoft Docs"
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
  - "vb.Get"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Get statement, syntax"
  - "Get statement"
  - "properties [Visual Basic], read-only"
  - "read-only properties"
  - "Get keyword"
  - "property procedures, Get statements"
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Get Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

宣告用以擷取屬性 \(Property\) 值的 `Get` 屬性程序。  
  
## 語法  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`attributelist`|選擇項。  請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|在這個屬性之其中一個 `Get` 和 `Set` 陳述式上的選擇項。  可以是下列其中一項：<br /><br /> -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`statements`|選擇項。  呼叫 `Get` 屬性程序時會執行的一或多個陳述式。|  
|`End Get`|必要項。  用於結束 `Get` 屬性程序的定義。|  
  
## 備註  
 除非屬性標示為 `WriteOnly`，否則每一個屬性都必須有一個 `Get` 屬性程序。  `Get` 程序是用於傳回屬性的目前值。  
  
 當運算式要求屬性值時，Visual Basic 就會自動呼叫屬性的 `Get` 程序。  
  
 屬性宣告主體只可在 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)與 `End Property` 陳述式之間包含屬性的 `Get` 和 `Set` 程序，  除了這些程序以外，它無法儲存其他程序。  特別是無法儲存屬性的目前值。  因為如果將這個值儲存在任一屬性程序中，則其他屬性程序無法存取它，所以必須將它儲存在屬性外部。  一般的處理方式是將值儲存在與屬性相同層級上宣告的 [Private](../../../visual-basic/language-reference/modifiers/private.md) 變數中。  您必須將 `Get` 程序定義在套用它的屬性內。  
  
 `Get` 程序預設為包含屬性的存取層級，除非您在 `Get` 陳述式中使用 `accessmodifier`。  
  
## 規則  
  
-   **混合存取層級** 如果您要定義 read\-write 屬性，可以選擇指定 `Get` 或 `Set` 程序的不同存取層級，但不可同時指定這兩者。  如果您這樣做，程序的存取層級必須比屬性的存取層級更嚴格。  例如，如果屬性已宣告為 `Friend`，則您可以將 `Get` 程序宣告為 `Private`，但不能宣告為 `Public`。  
  
     如果正在定義 `ReadOnly` 屬性，則 `Get` 程序會代表整個屬性。  若為 `Get` 宣告不同的存取層級，則會為屬性設定兩種存取層級，因此您不能這樣做。  
  
-   **傳回型別** [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)可以宣告它所傳回之值的資料型別。  `Get` 程序會自動傳回該資料型別。  您可以指定任何資料型別，或列舉型別、結構、類別或介面的名稱。  
  
     如果 `Property` 陳述式未指定 `returntype`，程序將傳回 `Object`。  
  
## 行為  
  
-   **從程序傳回** 當 `Get` 程序傳回到呼叫程式碼時，執行會在已要求屬性值的陳述式內繼續進行。  
  
     `Get` 屬性程序可以傳回值，方法是使用 [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md)，或指派傳回值給屬性名稱。  如需詳細資訊，請參閱 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) 中的＜傳回值＞一節。  
  
     `Exit Property` 和 `Return` 陳述式會造成立即退出屬性程序。  任意數目的 `Exit Property` 和 `Return` 陳述式可以出現在程序中的任何地方，並且 `Exit Property` 和 `Return` 陳述式可以混合使用。  
  
-   **傳回值** 若要從 `Get` 程序傳回值，您可以指派值給屬性名稱，或將它併入 [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md)。  `Return` 陳述式會同時指派 `Get` 程序傳回值並結束程序。  
  
     如果您使用 `Exit Property`，但未指派值給屬性名稱，則 `Get` 程序會傳回屬性資料型別的預設值。  如需詳細資訊，請參閱 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) 中的＜傳回值＞一節。  
  
     下列範例會說明兩種方法，唯讀屬性 `quoteForTheDay` 可以用於傳回私用變數 `quoteValue` 中所保留的值。  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## 範例  
 下列範例會使用 `Get` 陳述式，傳回屬性的值。  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## 請參閱  
 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Objects and Classes](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Walkthrough: Defining Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)