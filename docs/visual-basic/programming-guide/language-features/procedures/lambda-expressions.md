---
title: Lambda 運算式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: e688beac18e782367bf39ddec8339df2b2735225
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928908"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda 運算式 (Visual Basic)
*Lambda 運算式*是一個不含名稱的函式或副程式, 可以在委派有效的任何地方使用。 Lambda 運算式可以是函數或副程式, 而且可以是單行或多行。 您可以將值從目前範圍傳遞至 lambda 運算式。  
  
> [!NOTE]
> `RemoveHandler`語句是例外狀況。 您無法在中傳遞的 lambda 運算式做為的委派`RemoveHandler`參數。  
  
 您可以使用`Function`或`Sub`關鍵字來建立 lambda 運算式, 就如同建立標準函數或副程式一樣。 不過, lambda 運算式會包含在語句中。  
  
 下列範例是 lambda 運算式, 它會遞增其引數並傳回值。 此範例會顯示函數的單行和多行 lambda 運算式語法。  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
 下列範例是將值寫入主控台的 lambda 運算式。 此範例會顯示副程式的單行和多行 lambda 運算式語法。  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
 請注意, 在先前的範例中, lambda 運算式會指派給變數名稱。 每當您參考變數時, 就會叫用 lambda 運算式。 您也可以同時宣告和叫用 lambda 運算式, 如下列範例所示。  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
 Lambda 運算式可以當做函式呼叫的值傳回 (如本主題稍後的[內容](#context)章節中的範例所示), 或當做引數傳遞給採用委派類型的參數, 如下列範例所示。  
  
 [!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]  
  
## <a name="lambda-expression-syntax"></a>Lambda 運算式語法  
 Lambda 運算式的語法類似于標準函式或副程式。 差異如下:  
  
- Lambda 運算式沒有名稱。  
  
- Lambda 運算式不能有修飾詞, `Overloads`例如`Overrides`或。  
  
- 單行 lambda 函數不會使用`As`子句來指定傳回類型。 相反地, 型別是從 lambda 運算式主體評估為的值推斷而來。 例如, 如果 lambda 運算式的主體是`cust.City = "London"`, 其傳回型別會是。 `Boolean`  
  
- 在多行 lambda 函式中, 您可以使用`As`子句來指定傳回類型, 或`As`省略子句, 以推斷傳回類型。 當多行 lambda 函數省略`Return` 子句時,會將傳回型別推斷為多行lambda函式中所有語句的主要型別。`As` *主要類型*是所有其他類型都可以擴展的唯一類型。 如果無法判斷此唯一類型, 則主要類型是陣列中所有其他類型都可以縮小為的唯一類型。 如果這些類型皆無法決定，則主類型為 `Object`。 在此情況下, `Option Strict`如果設定為`On`, 則會發生編譯器錯誤。  
  
     例如`Return` , 如果提供給語句的運算式包含型`Integer`別、 `Long`和`Double`的值, 則產生的陣列會是型`Double`別。 和只會擴大`Double`為和。 `Double` `Long` `Integer` 因此， `Double` 是主類型。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
- 單行函數的主體必須是傳回值的運算式, 而不是語句。 沒有單行函式的語句。`Return` 單行函式所傳回的值是函數主體中的運算式值。  
  
- 單行副程式的主體必須是單行語句。  
  
- 單行函數和副程式不包含`End Function`或`End Sub`語句。  
  
- 您可以使用`As`關鍵字來指定 lambda 運算式參數的資料類型, 或可以推斷參數的資料類型。 所有參數都必須具有指定的資料類型, 否則必須推斷全部。  
  
- `Optional`不`Paramarray`允許使用和參數。  
  
- 不允許泛型參數。  
  
## <a name="async-lambdas"></a>非同步 Lambda  
 您可以使用[Async](../../../../visual-basic/language-reference/modifiers/async.md)和[Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md)關鍵字, 輕鬆建立結合非同步處理的 lambda 運算式和語句。 例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 您可以在[AddHandler 語句](../../../../visual-basic/language-reference/statements/addhandler-statement.md)中使用非同步 lambda 來加入相同的事件處理常式。 若要加入這個處理常式，請將 `Async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示。  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 如需如何建立和使用非同步方法的詳細資訊, 請參閱[使用 async 和 Await 進行非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。  
  
## <a name="context"></a>內容  
 Lambda 運算式會與其定義所在的範圍共用其內容。 其存取權限與在包含範圍中撰寫的任何程式碼相同。 這包括存取成員變數、函式和`Me`子函式, 以及包含範圍內的參數和區域變數。  
  
 存取包含範圍中的本機變數和參數, 可以延伸超出該範圍的存留期。 只要參考 lambda 運算式的委派無法用於垃圾收集, 就會保留原始環境中變數的存取權。 在下列範例中, 變數`target`是的`makeTheGame`區域, 也就是定義 lambda 運算式`playTheGame`的方法。 請注意, 指派`takeAGuess`給中`Main`的傳回 lambda 運算式仍然具有區域變數的`target`存取權。  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 下列範例示範嵌套 lambda 運算式的範圍存取權限。 `Main` 從`aDel`執行傳回的 lambda 運算式時, 它會存取下列元素:  
  
- 其定義所在類別的欄位:`aField`  
  
- 其定義所在之類別的屬性:`aProp`  
  
- 方法`functionWithNestedLambda`的參數, 其定義如下:`level1`  
  
- 的`functionWithNestedLambda`本機變數:`localVar`  
  
- Lambda 運算式的參數, 其會在其中加以嵌套:`level2`  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a>轉換成委派類型  
 Lambda 運算式可以隱含地轉換成相容的委派類型。 如需相容性一般需求的相關資訊, 請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。 例如, 下列程式碼範例顯示隱含轉換成`Func(Of Integer, Boolean)`或相符委派簽章的 lambda 運算式。  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 下列程式碼範例顯示隱含轉換成`Sub(Of Double, String, Double)`或相符之委派簽章的 lambda 運算式。  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 當您將 lambda 運算式指派給委派, 或將它們當做引數傳遞給程式時, 您可以指定參數名稱但省略其資料類型, 讓型別可以從委派取得。  
  
## <a name="examples"></a>範例  
  
- 下列範例會定義 lambda 運算式, `True`如果可為 null 的引數具有指派的值, 且`False`其值為`Nothing`, 則會傳回。  
  
     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]  
  
- 下列範例會定義 lambda 運算式, 以傳回陣列中最後一個元素的索引。  
  
     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [可為 Null 的值類型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [如何：將程式傳遞至 Visual Basic 中的另一個程式](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [如何：建立 Lambda 運算式](./how-to-create-a-lambda-expression.md)
- [寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
