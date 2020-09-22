---
title: 函式運算式
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 719969be23a6d94f22a1d86cb4ad3f37e4c3b254
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873415"
---
# <a name="function-expression-visual-basic"></a>函式運算式 (Visual Basic)

宣告定義函數 lambda 運算式的參數和程式碼。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`parameterlist`|選擇性。 區域變數名稱的清單，這些變數表示此程式的參數。 即使清單是空的，也必須有括弧。 請參閱 [參數清單](../statements/parameter-list.md)。|  
|`expression`|必要。 單一運算式。 運算式的型別是函數的傳回型別。|  
|`statements`|必要。 使用語句傳回值的語句清單 `Return` 。  (請參閱 [Return 語句](../statements/return-statement.md)。 ) 傳回值的類型是函式的傳回型別。|  
  
## <a name="remarks"></a>備註  

 *Lambda 運算式*是沒有名稱的函式，其會計算並傳回值。 除了做為的引數以外，您可以在任何可使用委派類型的位置使用 lambda 運算式 `RemoveHandler` 。 如需委派的詳細資訊，以及使用 lambda 運算式搭配委派的詳細資訊，請參閱 [委派語句](../statements/delegate-statement.md) 和 [寬鬆委派轉換](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## <a name="lambda-expression-syntax"></a>Lambda 運算式語法  

 Lambda 運算式的語法與標準函式的語法類似。 差異如下：  
  
- Lambda 運算式沒有名稱。  
  
- Lambda 運算式不能有修飾詞，例如 `Overloads` 或 `Overrides` 。  
  
- Lambda 運算式不使用 `As` 子句來指定函式的傳回型別。 相反地，型別是從單行 lambda 運算式的主體評估為的值，或是多行 lambda 運算式的傳回值推斷而來。 例如，如果單行 lambda 運算式的主體是 `Where cust.City = "London"` ，其傳回型別為 `Boolean` 。  
  
- 單行 lambda 運算式的主體必須是運算式，而非語句。 本文可能包含對函數程式的呼叫，但不包含對 sub 程式的呼叫。  
  
- 所有參數都必須有指定的資料類型，或全部都必須加以推斷。  
  
- 不允許選擇性和 Paramarray 參數。  
  
- 不允許泛型參數。  
  
## <a name="example"></a>範例  

 下列範例示範兩種建立簡單 lambda 運算式的方式。 第一個使用 `Dim` 來提供函數的名稱。 若要呼叫函式，請將參數的值傳送給。  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a>範例  

 或者，您也可以同時宣告和執行函數。  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a>範例  

 以下是 lambda 運算式的範例，它會遞增其引數並傳回值。 此範例會顯示函數的單行和多行 lambda 運算式語法。 如需更多範例，請參閱 [Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a>範例  

 Lambda 運算式在語言整合查詢中有許多查詢運算子 (LINQ) ，而且可以在以方法為基礎的查詢中明確地使用。 下列範例顯示一般 LINQ 查詢，然後將查詢轉譯成方法格式。  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 如需查詢方法的詳細資訊，請參閱 [查詢](../queries/index.md)。 如需標準查詢運算子的詳細資訊，請參閱 [標準查詢運算子總覽](../../programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [Function 陳述式](../statements/function-statement.md)
- [Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [運算子和運算式](../../programming-guide/language-features/operators-and-expressions/index.md)
- [陳述式](../../programming-guide/language-features/statements.md)
- [數值比較](../../programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [布林運算式](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [If 運算子](if-operator.md)
- [寬鬆委派轉換](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
