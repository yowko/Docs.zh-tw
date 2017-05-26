---
title: "Lambda 運算式 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.LambdaFunction
dev_langs:
- VB
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: 52
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e50593e76afecfe8807c3cb5bac479245d2feaef
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="lambda-expressions-visual-basic"></a>Lambda 運算式 (Visual Basic)
A *lambda 運算式*函式或副程式沒有就可以使用委派是有效的名稱。 Lambda 運算式可以是函式或副程式，而且可以是單行或多行。 Lambda 運算式，您可以從目前的範圍傳遞值。  
  
> [!NOTE]
>  `RemoveHandler`陳述式是例外狀況。 您無法傳遞的委派參數的 lambda 運算式中`RemoveHandler`。  
  
 使用建立 lambda 運算式`Function`或`Sub`關鍵字，就像建立標準函式或副程式。 不過，lambda 運算式會包含陳述式中。  
  
 下列範例是遞增其引數和傳回值的 lambda 運算式。 函式的兩個單行或多行 lambda 運算式語法範例。  
  
 [!code-vb[VbVbalrLambdas #&14;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 下列範例會將值寫入主控台的 lambda 運算式。 範例會示範這兩個單行或多行 lambda 運算式語法的副程式。  
  
 [!code-vb[VbVbalrLambdas #&15;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 請注意，上述範例中 lambda 運算式指派給變數的名稱。 每當您參考變數，您就會叫用 lambda 運算式。 您也可以宣告和叫用一次，lambda 運算式，如下列範例所示。  
  
 [!code-vb[VbVbalrLambdas #&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 Lambda 運算式可以傳回做為函式呼叫的值 (在此範例所示[內容](#context)本主題稍後的章節)，或在傳遞做為引數至參數採用委派型別，如下列範例所示。  
  
 [!code-vb[VbVbalrLambdas #&8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a>Lambda 運算式語法  
 Lambda 運算式的語法類似於標準函式或副程式。 差異如下︰  
  
-   Lambda 運算式沒有名稱。  
  
-   Lambda 運算式不能有修飾詞，例如`Overloads`或`Overrides`。  
  
-   不使用單行 lambda 函式`As`子句來指定傳回型別。 相反地，從 lambda 運算式的主體會評估為值推斷型別。 例如，如果 lambda 運算式的主體是`cust.City = "London"`，其傳回型別是`Boolean`。  
  
-   在多行 lambda 函式中，您可以指定傳回型別使用`As`子句，或省略`As`子句，以便傳回型別推斷。 當`As`子句省略多行 lambda 函式，傳回的型別推斷為主控項的型別，從所有`Return`多行 lambda 函式中的陳述式。 *優勢型別*是所有其他型別可以擴展成的唯一類型。 如果無法判斷此唯一的型別，主控項的型別是陣列中的所有其他類型可以縮小到唯一的型別。 如果這些類型皆無法決定，則主類型為 `Object`。 在此情況下，如果`Option Strict`設為`On`，就會發生編譯器錯誤。  
  
     例如，如果運算式提供給`Return`陳述式包含型別的值`Integer`， `Long`，和`Double`，產生的陣列是類型的`Double`。 同時`Integer`和`Long`擴展為`Double`只有`Double`。 因此， `Double` 是主類型。 如需詳細資訊，請參閱[擴大和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
-   單行函式的主體必須是傳回值，而不是陳述式的運算式。 有沒有`Return`單行函式的陳述式。 單行函式所傳回的值是函式主體中運算式的值。  
  
-   單行副程式的主體必須是單行陳述式。  
  
-   不包含單行函式和副程式`End Function`或`End Sub`陳述式。  
  
-   您可以使用指定的 lambda 運算式參數的資料型別`As`關鍵字或參數的資料型別來推斷。 必須推斷資料型別或所有必須指定所有參數。  
  
-   `Optional`和`Paramarray`不允許使用參數。  
  
-   不允許泛型參數。  
  
## <a name="async-lambdas"></a>非同步 Lambda  
 您可以輕鬆地建立 lambda 運算式和陳述式使用結合非同步處理[非同步](../../../../visual-basic/language-reference/modifiers/async.md)和[Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md)關鍵字。 例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。  
  
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
  
 您可以使用非同步 lambda 中的新增相同的事件處理常式[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)。 若要加入這個處理常式，請將 `Async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示。  
  
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
 Lambda 運算式共用其內容與在其中定義的範圍。 其包含的範圍中撰寫程式碼的相同存取權限。 這包括存取成員變數、 函式和子函數， `Me`，涵蓋範圍的區域變數和參數。  
  
 存取區域變數和參數中包含的範圍可以擴充到超出該範圍的存留期間。 只要委派來參考 lambda 運算式不適用於記憶體回收，會保留在原始環境變數的存取權。 在下列範例中，變數`target`本機`makeTheGame`，此方法用於 lambda 運算式`playTheGame`定義。 請注意，傳回的 lambda 運算式指派給`takeAGuess`中`Main`，仍然可以存取本機變數`target`。  
  
 [!code-vb[VbVbalrLambdas #&12;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 下列範例將示範各種的巢狀的 lambda 運算式的存取權限。 從執行傳回的 lambda 運算式會`Main`為`aDel`，它會存取這些項目︰  
  
-   在定義類別的欄位︰`aField`  
  
-   在定義類別的屬性︰`aProp`  
  
-   方法的參數`functionWithNestedLambda`，在其中定義︰`level1`  
  
-   區域變數的`functionWithNestedLambda`:`localVar`  
  
-   在它巢狀 lambda 運算式的參數︰`level2`  
  
 [!code-vb[VbVbalrLambdas #&9;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a>轉換為委派型別  
 Lambda 運算式可以隱含地轉換成相容的委派型別。 一般相容性需求的詳細資訊，請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。 例如，下列程式碼範例顯示的 lambda 運算式隱含地轉換成`Func(Of Integer, Boolean)`或相符的委派簽章。  
  
 [!code-vb[VbVbalrLambdas #&16;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 下列程式碼範例示範 lambda 運算式的隱含地轉換成`Sub(Of Double, String, Double)`或相符的委派簽章。  
  
 [!code-vb[VbVbalrLambdas #&23;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 當您將 lambda 運算式指派給委派，或將其做為引數傳遞至程序時，您可以指定參數名稱，但省略其資料型別，以便進行委派的型別。  
  
## <a name="examples"></a>範例  
  
-   下列範例會定義傳回的 lambda 運算式`True`如果指派的值，可為 null 引數和`False`如果其值為`Nothing`。  
  
     [!code-vb[VbVbalrLambdas #&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   下列範例會定義 lambda 運算式以傳回陣列中的最後一個項目的索引。  
  
     [!code-vb[VbVbalrLambdas #&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [可為 null 的實值型別](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [如何︰ 將傳遞至另一個程序，在 Visual Basic 中的程序](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [如何︰ 建立 Lambda 運算式](./how-to-create-a-lambda-expression.md)   
 [寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)

