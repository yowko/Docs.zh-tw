---
title: "Implements Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Implements"
  - "Implements"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Implements statement, syntax"
  - "Implements statement"
  - "interface implementation, Implements statement"
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Implements Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定必須在所在類別或結構定義中實作的一或多個介面或是介面成員。  
  
## 語法  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## 組件  
 `interfacename`  
 必要項。  屬性 \(Property\)、程序及事件將透過類別或結構中對應成員實作的介面。  
  
 `interfacemember`  
 必要項。  要實作介面的成員。  
  
## 備註  
 介面是原型 \(Prototype\) 的集合，代表介面封裝的成員 \(屬性、成員及事件\)。  介面只包含成員的宣告；類別和結構則實作這些成員。  如需詳細資訊，請參閱 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。  
  
 `Implements` 陳述式必須緊跟在 `Class` 或 `Structure` 陳述式之後。  
  
 當您實作介面時，您必須實作所有在介面中宣告的成員。  省略任一成員將被視為是語法錯誤。  若要實作個別成員，您可以在類別或結構中宣告時成員時，指定 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) 關鍵字 \(此關鍵字必須在 `Implements` 陳述式外另行指定\)。  如需詳細資訊，請參閱 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。  
  
 類別可以使用屬性和程序的 [Private](../../../visual-basic/language-reference/modifiers/private.md) 實作，但是這些成員的存取只能透過將實作類別之執行個體 \(Instance\) 轉換成已宣告為介面型別的變數來進行。  
  
## 範例  
 下列範例會顯示如何使用 `Implements` 陳述式實作介面的成員。  它會定義名為 `ICustomerInfo` 的介面，此介面具有一個事件、一個屬性和一個程序。  `customerInfo` 類別則會實作在介面中定義的所有成員。  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 請注意，`customerInfo` 類別會在另一行原始程式碼中使用 `Implements` 陳述式，指出類別會實作 `ICustomerInfo` 介面的所有成員。  接著，類別中的每個成員都會使用 `Implements` 關鍵字，做為成員宣告的一部分，指出它會實作該介面成員。  
  
## 範例  
 以下兩個程序將顯示如何使用上述範例中所實作的介面。  若要測試實作，請將這些程序加入至您的專案中，並呼叫 `testImplements` 程序。  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## 請參閱  
 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)