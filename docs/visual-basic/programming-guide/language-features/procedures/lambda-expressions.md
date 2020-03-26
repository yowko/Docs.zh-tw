---
title: Lambda 運算式
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 1827eb5630ed217527de25fc9d9c2bb8994b9aff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249665"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda 運算式 (Visual Basic)

*lambda 運算式*是一個函數或副程式，沒有名稱，可以在委託有效的地方使用。 Lambda 運算式可以是函數或副程式，可以是單行運算式或多行運算式。 可以將值從當前作用域傳遞到 lambda 運算式。

> [!NOTE]
> 該`RemoveHandler`語句是一個例外。 不能為 的委託參數傳遞 lambda 運算式`RemoveHandler`。

使用`Function`or`Sub`關鍵字創建 lambda 運算式，就像創建標準函數或副程式一樣。 但是，lambda 運算式包含在語句中。

下面的示例是 lambda 運算式，該運算式遞增其參數並傳回值。 該示例顯示了函數的單行和多行 lambda 運算式語法。

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

下面的示例是 lambda 運算式，該運算式將值寫入主控台。 該示例顯示了副程式的單行和多行 lambda 運算式語法。

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

請注意，在前面的示例中，lambda 運算式被分配給一個變數名稱。 每當引用變數時，都會調用 lambda 運算式。 您還可以同時聲明和調用 lambda 運算式，如以下示例所示。

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

lambda 運算式可以作為函式呼叫的值返回（如本主題後面的["上下文](#context)"部分中的示例中所示），也可以作為參數傳遞給採用委託類型的參數，如以下示例所示。

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Lambda 運算式語法

lambda 運算式的語法類似于標準函數或副程式的語法。 差異如下：

- lambda 運算式沒有名稱。

- Lambda 運算式不能具有修飾符，如`Overloads`或`Overrides`。

- 單行 lambda 函數不使用子句`As`來指定返回類型。 相反，類型是從 lambda 運算式的正文計算到的值推斷的。 例如，如果 lambda 運算式的正文為`cust.City = "London"`，則其返回類型`Boolean`為 。

- 在多行 lambda 函數中，可以使用`As`子句指定返回類型，或者省略`As`子句，以便推斷返回類型。 當多`As`行 lambda 函數省略子句時，返回類型被推斷為多行 lambda 函數中所有`Return`語句中的主要類型。 *主導類型*是所有其他類型都可以擴展到的唯一類型。 如果無法確定此唯一類型，則主導類型是陣列中所有其他類型都可以縮小到的唯一類型。 如果這些類型皆無法決定，則主類型為 `Object`。 在這種情況下，如果`Option Strict`設置為`On`，則會發生編譯器錯誤。

     例如`Return`，如果提供給語句的運算式包含 類型`Integer`的值 ，`Long`和`Double`， 生成的陣列的類型`Double`為 。 兩`Integer`者`Long`加寬`Double`至和`Double`僅。 因此， `Double` 是主類型。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。

- 單行函數的正文必須是傳回值的運算式，而不是語句。 單行函數`Return`沒有語句。 單行函數返回的值是函數正文中運算式的值。

- 單行副程式的正文必須是單行語句。

- 單行函數和副程式不包括 或`End Function``End Sub`語句。

- 可以使用`As`關鍵字指定 lambda 運算式參數的資料類型，也可以推斷參數的資料類型。 所有參數都必須具有指定的資料類型，或者必須推斷所有參數。

- `Optional`不允許`Paramarray`和參數。

- 不允許使用通用參數。

## <a name="async-lambdas"></a>非同步 Lambda

通過使用[Async](../../../../visual-basic/language-reference/modifiers/async.md)和[Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md)關鍵字，可以輕鬆地創建包含非同步處理的 lambda 運算式和語句。 例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。

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

您可以通過在[AddHandler 語句](../../../../visual-basic/language-reference/statements/addhandler-statement.md)中使用非同步 lambda 來添加相同的事件處理常式。 若要加入這個處理常式，請將 `Async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示。

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

有關如何創建和使用非同步方法的詳細資訊，請參閱[使用非同步和 Await 進行非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。

## <a name="context"></a>Context

lambda 運算式與其定義上下文的範圍共用上下文。 它具有與在包含作用域中編寫的任何代碼相同的存取權限。 這包括訪問包含作用域中的成員變數、函數和子以及`Me`參數和區域變數。

對包含作用域中的區域變數和參數的訪問可以超出該作用域的存留期。 只要引用 lambda 運算式的委託不能用於垃圾回收，則將保留對原始環境中變數的訪問。 在下面的示例中，變數`target`是 局部的`makeTheGame`， 在 其中定義 lambda 運算式`playTheGame`的方法。 請注意，分配給`takeAGuess``Main`的返回 lambda 運算式仍有權訪問區域變數`target`。

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

下面的示例演示嵌套 lambda 運算式的廣泛存取權限。 當返回的 lambda 運算式從`Main``aDel`執行 時，它將訪問以下元素：

- 在其中定義它的類的欄位：`aField`

- 定義它的類的屬性：`aProp`

- 方法`functionWithNestedLambda`的參數，`level1`

- 的`functionWithNestedLambda`區域變數：`localVar`

- 嵌套在 lambda 運算式中的參數：`level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>轉換為委託類型

lambda 運算式可以隱式轉換為相容的委託類型。 有關相容性的一般要求的資訊，請參閱[放寬委託轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。 例如，以下代碼示例顯示隱式轉換為`Func(Of Integer, Boolean)`或匹配委託簽名的 lambda 運算式。

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

下面的代碼示例顯示隱式轉換為`Sub(Of Double, String, Double)`或匹配委託簽名的 lambda 運算式。

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

將 lambda 運算式分配給委託或將它們作為參數傳遞給過程時，可以指定參數名稱，但省略其資料類型，允許從委託獲取類型。

## <a name="examples"></a>範例

- 下面的示例定義 lambda 運算式，如果空`True`數值型別參數具有賦值，並且`False`其值為`Nothing`，則返回該運算式。

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- 下面的示例定義一個 lambda 運算式，該運算式返回陣列中最後一個元素的索引。

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [空數值型別](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [如何：在 Visual Basic 中將程序傳遞至其他程序](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [如何：建立 Lambda 運算式](./how-to-create-a-lambda-expression.md)
- [寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
