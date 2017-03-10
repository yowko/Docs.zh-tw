---
title: "Function Expression (Visual Basic) | Microsoft Docs"
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
  - "Function expression [Visual Basic]"
  - "functions [Visual Basic], function expressions"
  - "lambda expressions [Visual Basic], function expression"
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Function Expression (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

宣告定義函式 Lambda 運算式的參數和程式碼。  
  
## 語法  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`parameterlist`|選擇項。  代表此程序之參數的區域變數名稱清單。  就算清單是空白的，還是要保留括弧。  請參閱 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`expression`|必要項。  單一運算式。  運算式的型別是函式傳回的型別。|  
|`statements`|必要項。  透過使用 `Return` 陳述式傳回值的陳述式清單。  \(請參閱[Return Statement](../../../visual-basic/language-reference/statements/return-statement.md)\)。 傳回值的型別是函式的傳回型別。|  
  
## 備註  
 「*Lambda 運算式*」\(Lambda Expression\) 是沒有名稱的函式，會計算並傳回值。  除了做為 `RemoveHandler` 的引數，您可以將 Lambda 運算式用於任何能使用委派型別的地方。  如需委派以及配合委派使用 Lambda 運算式的詳細資訊，請參閱 [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)和[Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## Lambda 運算式語法  
 Lambda 運算式的語法類似標準函式。  其差異如下：  
  
-   Lambda 運算式沒有名稱。  
  
-   Lambda 運算式不能有修飾詞 \(Modifier\)，例如 `Overloads` 或 `Overrides`。  
  
-   Lambda 運算式不會使用 `As` 子句指定函式的傳回型別。  相反的，型別是由單行 Lambda 運算式主體評估值或多行 Lambda 運算式傳回值推斷而來。  例如，如果單行 Lambda 運算式的主體是 `Where cust.City = "London"`，其傳回型別為 `Boolean`。  
  
-   單行 Lambda 運算式的主體必須是運算式，而不是陳述式。  主體可以由對 Function 程序的呼叫組成，但不可由對子程序的呼叫組成。  
  
-   所有參數都必須具有指定的資料型別，不然所有參數就都必須經過推斷。  
  
-   不允許使用 Optional 和 Paramarray 參數。  
  
-   不允許使用泛型參數。  
  
## 範例  
 下列範例會示範建立簡單 Lambda 運算式的兩個方法。  第一個使用 `Dim` 提供函式的名稱。  若要呼叫函式，則傳送參數的值。  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/vbvbalrlambdas/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/vbvbalrlambdas/Class1.vb#2)]  
  
## 範例  
 或者，您可以同時宣告並執行函式。  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/vbvbalrlambdas/Class1.vb#3)]  
  
## 範例  
 以下是會遞增其引數並傳回值的 Lambda 運算式範例。  下列範例同時顯示函式的單行和多行 Lambda 運算式語法。  如需更多範例，請參閱 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/vbvbalrlambdas/Class1.vb#14)]  
  
## 範例  
 Lambda 運算式是許多 [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext-md.md)] 中之查詢運算子的基礎，能明確用於方法架構查詢中。  下列範例示範了典型的 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 查詢，緊跟著則將查詢轉譯為方法格式。  
  
```vb#  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 如需查詢方法的詳細資訊，請參閱[Queries](../../../visual-basic/language-reference/queries/queries.md)。  如需標準查詢運算子的詳細資訊，請參閱[Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
## 請參閱  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Value Comparisons](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [If Operator](../../../visual-basic/language-reference/operators/if-operator.md)   
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)