---
title: Sub 運算式
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: e564fa3f717fc1a9f4e9961d9b3e961912a4d56b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873327"
---
# <a name="sub-expression-visual-basic"></a>Sub 運算式 (Visual Basic)

宣告定義副程式 lambda 運算式的參數和程式碼。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`parameterlist`|選擇性。 區域變數名稱的清單，這些變數表示程式的參數。 即使清單是空的，也必須有括弧。 如需詳細資訊，請參閱 [Parameter List](../statements/parameter-list.md)。|  
|`statement`|必要。 單一語句。|  
|`statements`|必要。 陳述式的清單。|  
  
## <a name="remarks"></a>備註  

 *Lambda 運算式*是沒有名稱，且會執行一或多個語句的副程式。 您可以在任何可使用委派類型的位置使用 lambda 運算式，但做為的引數除外 `RemoveHandler` 。 如需委派的詳細資訊，以及使用 lambda 運算式搭配委派的詳細資訊，請參閱 [委派語句](../statements/delegate-statement.md) 和 [寬鬆委派轉換](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## <a name="lambda-expression-syntax"></a>Lambda 運算式語法  

 Lambda 運算式的語法與標準副程式的語法類似。 差異如下：  
  
- Lambda 運算式沒有名稱。  
  
- Lambda 運算式不能有修飾詞，例如 `Overloads` 或 `Overrides` 。  
  
- 單行 lambda 運算式的主體必須是語句，而不是運算式。 本文可能包含對 sub 程式的呼叫，但不包含對函數程式的呼叫。  
  
- 在 lambda 運算式中，所有參數都必須有指定的資料類型，或必須推斷所有參數。  
  
- `ParamArray`Lambda 運算式中不允許選擇性和參數。  
  
- Lambda 運算式中不允許泛型參數。  
  
## <a name="example"></a>範例  

 以下是將值寫入主控台的 lambda 運算式範例。 此範例會顯示副程式的單行和多行 lambda 運算式語法。 如需更多範例，請參閱 [Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>另請參閱

- [Sub 陳述式](../statements/sub-statement.md)
- [Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [運算子和運算式](../../programming-guide/language-features/operators-and-expressions/index.md)
- [陳述式](../../programming-guide/language-features/statements.md)
- [寬鬆委派轉換](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
