---
title: "Sub Expression (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "lambda expressions [Visual Basic], sub expression"
  - "Sub Expression [Visual Basic]"
  - "subroutines [Visual Basic], sub expressions"
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sub Expression (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

宣告定義副程式 Lambda 運算式的參數和程式碼。  
  
## 語法  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`parameterlist`|選擇項。  代表此程序之參數的區域變數名稱清單。  就算清單是空白的，還是要保留括弧。  如需詳細資訊，請參閱 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`statement`|必要項。  單一陳述式。|  
|`statements`|必要項。  陳述式清單。|  
  
## 備註  
 「*Lambda 運算式*」\(Lambda Expression\) 是沒有名稱的副程式，其中會執行一個或多個陳述式。  除了做為 `RemoveHandler` 的引數，您可以將 Lambda 運算式用於任何能使用委派型別的地方。  如需委派以及配合委派使用 Lambda 運算式的詳細資訊，請參閱 [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)和[Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## Lambda 運算式語法  
 Lambda 運算式的語法和標準副程式的語法類似。  其差異如下：  
  
-   Lambda 運算式沒有名稱。  
  
-   Lambda 運算式不能有修飾詞 \(Modifier\)，例如 `Overloads` 或 `Overrides`。  
  
-   單行 Lambda 運算式的主體必須是陳述式，而不是運算式。  主體可以由對子程序的呼叫組成，但不可由對 Function 程序的呼叫組成。  
  
-   在 Lambda 運算式中，所有參數都必須具有指定的資料型別，不然所有參數就都必須經過推斷。  
  
-   Lambda 運算式中不允許選擇性及 `ParamArray` 參數。  
  
-   Lambda 運算式中不允許泛型參數。  
  
## 範例  
 以下是會將值寫入至主控台的 Lambda 運算式範例。  下列範例同時顯示副程式的單行和多行 Lambda 運算式語法。  如需更多範例，請參閱 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!CODE [VbVbalrLambdas#15](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrLambdas#15)]  
  
## 請參閱  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)