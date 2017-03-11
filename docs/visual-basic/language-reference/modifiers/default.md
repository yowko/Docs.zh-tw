---
title: "Default (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Default"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "defaults, properties"
  - "properties [Visual Basic], default"
  - "default properties, in Visual Basic"
  - "Default keyword [Visual Basic]"
  - "default properties"
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Default (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

將屬性識別為其類別、結構或介面的預設屬性。  
  
## 備註  
 類別、結構或介面最多可將它的其中一個屬性指定成「*預設屬性*」，而且假設屬性至少採用一個參數。  如果程式碼產生類別或結構的參考，而未指定成員，則 Visual Basic 會將該參考解析成預設屬性。  
  
 預設屬性可小幅度地減少原始程式碼字元，但會讓其他人更不容易看懂您的程式碼。  如果呼叫程式碼不熟悉您的類別或結構，則在它產生該類別或結構名稱的參考時，會無法確定該參考存取的是類別或結構本身或預設屬性。  這會造成編譯器錯誤，或微妙的執行階段邏輯錯誤。  
  
 您永遠可以使用 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)，將編譯器型別檢查 \(Type Checking\) 設為 `On`，以減少預設屬性錯誤的機會。  
  
 如果您預計在程式碼中使用預先定義的類別或結構，則必須判斷它是否具有預設屬性，如果有則其名稱為何。  
  
 因為這些缺點，所以您應考慮不要定義預設屬性。  為了增加程式碼可讀性，也應考慮一律明確參考所有屬性 \(甚至是預設屬性\)。  
  
 `Default` 修飾詞可用於以下內容中：  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## 請參閱  
 [How to: Declare and Call a Default Property in Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)