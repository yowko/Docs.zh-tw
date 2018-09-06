---
title: 函式運算式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: cfdd17f6f4ee6c4ddb3fa73ab3ec9c5ce46a162f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788239"
---
# <a name="function-expression-visual-basic"></a>函式運算式 (Visual Basic)
宣告參數與定義的函式的 lambda 運算式的程式碼。  
  
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
|`parameterlist`|選擇性。 本機變數的名稱，表示此程序參數的清單。 括號必須要有即使清單是空的。 請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`expression`|必要。 在單一運算式。 運算式的類型是函式的傳回型別。|  
|`statements`|必要。 陳述式會使用傳回值的清單`Return`陳述式。 (請參閱[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。)傳回值的類型是函式的傳回型別。|  
  
## <a name="remarks"></a>備註  
 A *lambda 運算式*是函式不會計算並傳回值的名稱。 您可以使用 lambda 運算式任何地方使用委派類型，除非做為引數`RemoveHandler`。 如需委派和 lambda 運算式與委派使用的詳細資訊，請參閱[委派陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)並[寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## <a name="lambda-expression-syntax"></a>Lambda 運算式語法  
 Lambda 運算式的語法類似於標準函式。 差異如下所示：  
  
-   Lambda 運算式沒有名稱。  
  
-   Lambda 運算式不能有修飾詞，例如`Overloads`或`Overrides`。  
  
-   不使用 lambda 運算式`As`子句來指定函式的傳回型別。 相反地，從單行 lambda 運算式的主體，所評估的值或多行 lambda 運算式的傳回值推斷型別。 例如，單行 lambda 運算式的主體是否`Where cust.City = "London"`，其傳回類型是`Boolean`。  
  
-   單行 lambda 運算式的主體必須是運算式，不是陳述式。 主體可以包含的函式程序的呼叫，但不是呼叫子函數程序。  
  
-   可能是所有的參數必須必須推斷資料類型或全部指定。  
  
-   不允許 Optional 和 Paramarray 參數。  
  
-   不允許泛型參數。  
  
## <a name="example"></a>範例  
 下列範例顯示兩種方式可建立簡單的 lambda 運算式。 第一個範例使用`Dim`提供函式的名稱。 若要呼叫的函式，您將會傳送參數的值。  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>範例  
 或者，您可以宣告，並在同一時間執行的函式。  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>範例  
 以下是遞增其引數和傳回值的 lambda 運算式的範例。 此範例會顯示函式的這兩個單行和多行 lambda 運算式語法。 如需其他範例，請參閱 < [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>範例  
 Lambda 運算式為基礎的查詢運算子，在許多[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]，並可以在以方法為基礎的查詢中明確使用。 下列範例示範典型[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]後面接著的查詢轉譯成方法格式的查詢。  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 如需有關查詢方法的詳細資訊，請參閱[查詢](../../../visual-basic/language-reference/queries/index.md)。 如需有關標準查詢運算子的詳細資訊，請參閱[標準查詢運算子概觀](../../programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)  
 [數值比較](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [布林運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [If 運算子](../../../visual-basic/language-reference/operators/if-operator.md)  
 [寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
