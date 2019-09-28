---
title: 函式運算式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 0ab4a77395b478df06f34240212438f3e6e18f6e
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592199"
---
# <a name="function-expression-visual-basic"></a>函式運算式 (Visual Basic)
宣告定義函式 lambda 運算式的參數和程式碼。  
  
## <a name="syntax"></a>語法  
  
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
|`parameterlist`|選擇性。 本機變數名稱的清單，代表此程式的參數。 即使清單是空的，括弧也必須存在。 請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`expression`|必要項。 單一運算式。 運算式的類型是函式的傳回型別。|  
|`statements`|必要項。 使用 `Return` 語句來傳回值的語句清單。 （請參閱[Return 語句](../../../visual-basic/language-reference/statements/return-statement.md)）。傳回值的類型是函式的傳回型別。|  
  
## <a name="remarks"></a>備註  
 *Lambda 運算式*是沒有名稱的函式，會計算並傳回值。 您可以在任何可使用委派類型的位置使用 lambda 運算式，但 `RemoveHandler` 的引數除外。 如需委派的詳細資訊，以及搭配使用 lambda 運算式和委派的用法，請參閱[委派語句](../../../visual-basic/language-reference/statements/delegate-statement.md)和[寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## <a name="lambda-expression-syntax"></a>Lambda 運算式語法  
 Lambda 運算式的語法類似于標準函式。 差異如下：  
  
- Lambda 運算式沒有名稱。  
  
- Lambda 運算式不能有修飾詞，例如 `Overloads` 或 `Overrides`。  
  
- Lambda 運算式不會使用 `As` 子句來指定函式的傳回型別。 相反地，型別是從單行 lambda 運算式的主體評估為的值，或多行 lambda 運算式的傳回值推斷而來。 例如，如果單行 lambda 運算式的主體為 `Where cust.City = "London"`，則其傳回型別會 `Boolean`。  
  
- 單行 lambda 運算式的主體必須是運算式，而不是語句。 主體可以包含函式程式的呼叫，而不是對 sub 程式的呼叫。  
  
- 所有參數都必須具有指定的資料類型，否則必須推斷全部。  
  
- 不允許選擇性和 Paramarray 參數。  
  
- 不允許泛型參數。  
  
## <a name="example"></a>範例  
 下列範例示範兩種建立簡單 lambda 運算式的方式。 第一個使用 `Dim` 來提供函式的名稱。 若要呼叫函式，請傳送參數的值。  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a>範例  
 或者，您可以同時宣告和執行函數。  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a>範例  
 以下是 lambda 運算式的範例，它會遞增其引數並傳回值。 此範例會顯示函數的單行和多行 lambda 運算式語法。 如需更多範例，請參閱[Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a>範例  
 Lambda 運算式在 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 中的許多查詢運算子，而且可以在以方法為基礎的查詢中明確地使用。 下列範例顯示一般的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢，然後將查詢轉譯成方法格式。  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 如需查詢方法的詳細資訊，請參閱[查詢](../../../visual-basic/language-reference/queries/index.md)。 如需標準查詢運算子的詳細資訊，請參閱[標準查詢運算子總覽](../../programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
- [數值比較](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [布林運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [If 運算子](../../../visual-basic/language-reference/operators/if-operator.md)
- [寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
