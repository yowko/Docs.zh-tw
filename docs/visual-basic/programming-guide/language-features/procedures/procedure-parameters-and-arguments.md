---
title: "Procedure Parameters and Arguments (Visual Basic) | Microsoft Docs"
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
  - "procedures, argument lists"
  - "values, passing to procedures"
  - "arguments [Visual Basic], passing"
  - "procedures, parameters"
  - "Visual Basic code, argument lists"
  - "Visual Basic code, procedures"
  - "parameters, Visual Basic procedures"
  - "parameters, lists"
  - "arguments [Visual Basic], Visual Basic procedures"
  - "arguments [Visual Basic], procedures"
  - "parameter lists"
  - "Visual Basic code, parameter lists"
  - "argument lists"
  - "procedures, parameter lists"
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Procedure Parameters and Arguments (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

在大多數情況下，程序需要一些可在其中呼叫程序之環境的相關資訊。  執行重複或共用工作的程序，每一次呼叫都使用不同的資訊。  該資訊是由呼叫程序時傳給它的變數、常數和運算式所組成。  
  
 「*參數*」\(Parameter\) 表示您必須在呼叫程序時提供的值，  程序的宣告會定義其參數。  
  
 您可以定義不含參數、含一個參數，或含多個參數的程序。  程序定義中用於指定參數的部分稱為「*參數清單*」\(Parameter List\)。  
  
 「*引數*」\(Argument\) 表示呼叫程序時，提供給程序參數的值。  呼叫程式碼會在呼叫程序時提供引數。  用於指定引數的程序呼叫部分稱為「*引數清單*」\(Argument List\)。  
  
 下圖顯示一段程式碼，該程式碼會從兩個不同的地點呼叫程序 `safeSquareRoot`。  第一個呼叫會將變數 `x` 值 \(4.0\) 傳遞到參數 `number`，並將 `root` 中的傳回值 \(2.0\) 指派給變數 `y`。  第二個呼叫會將常值 9.0 傳遞到 `number`，並將傳回值 \(3.0\) 指派給變數 `z`。  
  
 ![傳遞引數至參數示意圖](../../../../visual-basic/programming-guide/language-features/procedures/media/parametersargue.gif "ParametersArgue")  
將引數傳遞至參數  
  
 如需詳細資訊，請參閱[Differences Between Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)。  
  
## 參數資料型別  
 您可以在參數宣告中使用 `As` 子句來定義參數的資料型別。  例如，下列函式可接受字串和整數。  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 如果型別檢查參數 \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) 是 `Off,`，則 `As` 子句是選擇項，但若有任一參數使用此子句，則所有的參數都必須使用此子句。  如果型別檢查是 `On`，則所有的程序參數都必須使用 `As` 子句。  
  
 如果呼叫程式碼必須提供與對應參數不同資料型別的引數，例如 `Byte` 對 `String` 參數，則必須執行下列其中一項：  
  
-   只提供資料型別可擴展至參數資料型別的引數  
  
-   設定 `Option Strict Off` 以允許隱含的縮小轉換  
  
-   使用轉換關鍵字以明確轉換資料型別  
  
### 型別參數  
 除了一般參數以外，「*泛型程序*」\(Generic Procedure\) 也會定義一或多個「*型別參數*」\(Type Parameter\)。  泛型程序可讓呼叫程式碼在每次呼叫程序時，傳遞不同的資料型別，以便根據個別呼叫的需求，調整資料型別。  請參閱 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define a Parameter for a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-parameter-for-a-procedure.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)