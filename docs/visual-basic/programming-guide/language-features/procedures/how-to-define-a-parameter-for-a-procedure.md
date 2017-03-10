---
title: "How to: Define a Parameter for a Procedure (Visual Basic) | Microsoft Docs"
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
  - "procedure parameters, defining data types for"
  - "procedures, parameters"
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedure parameters, defining"
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Define a Parameter for a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

「*參數*」\(Parameter\) 允許呼叫程式碼在呼叫程序時將值傳遞給該程序。  您可以利用指定參數名稱與資料型別，為程序宣告每一個參數，就像宣告一般變數的方式一樣。  而且，您也可以指定傳遞的機制，以及該參數是否為選擇性 \(Optional\)。  
  
 如需詳細資訊，請參閱[Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)。  
  
### 若要定義程序參數  
  
1.  在程序宣告中，將參數名稱加入至程序參數清單 \(用逗號隔開每個參數\)。  
  
2.  決定參數的資料型別。  
  
3.  在參數名稱後面緊接著 `As` 子句，以指定資料型別。  
  
4.  決定要用於參數的傳遞機制。  一般而言，除非想讓程序可變更它在呼叫程式碼中的值，否則會以傳值 \(By Value\) 方式傳遞參數。  
  
5.  在參數名稱前面加上 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 或 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，以指定傳遞機制。  如需詳細資訊，請參閱[Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
6.  如果是選擇性參數，請在傳遞機制前面加上 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)，且在參數資料型別後面緊接著等號 \(`=`\) 和預設值。  
  
     下列範例會定義含有三個參數之 `Sub` 程序的大綱。  前兩個是必要項，而第三個是選擇項。  參數清單中的參數宣告是用逗號隔開。  
  
     [!code-vb[VbVbcnProcedures#33](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-define-a-paramete_1.vb)]  
  
     第一個參數會接受 \(Accept\)  `customer`  物件，而 `updateCustomer` 可直接更新傳遞給 `c` 的變數，因為引數是以 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) 方式傳遞。  程序無法變更後兩個引數的值，因為它們是以 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 方式傳遞。  
  
     如果呼叫程式碼未提供  `level`  參數的值，則 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會將它設為預設值 0。  
  
     如果型別檢查 \(Type Checking\) 參數 \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) 為 `Off`，則在定義參數時，`As` 子句為選擇性的。  然而，如果任一參數會使用 `As` 子句，則所有參數就必須使用它。  如果型別檢查參數是 `On`，則每個參數定義都要有 `As` 子句。  
  
     指定所有程式項目的資料型別稱為「*強式型別*」\(Strong Typing\)。  設定 `Option Strict On` 時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會強制使用強式型別。  因為下列理由，所以強烈建議您這麼做：  
  
    -   讓 IntelliSense 能夠支援變數和參數。  這能讓您在輸入程式碼時看到其屬性和其他成員。  
  
    -   讓編譯器能夠執行型別檢查。  這有助於找出因為錯誤 \(例如溢位\) 而導致執行階段發生失敗的陳述式。  這也能夠偵測在不支援變數的物件上所進行的方法呼叫。  
  
    -   執行程式碼的速度較快。  其中一個理由是，如果未指定程式設計項目的資料型別，則 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會將它指派為 `Object` 型別。  編譯的程式碼可能必須在 `Object` 與其他資料型別之間進行來回轉換，因而會降低效能。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [物件導向程式設計](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)