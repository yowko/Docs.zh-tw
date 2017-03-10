---
title: "Differences Between Parameters and Arguments (Visual Basic) | Microsoft Docs"
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
  - "procedures, arguments"
  - "procedures, parameters"
  - "parameters, and arguments"
  - "procedure arguments"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], and parameters"
  - "procedure parameters"
  - "parameters, definition"
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Differences Between Parameters and Arguments (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

在大多數情況下，程序必須有一些可在其中呼叫程序之環境的相關資訊。  執行重複或共用工作的程序，每一次呼叫都使用不同的資訊。  該資訊是由呼叫程序時傳給它的變數、常數和運算式所組成。  
  
 為了讓程序使用此資訊，程序將定義「*參數*」\(Parameter\)，而呼叫程式碼也會將「*引數*」\(Argument\) 傳給該參數。  您可以將參數想像成停車位，將引數當做汽車。  就像不同的汽車能在不同的時間停入停車位，呼叫程式碼也可以在每次呼叫程序時，將不同的引數傳給同一個參數。  
  
## 參數  
 一個「*參數*」\(Parameter\) 代表一個值，您必須在呼叫程序時傳遞該參數。  程序的宣告會定義其參數。  
  
 當您定義 `Function` 或 `Sub` 程序時，會在緊接著程序名稱之後的括號中指定「*參數清單*」\(Parameter List\)。  您會針對每個參數，指定名稱、資料型別和傳遞機制 \([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 或 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)\)。  您也可以指定某個參數為選擇性參數，  這表示呼叫程式碼不必將值傳給該參數。  
  
 每一個參數的名稱都可做為程序內部的「*區域變數*」\(Local Variable\)。  您可以使用任何其他變數的相同方式來使用參數名稱。  
  
## 引數  
 「*引數*」\(Argument\) 代表您在呼叫程序時會傳給程序參數的值。  呼叫程式碼會在呼叫程序時提供引數。  
  
 呼叫 `Function` 或 `Sub` 程序時，會在緊接著程序名稱之後的括號中包含「*引數清單*」\(Argument List\)。  每一個引數會對應至清單中相同位置的參數。  
  
 與參數定義不同的是，引數沒有名稱。  每個引數都是一個運算式，可包含零或多個變數、常數和常值 \(Literal\)。  評估運算式的資料型別，通常應該會符合為對應參數所定義的資料型別，且不論在任何情況下，都必須能將它轉換成參數型別。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define a Parameter for a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-parameter-for-a-procedure.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)