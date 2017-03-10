---
title: "Procedures in Visual Basic | Microsoft Docs"
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
  - "procedures, structured code"
  - "Visual Basic code, procedures"
  - "procedures, types of"
  - "structured code, procedures"
  - "procedures"
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Procedures in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

「*程序*」\(Procedure\) 是用宣告陳述式 \(`Function`、`Sub`、`Operator`、`Get`、`Set`\) 和相符 `End` 宣告所括住的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 陳述式區塊。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的所有可執行陳述式都必須位在某個程序中。  
  
## 呼叫程序  
 從程式碼的其他位置叫用 \(Invoke\) 程序。  這即為「*程序呼叫*」\(Procedure Call\)。  程序執行完成時，會將控制權傳回給叫用它的程式碼 \(即「*呼叫程式碼*」\(Calling Code\)\)。  呼叫程式碼是一種陳述式 \(Statement\)，或是陳述式中的運算式，可依照名稱指定程序並轉換控制權給它。  
  
## 從程序傳回  
 程序執行完成時，會將控制權傳回給呼叫程式碼。  若要這樣做，則可使用 [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md)、程序的適當 [Exit Statement](../../../../visual-basic/language-reference/statements/exit-statement.md) 陳述式，或程序的 [End \<keyword\> Statement](../../../../visual-basic/language-reference/statements/end-keyword-statement.md) 陳述式。  控制權接著會在程序呼叫點之後傳遞給呼叫程式碼。  
  
-   使用 `Return` 陳述式，控制權會立即傳回給呼叫程式碼。  `Return` 陳述式後面的陳述式則不會執行。  在相同程序中可有一個以上的 `Return` 陳述式。  
  
-   使用 `Exit Sub` 或 `Exit Function` 陳述式，控制權會立即傳回給呼叫程式碼。  `Exit` 陳述式後面的陳述式則不會執行。  在相同程序中可有一個以上的 `Exit` 陳述式，且可在相同程序中混合 `Return` 和 `Exit` 陳述式。  
  
-   如果程序沒有 `Return` 或 `Exit` 陳述式，則它會在程序主體的最後一個陳述式後面使用 `End Sub` 或 `End Function`、`End Get` 或 `End Set` 陳述式做結束。  `End` 陳述式會立即將控制權傳回給呼叫程式碼。  在程序中只可以有一個 `End` 陳述式。  
  
## 參數和引數  
 在大部分情況下，每次呼叫程序時，都需要處理不同的資料。  您可以將這個資訊傳遞給程序，做為程序呼叫的一部分。  程序會定義零或多個的「*參數*」\(Parameter\)，而每個都表示它希望您傳遞給它的值。  與程序定義中的每個參數對應的是程序呼叫中的「*引數*」\(Argument\)。  引數表示傳遞給所指定程序呼叫中對應參數的值。  
  
## 程序型別  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 使用數種程序型別：  
  
-   [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)：執行動作，但不會將值傳回給呼叫程式碼。  
  
-   事件處理程序：是 `Sub` 程序，依據使用者動作或程式項目所引發的事件而執行。  
  
-   [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)：將值傳回給呼叫程式碼。  它們可以在傳回之前執行其他動作。  
  
-   [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)：傳回並指派物件或模組的屬性值。  
  
-   [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)：在一或兩個運算元是最新定義的類別或結構時，定義標準運算子的行為。  
  
-   [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)：除了定義它們的一般參數外，還會定義一或多個「*型別參數*」\(Type Parameter\)，因此呼叫程式碼可在每次進行呼叫時傳遞特定的資料型別。  
  
## 程序和結構化程式碼  
 應用程式中的每行程式碼都必須位在某個程序內 \(例如 `Main`、`calculate` 或 `Button1_Click`\)。  如果您將大型程序細分為較小的程序，您的應用程式會比較容易讀取。  
  
 程序適用於進行重複或共用的工作，例如常用的計算、文字和控制項的操作，以及資料庫作業。  您可以從程式碼中許多不同的位置呼叫程序，如此您可以將程序當做應用程式的建置區塊。  
  
 用程序來建構程式碼有下列優點：  
  
-   程序可讓您將應用程式分成不連續的邏輯單位 \(Logical Unit\)。  與偵錯不用程序的整個程式相比，您可以更輕易地對個別單位進行偵錯。  
  
-   開發在某個程式中使用的程序之後，通常不需要太多修改，甚至不用修改，就可以在其他程式中使用。  這可以協助您避免程式碼重複。  
  
## 請參閱  
 [How to: Create a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)