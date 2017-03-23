---
title: "函式運算式 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9b181b18a28a8b92a392fffdc10e08690d54f545
ms.lasthandoff: 03/13/2017

---
# <a name="function-expression-visual-basic"></a>函式運算式 (Visual Basic)
宣告的參數和函式的 lambda 運算式定義的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`parameterlist`|選擇項。 本機變數的名稱，表示此程序的參數清單。 括號必須存在，即使清單是空的。 請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`expression`|必要項。 單一運算式。 運算式的類型是函式的傳回型別。|  
|`statements`|必要項。 使用傳回值的陳述式清單`Return`陳述式。 (請參閱[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。)傳回值的類型是函式的傳回型別。|  
  
## <a name="remarks"></a>備註  
 A *lambda 運算式*是函式不會計算並傳回值的名稱。 您可以使用 lambda 運算式任何地方使用委派類型，除了做為引數`RemoveHandler`。 如需委派和使用委派 lambda 運算式的詳細資訊，請參閱[委派陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)和[寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## <a name="lambda-expression-syntax"></a>Lambda 運算式語法  
 Lambda 運算式的語法類似於標準函式。 差異如下︰  
  
-   Lambda 運算式沒有名稱。  
  
-   Lambda 運算式不能有修飾詞，例如`Overloads`或`Overrides`。  
  
-   不使用 lambda 運算式`As`子句來指定函式的傳回型別。 相反地，來自單行 lambda 運算式的主體，所評估的值或多行 lambda 運算式的傳回值推斷型別。 例如，如果單行 lambda 運算式的主體是`Where cust.City = "London"`，其傳回型別是`Boolean`。  
  
-   單行 lambda 運算式的主體必須是運算式，而不是陳述式。 主體可以包含呼叫的函式程序，但不呼叫 sub 程序。  
  
-   必須推斷資料型別或所有必須指定所有參數。  
  
-   不允許選用和參數陣列參數。  
  
-   不允許泛型參數。  
  
## <a name="example"></a>範例  
 下列範例示範兩種方式建立簡單的 lambda 運算式。 第一個使用`Dim`提供函式的名稱。 若要呼叫的函式，您傳送參數的值。  
  
 [!code-vb[VbVbalrLambdas #&1;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas #&2;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>範例  
 或者，您可以宣告和函式執行一次。  
  
 [!code-vb[VbVbalrLambdas #&3;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>範例  
 以下是遞增其引數和傳回值的 lambda 運算式的範例。 函式的兩個單行或多行 lambda 運算式語法範例。 如需詳細資訊，請參閱[Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbVbalrLambdas #&14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>範例  
 Lambda 運算式為基礎的查詢運算子，在許多[!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]，並可以在以方法為基礎的查詢中明確地使用。 下列範例示範典型[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)]後面接著的查詢轉譯成方法格式的查詢。  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 如需查詢方法的詳細資訊，請參閱[查詢](../../../visual-basic/language-reference/queries/queries.md)。 如需標準查詢運算子的詳細資訊，請參閱[標準查詢運算子概觀](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)。  
  
## <a name="see-also"></a>另請參閱  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)   
 [值的比較](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [布林運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [如果運算子](../../../visual-basic/language-reference/operators/if-operator.md)   
 [寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
