---
title: Sub 運算式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 6cdb75f150831ae3857a510d87b58773bdcf13c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609603"
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
|`parameterlist`|選擇性。 代表程序參數的本機變數名稱的清單。 括號必須要有即使清單是空的。 如需詳細資訊，請參閱 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`statement`|必要項。 單一陳述式。|  
|`statements`|必要項。 陳述式的清單。|  
  
## <a name="remarks"></a>備註  
 A *lambda 運算式*是沒有名稱的副程式，並執行一或多個陳述式。 您可以任意處使用 lambda 運算式，您可以使用委派類型，除非做為引數`RemoveHandler`。 如需委派和 lambda 運算式與委派使用的詳細資訊，請參閱[委派陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)並[寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## <a name="lambda-expression-syntax"></a>Lambda 運算式語法  
 Lambda 運算式的語法類似於標準的副程式。 差異如下所示：  
  
- Lambda 運算式沒有名稱。  
  
- Lambda 運算式不能有修飾詞，例如`Overloads`或`Overrides`。  
  
- 單行 lambda 運算式的主體必須是陳述式，而不是運算式。 主體可以包含子程序的呼叫，但不是呼叫的函式程序。  
  
- 在 lambda 運算式中，可能是所有的參數必須指定必須推斷資料類型或所有參數。  
  
- 選擇性和`ParamArray`lambda 運算式中不允許使用參數。  
  
- Lambda 運算式中不允許泛型參數。  
  
## <a name="example"></a>範例  
 以下是將值寫入主控台的 lambda 運算式的範例。 此範例顯示一個副程式的這兩個單行和多行 lambda 運算式的語法。 如需其他範例，請參閱 < [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>另請參閱

- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
- [寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
