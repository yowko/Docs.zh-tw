---
title: "Visual Basic 中的資料類型 | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "資料類型 [Visual Basic]，宣告"
  - "類型"
  - "資料類型 [Visual Basic]"
  - "Visual Basic 程式碼，資料類型"
  - "資料類型 [Visual Basic]，改善速度"
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
caps.latest.revision: 28
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# Visual Basic 中的資料類型
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

程式設計項目的「*資料型別*」\(Data Type\) 指的是它可保存的資料種類，以及它儲存該資料的方式。  資料型別適用於所有可儲存在電腦記憶體中或是放在運算式中計算的值。  任何變數、常值 \(Literal\)、常數、列舉型別 \(Enumeration\)、屬性 \(Property\)、程序參數、程序引數 \(Procedure Argument\) 及程序傳回值都具有資料型別。  
  
## 宣告的資料型別  
 您可以利用宣告陳述式 \(Declaration Statement\) 定義程式設計項目，然後以 `As` 子句指定它的資料型別。  下表會顯示可用於宣告各種項目的陳述式。  
  
|程式設計項目|資料型別宣告|  
|------------|------------|  
|變數|在 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 中<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Literal|使用常值型別字元，請參閱[Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)中「常值型別字元」的內容<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|常數|在 [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) 中<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|列舉|在 [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md) 中<br /><br /> `Public`   `Enum`   `colors`|  
|屬性|在 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) 中<br /><br /> `Property`   `region() As String`|  
|程序參數|在 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)、[Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) 或 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)中<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|程序引數|在呼叫程式碼中，每個引數都是已宣告的程式設計項目，或者是包含已宣告之項目的運算式<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|程序傳回值|在 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) 或 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)中<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 如需 Visual Basic 資料型別清單，請參閱 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
## 請參閱  
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Visual Basic 中的泛型類型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)