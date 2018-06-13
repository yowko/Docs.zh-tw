---
title: Sub 運算式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 602212e664fa3362742fb1ba0dc033610272d3af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603531"
---
# <a name="sub-expression-visual-basic"></a>Sub 運算式 (Visual Basic)
宣告的參數和副程式 lambda 運算式定義的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`parameterlist`|選擇性。 代表程序參數的本機變數名稱的清單。 括號必須要有即使清單是空的。 如需詳細資訊，請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`statement`|必要。 單一陳述式。|  
|`statements`|必要。 陳述式的清單。|  
  
## <a name="remarks"></a>備註  
 A *lambda 運算式*沒有名稱的副程式，並執行一或多個陳述式。 您可以使用 lambda 運算式，任何位置，您可以使用委派類型，除了做為引數`RemoveHandler`。 如需委派和 lambda 運算式與委派的使用詳細資訊，請參閱[委派陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)和[寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## <a name="lambda-expression-syntax"></a>Lambda 運算式語法  
 Lambda 運算式的語法類似於標準的副程式。 差異如下所示：  
  
-   Lambda 運算式沒有名稱。  
  
-   Lambda 運算式不能有修飾詞，例如`Overloads`或`Overrides`。  
  
-   單行 lambda 運算式的主體必須是陳述式，而不是運算式。 主體可以包含子程序呼叫，但不函式程序的呼叫。  
  
-   在 lambda 運算式中，所有參數必須都指定必須推斷資料型別或所有參數。  
  
-   選擇性和`ParamArray`參數不允許在 lambda 運算式中。  
  
-   Lambda 運算式中不允許泛型參數。  
  
## <a name="example"></a>範例  
 以下是將值寫入主控台的 lambda 運算式的範例。 此範例顯示這兩個單行或多行 lambda 運算式語法副程式。 如需其他範例，請參閱[Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)  
 [寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
