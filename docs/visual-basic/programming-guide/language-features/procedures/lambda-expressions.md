---
title: "Lambda 運算式 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: "52"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69ac88d295420277e99058d0f80a5ae1c2ce2e39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-visual-basic"></a>Lambda 運算式 (Visual Basic)
A *lambda 運算式*函式或副程式沒有可用於委派是有效的名稱。 Lambda 運算式可以是函式或副程式，而且可以是單行或多行。 您可以在 lambda 運算式，從目前的範圍傳遞值。  
  
> [!NOTE]
>  `RemoveHandler`陳述式是例外狀況。 您無法將傳遞的委派參數的 lambda 運算式中`RemoveHandler`。  
  
 使用建立 lambda 運算式`Function`或`Sub`關鍵字，就像建立標準函式或副程式。 不過，lambda 運算式會包含陳述式中。  
  
 下列範例是遞增其引數和傳回值的 lambda 運算式。 函式的兩個多行的單行 lambda 運算式語法範例。  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 下列範例會將值寫入主控台的 lambda 運算式。 此範例顯示副程式的這兩個多行的單行 lambda 運算式的語法。  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 請注意，上述範例中的 lambda 運算式指派給變數的名稱。 每當您參考的變數，您就會叫用 lambda 運算式。 您也可以宣告和叫用相同的時間，lambda 運算式，如下列範例所示。  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 Lambda 運算式可以傳回做為函式呼叫的值 (如下所示的範例[內容](#context)本主題稍後的章節)，或傳遞做為引數至參數會是委派類型，如下列所示範例。  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a>Lambda 運算式語法  
 Lambda 運算式的語法類似於標準函式或副程式。 差異如下所示：  
  
-   Lambda 運算式沒有名稱。  
  
-   Lambda 運算式不能有修飾詞，例如`Overloads`或`Overrides`。  
  
-   單行 lambda 函式就不會使用`As`子句來指定傳回型別。 相反地，從 lambda 運算式的主體會評估為值推斷的類型。 例如，如果 lambda 運算式的主體是`cust.City = "London"`，其傳回類型是`Boolean`。  
  
-   在多行 lambda 函式，您可以指定傳回型別使用`As`子句，或省略`As`子句，讓推斷傳回類型。 當`As`子句省略多行 lambda 函式，就會推斷傳回型別是從所有主控項的類型`Return`多行 lambda 函式中的陳述式。 *主類型*是所有其他類型可以擴展成的唯一類型。 無法決定此唯一類型，如果主類型是陣列中的其他類型皆可縮小到的唯一類型。 如果這些類型皆無法決定，則主類型為 `Object`。 在此情況下，如果`Option Strict`設`On`，就會發生編譯器錯誤。  
  
     例如，如果運算式提供給`Return`陳述式包含類型的值`Integer`， `Long`，和`Double`，產生的陣列會屬於類型`Double`。 同時`Integer`和`Long`擴展為`Double`僅限和`Double`。 因此， `Double` 是主類型。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
-   單行函式的主體必須傳回值，而不是陳述式的運算式。 沒有任何`Return`單行函式的陳述式。 函式主體中的運算式的值為單行函式所傳回的值。  
  
-   單行副程式的主體必須是單行陳述式。  
  
-   不包含單行函式和副程式`End Function`或`End Sub`陳述式。  
  
-   您可以使用指定的 lambda 運算式參數的資料型別`As`推斷關鍵字或參數的資料類型。 必須推斷資料型別或所有必須指定所有參數。  
  
-   `Optional`和`Paramarray`參數不允許使用。  
  
-   不允許泛型參數。  
  
## <a name="async-lambdas"></a>非同步 Lambda  
 您可以輕鬆地建立 lambda 運算式和陳述式結合非同步處理的使用[非同步](../../../../visual-basic/language-reference/modifiers/async.md)和[Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md)關鍵字。 例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。  
  
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
  
 您可以使用在非同步 lambda 加入相同的事件處理常式[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)。 若要加入這個處理常式，請將 `Async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示。  
  
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
  
 如需如何建立和使用非同步方法的詳細資訊，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。  
  
##  <a name="context"></a>內容  
 Lambda 運算式內定義的範圍與共用其內容。 其包含的範圍中撰寫任何程式碼的相同存取權限。 這包括存取成員變數、 函式和子函數， `Me`，在包含的範圍中的區域變數和參數。  
  
 存取區域變數和參數中包含的範圍可以擴充到超出該範圍的存留期間。 只要參考 lambda 運算式的委派不適用於記憶體回收，會保留原始的環境變數的存取權。 在下列範例中，變數`target`本機`makeTheGame`，此方法用於 lambda 運算式`playTheGame`定義。 請注意，傳回的 lambda 運算式中，指派給`takeAGuess`中`Main`，仍然可以存取區域變數`target`。  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 下列範例會示範各種不同的存取權限的巢狀的 lambda 運算式。 從執行傳回的 lambda 運算式時`Main`為`aDel`，它會存取這些項目：  
  
-   在定義類別的欄位：`aField`  
  
-   在定義類別的屬性：`aProp`  
  
-   方法的參數`functionWithNestedLambda`，它會定義：`level1`  
  
-   本機變數`functionWithNestedLambda`:`localVar`  
  
-   在它巢狀 lambda 運算式的參數：`level2`  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a>轉換成委派類型  
 Lambda 運算式可以隱含地轉換成相容的委派類型。 如需相容性的一般需求資訊，請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。 例如，下列程式碼範例示範隱含地轉換成的 lambda 運算式`Func(Of Integer, Boolean)`或相符的委派簽章。  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 下列程式碼範例示範 lambda 運算式的隱含地轉換成`Sub(Of Double, String, Double)`或相符的委派簽章。  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 當您將 lambda 運算式指派給委派，或將其做為引數傳遞至程序時，您可以指定參數名稱，但省略其資料型別，以便從委派的類型。  
  
## <a name="examples"></a>範例  
  
-   下列範例會定義傳回的 lambda 運算式`True`可為 null 的引數必須具有指派的值，如果和`False`如果其值為`Nothing`。  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   下列範例會定義傳回最後一個項目的索引陣列中的 lambda 運算式。  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [可為 Null 的值類型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [如何：在 Visual Basic 中將程序傳遞至其他程序](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [如何：建立 Lambda 運算式](./how-to-create-a-lambda-expression.md)  
 [寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
