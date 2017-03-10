---
title: "函式程序 (Visual Basic) | Microsoft Docs"
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
  - "函式程序"
  - "傳回值，函式程序"
  - "Visual Basic 程式碼，程序"
  - "程序，呼叫"
  - "程序，函式程序"
  - "語法，函式程序"
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# 函式程序 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

`Function` 程序是一組以 `Function` 和 `End Function` 陳述式前後括起來的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 陳述式。  `Function` 程序會執行工作，然後將控制權傳回給呼叫程式碼。  當它傳回控制權時，它也會傳回一值給呼叫程式碼。  
  
 每當程序被呼叫時，它的陳述式會以 `Function` 陳述式之後的第一個可執行陳述式開始執行，並以它所遇到的第一個 `End Function`、`Exit Function` 或 `Return` 陳述式結束。  
  
 您可以在模組、類別或結構中定義 `Function` 程序。  它會預設值為 `Public`，這表示您可以從應用程式的任何位置呼叫它，但這個應用程式必須在定義它的模組、類別或結構中擁有權限。  
  
 `Function` 程序可以取得由呼叫程式碼所傳送給它的引數，例如常數、變數或運算式。  
  
## 宣告語法  
 宣告 `Function` 程序的語法如下：  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *modifiers* 可以指定存取層級和有關多載、覆寫、共用及遮蔽的資訊。  如需詳細資訊，請參閱[Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)。  
  
 您可以利用對 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)所用的同一方法，宣告每一個參數。  
  
### 資料型別  
 每一個 `Function` 程序都有一個資料型別，與變數一樣。  這個資料型別是由 `Function` 陳述式中的 `As` 子句所指定，而且它可以決定函式傳回給呼叫程式碼之值的資料型別。  下列範例宣告將對此進行說明。  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 如需詳細資訊，請參閱 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) 中的參數。  
  
## 傳回值  
 `Function` 程序傳回到呼叫程式碼的呼叫它的傳回值。  程序會以下列其中一種方式傳回此值：  
  
-   它會使用 `Return` 陳述式來指定傳回值，並立即將控制權傳回給呼叫程式。  下列範例將說明這點。  
  
    ```vb  
    Function FunctionName [(ParameterList)] As ReturnType  
        ' The following statement immediately transfers control back  
        ' to the calling code and returns the value of Expression.  
        Return Expression  
    End Function  
    ```  
  
-   它會在程序的一個或多個陳述式中指派一個值給自己的函式名稱。  直到 `Exit Function` 或 `End Function` 陳述式執行之後，才會將控制權傳回給呼叫程式。  下列範例將說明這點。  
  
    ```vb  
    Function FunctionName [(ParameterList)] As ReturnType  
        ‘ The following statement does not transfer control back to the calling code.  
        FunctionName = Expression  
        ' When control returns to the calling code, Expression is the return value.  
    End Function  
    ```  
  
 將傳回值指派給函式名稱的優點是，直到其遇上 `Exit Function` 或 `End Function` 陳述式之後，才會從程序傳回控制權。  這可讓您指派一個基本值，如有必要再加以調整。  
  
 如需傳回值的詳細資訊，請參閱 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)。  如需傳回陣列的詳細資訊，請參閱 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## 呼叫語法  
 您可以藉由將 `Function` 程序的名稱和引數包括在指派陳述式 \(Assignment Statement\) 的右邊或在運算式中，以叫用 \(Invoke\) 該程序。  您必須為所有非選擇性的引數提供值，也必須將引數清單用括號括起來。  如果未提供引數，您也可以省略括號。  
  
 呼叫 `Function` 程序的語法如下：  
  
 *左值* `=` *functionname* `[(` *argumentlist* `)]`  
  
 `If ((` *functionname* `[(` *argumentlist* `)] / 3) <=` *運算式* `) Then`  
  
 當您呼叫 `Function` 程序時，不一定要使用它的傳回值。  如果您不使用，則會執行該函式的所有動作，但會忽略傳回值。  <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 通常會以這種方式呼叫。  
  
### 宣告和呼叫的說明  
 下列 `Function` 程序會在已知其他兩邊值的情況下，計算直角三角形的最長邊 \(也稱為斜邊\)。  
  
 [!code-vb[VbVbcnProcedures#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/function-procedures_1.vb)]  
  
 下列範例示範 `hypotenuse` 的典型呼叫。  
  
 [!code-vb[VbVbcnProcedures#6](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/function-procedures_2.vb)]  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [How to: Create a Procedure that Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure-that-returns-a-value.md)   
 [How to: Return a Value from a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-return-a-value-from-a-procedure.md)   
 [How to: Call a Procedure That Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)