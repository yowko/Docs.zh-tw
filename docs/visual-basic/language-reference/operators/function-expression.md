---
title: 函式運算式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 29bf95a336b6f6ed5c9c310c9ea7575a91089361
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604883"
---
# <a name="function-expression-visual-basic"></a>函式運算式 (Visual Basic)
宣告參數與函式的 lambda 運算式定義的程式碼。  
  
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
|`parameterlist`|選擇性。 本機變數的名稱，代表此程序參數的清單。 括號必須要有即使清單是空的。 請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`expression`|必要。 在單一運算式。 運算式的類型是函式的傳回型別。|  
|`statements`|必要。 陳述式會使用傳回值的清單`Return`陳述式。 (請參閱[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。)傳回值的類型是函式的傳回型別。|  
  
## <a name="remarks"></a>備註  
 A *lambda 運算式*是函式不會計算並傳回值的名稱。 您可以使用 lambda 運算式任何位置使用委派類型，除了做為引數`RemoveHandler`。 如需委派和 lambda 運算式與委派的使用詳細資訊，請參閱[委派陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)和[寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## <a name="lambda-expression-syntax"></a>Lambda 運算式語法  
 Lambda 運算式的語法類似於標準函式。 差異如下所示：  
  
-   Lambda 運算式沒有名稱。  
  
-   Lambda 運算式不能有修飾詞，例如`Overloads`或`Overrides`。  
  
-   Lambda 運算式不使用`As`子句來指定函式的傳回型別。 相反地，從單行 lambda 運算式的主體，所評估的值或多行 lambda 運算式的傳回值推斷的類型。 例如，如果是單行 lambda 運算式的主體`Where cust.City = "London"`，其傳回類型是`Boolean`。  
  
-   單行 lambda 運算式的主體必須是運算式，不是陳述式。 主體可以包含呼叫的函式程序，但不 sub 程序的呼叫。  
  
-   必須推斷資料型別或所有必須指定所有參數。  
  
-   不允許選擇性和 Paramarray 參數。  
  
-   不允許泛型參數。  
  
## <a name="example"></a>範例  
 下列範例顯示兩種方式可建立簡單的 lambda 運算式。 第一個範例使用`Dim`提供函式的名稱。 若要呼叫的函式，您傳送參數的值。  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>範例  
 或者，您可以宣告和函式同時執行。  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>範例  
 以下是遞增其引數和傳回值的 lambda 運算式的範例。 函式的兩個單行或多行 lambda 運算式語法範例。 如需其他範例，請參閱[Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>範例  
 Lambda 運算式為基礎的查詢運算子內許多[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]，並可以在以方法為基礎的查詢中明確使用。 下列範例示範典型[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]後面接著的查詢轉譯成方法格式的查詢。  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 如需有關查詢方法的詳細資訊，請參閱[查詢](../../../visual-basic/language-reference/queries/queries.md)。 如需標準查詢運算子的詳細資訊，請參閱[標準查詢運算子概觀](../../programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)  
 [數值比較](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [布林運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [If 運算子](../../../visual-basic/language-reference/operators/if-operator.md)  
 [寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
