---
title: "如何︰ 建立 Lambda 運算式 (Visual Basic) |Microsoft 文件"
ms.custom: 
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
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: 27
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
ms.openlocfilehash: 5e105e87b1e63218f2c3c2204350257c139b5837
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>如何：建立 Lambda 運算式 (Visual Basic)
A *lambda 運算式*函式或不含名稱的副程式。 只要委派型別有效，可以使用 lambda 運算式。  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>若要建立的單行 lambda 運算式函式  
  
1.  在委派型別可以用在任何情況下，輸入關鍵字`Function`，如下列範例所示︰  
  
     `Dim add1 =`   `Function`  
  
2.  在括號內，緊接`Function`，類型函式的參數。 請注意，您不指定的名稱之後`Function`。  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  下列參數清單中，輸入單一運算式做為函式的主體。 運算式評估為值是函式所傳回的值。 您不使用`As`子句來指定傳回型別。  
  
     [!code-vb[VbVbalrLambdas #&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     Lambda 運算式可以呼叫傳入整數引數。  
  
     [!code-vb[VbVbalrLambdas #&2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  此外，相同的結果被透過下列的範例︰  
  
     [!code-vb[VbVbalrLambdas #&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>若要建立單行 lambda 運算式副程式  
  
1.  在委派型別可以用在任何情況下，輸入關鍵字`Sub`，如下列範例所示。  
  
     `Dim add1 =`   `Sub`  
  
2.  在括號內，緊接`Sub`，型別副程式的參數。 請注意，您不指定的名稱之後`Sub`。  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  下列參數清單中，輸入單一陳述式做為副程式的主體。  
  
     [!code-vb[VbVbalrLambdas #&17;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     Lambda 運算式可以呼叫傳入的字串引數。  
  
     [!code-vb[VbVbalrLambdas #&18;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>若要建立多行 lambda 運算式函式  
  
1.  在委派型別可以用在任何情況下，輸入關鍵字`Function`，如下列範例所示。  
  
     `Dim add1 =`   `Function`  
  
2.  在括號內，緊接`Function`，類型函式的參數。 請注意，您不指定的名稱之後`Function`。  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  請按 ENTER 鍵。 `End Function`陳述式會自動加入。  
  
4.  在函式的主體內，新增下列程式碼來建立運算式，並傳回值。 您不使用`As`子句來指定傳回型別。  
  
     [!code-vb[VbVbalrLambdas #&19;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     Lambda 運算式可以呼叫傳入整數引數。  
  
     [!code-vb[VbVbalrLambdas #&20;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>若要建立多行 lambda 運算式副程式  
  
1.  在委派型別可以用在任何情況下，輸入關鍵字`Sub`，如下列範例所示︰  
  
     `Dim add1 =`   `Sub`  
  
2.  在括號內，緊接`Sub`，型別副程式的參數。 請注意，您不指定的名稱之後`Sub`。  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  請按 ENTER 鍵。 `End Sub`陳述式會自動加入。  
  
4.  在函式主體，加入下列程式碼來叫用副程式時執行。  
  
     [!code-vb[VbVbalrLambdas #&21;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     Lambda 運算式可以呼叫傳入的字串引數。  
  
     [!code-vb[VbVbalrLambdas #&22;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a>範例  
 定義可以做為參數的型別引數傳入的函式的 lambda 運算式的常見用法是`Delegate`。 在下列範例中，<xref:System.Diagnostics.Process.GetProcesses%2A>方法會傳回本機電腦上執行的處理程序的陣列。</xref:System.Diagnostics.Process.GetProcesses%2A> <xref:System.Linq.Enumerable.Where%2A>方法從<xref:System.Linq.Enumerable>類別需要`Boolean`委派做為引數。</xref:System.Linq.Enumerable> </xref:System.Linq.Enumerable.Where%2A> 在範例中的 lambda 運算式用來達成目的。 它會傳回`True`每個處理序只有一個執行緒，且那些中所選`filteredList`。  
  
 [!code-vb[VbVbalrLambdas #&10;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 上述範例相當於下列程式碼，以撰寫[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]語法︰  
  
 [!code-vb[VbVbalrLambdas #&11;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 [Lambda 運算式](./lambda-expressions.md)   
 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [如何︰ 將傳遞至另一個程序，在 Visual Basic 中的程序](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Delegate 陳述式](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
