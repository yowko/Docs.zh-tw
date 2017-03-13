---
title: "Set Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Set"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "property procedures, Set statements"
  - "Set statement"
  - "Set statement, syntax"
  - "write-only properties"
  - "properties [Visual Basic], write-only"
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Set Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

宣告用來將值指派至屬性 \(Property\) 的 `Set` 屬性 \(Property\) 程序。  
  
## 語法  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## 組件  
 `attributelist`  
 選擇項。  請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
 `accessmodifier`  
 在這個屬性之其中一個 `Get` 和 `Set` 陳述式上的選擇項。  可以是下列其中一項：  
  
-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `value`  
 必要項。  包含屬性之新值的參數。  
  
 `datatype`  
 如果 `Option Strict` 為 `On`，則為必要項。  `value` 參數的資料型別。  指定的資料型別必須與宣告這個 `Set` 陳述式所在屬性 \(Property\) 的資料型別相同。  
  
 `statements`  
 選擇項。  一或多個呼叫 `Set` 屬性程序時所執行的陳述式。  
  
 `End Set`  
 必要項。  結束 `Set` 屬性程序的定義。  
  
## 備註  
 除非屬性已標示為 `ReadOnly`，否則每個屬性都必須有 `Set` 屬性程序。  `Set` 程序是用於設定屬性的值。  
  
 當指派陳述式 \(Assignment Statement\) 提供要儲存於屬性中的值時，Visual Basic 會自動呼叫屬性的 `Set` 程序。  
  
 Visual Basic 在屬性指派期間會將參數傳遞至 `Set` 程序。  如果未提供 `Set` 的參數，則整合式開發環境 \(IDE\) 會使用名為 `value` 的隱含參數。  該參數會保留要指派給屬性的值。  通常會將這個值儲存在私用區域變數中，每當呼叫 `Get` 程序時就會傳回它。  
  
 屬性宣告主體只可在 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)與 `End Property` 陳述式之間包含屬性的 `Get` 和 `Set` 程序，  除了這些程序以外，它無法儲存其他程序。  特別是無法儲存屬性的目前值。  因為如果將這個值儲存在任一屬性程序中，則其他屬性程序無法存取它，所以必須將它儲存在屬性外部。  一般的處理方式是將值儲存在與屬性相同層級上宣告的 [Private](../../../visual-basic/language-reference/modifiers/private.md) 變數中。  而您必須在所套用的屬性內定義 `Set` 程序。  
  
 除非是在 `Set` 陳述式中使用 `accessmodifier`，否則 `Set` 程序會預設為包含屬性的存取層級。  
  
## 規則  
  
-   **混合存取層級** 如果您要定義 read\-write 屬性，可以選擇指定 `Get` 或 `Set` 程序的不同存取層級，但不可同時指定這兩者。  如果您這樣做，程序的存取層級必須比屬性的存取層級更嚴格。  例如，如果屬性已宣告為 `Friend`，則您可以將 `Set` 程序宣告為 `Private`，但不能宣告為 `Public`。  
  
     如果正在定義 `WriteOnly` 屬性，則 `Set` 程序會代表整個屬性。  若為 `Set` 宣告不同的存取層級，則會為屬性設定兩種存取層級，因此您不能這樣做。  
  
## 行為  
  
-   **從屬性程序傳回** 當 `Set` 程序傳回到呼叫程式碼時，仍會繼續執行提供所要儲存之值的陳述式後面的陳述式。  
  
     `Set` 屬性程序可以使用 [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) 或 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md) 傳回。  
  
     `Exit Property` 和 `Return` 陳述式會造成立即退出屬性程序。  任意數目的 `Exit Property` 和 `Return` 陳述式可以出現在程序中的任何地方，並且 `Exit Property` 和 `Return` 陳述式可以混合使用。  
  
## 範例  
 下列範例會使用 `Set` 陳述式，設定屬性的值。  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## 請參閱  
 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)