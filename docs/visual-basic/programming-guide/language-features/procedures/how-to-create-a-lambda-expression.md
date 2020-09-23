---
title: 如何：建立 Lambda 運算式
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: cc2de38f7375848d104edff6f419656d9caa9cb2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071920"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>如何：建立 Lambda 運算式 (Visual Basic)

*Lambda 運算式*是沒有名稱的函數或副程式。 只要委派型別是有效的，就可以使用 lambda 運算式。  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>若要建立單行 lambda 運算式函數  
  
1. 在可以使用委派類型的任何情況下，請輸入關鍵字 `Function` ，如下列範例所示：  
  
     `Dim add1 =`   `Function`  
  
2. 在括弧中，直接 `Function` 輸入函數的參數。 請注意，您不會在之後指定名稱 `Function` 。  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. 在參數清單之後，輸入單一運算式作為函式的主體。 運算式評估為的值是函數所傳回的值。 您不使用 `As` 子句來指定傳回型別。  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     您可以藉由傳入整數引數來呼叫 lambda 運算式。  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. 另外，下列範例也會完成相同的結果：  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>若要建立單行 lambda 運算式副程式  
  
1. 在可以使用委派類型的任何情況下，請輸入關鍵字 `Sub` ，如下列範例所示。  
  
     `Dim add1 =`   `Sub`  
  
2. 在括弧中，直接 `Sub` 輸入副程式的參數。 請注意，您不會在之後指定名稱 `Sub` 。  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. 在參數清單之後，輸入單一語句作為副程式的主體。  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     您可以藉由傳入字串引數來呼叫 lambda 運算式。  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>若要建立多行 lambda 運算式函數  
  
1. 在可以使用委派類型的任何情況下，請輸入關鍵字 `Function` ，如下列範例所示。  
  
     `Dim add1 =`   `Function`  
  
2. 在括弧中，直接 `Function` 輸入函數的參數。 請注意，您不會在之後指定名稱 `Function` 。  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. 按 ENTER 鍵。 `End Function`系統會自動加入語句。  
  
4. 在函式主體中，加入下列程式碼以建立運算式並傳回值。 您不使用 `As` 子句來指定傳回型別。  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     您可以藉由傳入整數引數來呼叫 lambda 運算式。  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>若要建立多行 lambda 運算式副程式  
  
1. 在可以使用委派類型的任何情況下，請輸入關鍵字 `Sub` ，如下列範例所示：  
  
     `Dim add1 =`   `Sub`  
  
2. 在括弧中，直接 `Sub` 輸入副程式的參數。 請注意，您不會在之後指定名稱 `Sub` 。  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. 按 ENTER 鍵。 `End Sub`系統會自動加入語句。  
  
4. 在函式主體中，加入下列程式碼，以在叫用副程式時執行。  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     您可以藉由傳入字串引數來呼叫 lambda 運算式。  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a>範例  

 Lambda 運算式的常見用法是定義一個函式，這個函式可以當做型別為之參數的引數傳遞 `Delegate` 。 在下列範例中，方法會傳回在 <xref:System.Diagnostics.Process.GetProcesses%2A> 本機電腦上執行之進程的陣列。 <xref:System.Linq.Enumerable.Where%2A>類別中的方法 <xref:System.Linq.Enumerable> 需要 `Boolean` 委派做為其引數。 此範例中的 lambda 運算式會用於該用途。 它會 `True` 針對只有一個執行緒的每個進程傳回，而且在中選取這些程式 `filteredList` 。  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 上述範例相當於下列程式碼，這是以語言整合查詢 (LINQ) 語法所撰寫：  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq.Enumerable>
- [Lambda 運算式](./lambda-expressions.md)
- [Function 陳述式](../../../language-reference/statements/function-statement.md)
- [Sub 陳述式](../../../language-reference/statements/sub-statement.md)
- [委派](../delegates/index.md)
- [如何：在 Visual Basic 中將程序傳遞至其他程序](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [Delegate 陳述式](../../../language-reference/statements/delegate-statement.md)
- [Visual Basic 中的 LINQ 簡介](../linq/introduction-to-linq.md)
