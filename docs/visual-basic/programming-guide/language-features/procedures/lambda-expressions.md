---
title: "Lambda Expressions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.LambdaFunction"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "functions [Visual Basic], lambda expressions"
  - "lambda expressions [Visual Basic]"
  - "expressions [Visual Basic], lambda"
  - "inline functions [Visual Basic]"
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: 52
caps.handback.revision: 52
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lambda Expressions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

「*Lambda 運算式*」\(Lambda expression\) 是不具名稱的函式或副程式，當委派有效時可以使用此運算式。  Lambda 運算式可以是函式或副程式，也可以是單行或多行。  您可以從目前範圍傳遞值到 Lambda 運算式。  
  
> [!NOTE]
>  `RemoveHandler` 陳述式 \(Statement\) 是例外狀況 \(Exception\)。  您無法針對 `RemoveHandler` 的委派參數傳遞 Lambda 運算式。  
  
 您可以使用 `Function` 或 `Sub` 關鍵字建立 Lambda 運算式，如同建立標準函式或副程式一般。  但是，Lambda 運算式是包含在陳述式中。  
  
 下列範例是會遞增其引數並傳回值的 Lambda 運算式。  下列範例同時顯示函式的單行和多行 Lambda 運算式語法。  
  
 [!CODE [VbVbalrLambdas#14](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrLambdas#14)]  
  
 下列範例是一個 Lambda 運算式，可以將值寫入至主控台。  下列範例同時顯示副程式的單行和多行 Lambda 運算式語法。  
  
 [!CODE [VbVbalrLambdas#15](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrLambdas#15)]  
  
 請注意，上述範例中 Lambda 運算式已經指派給變數名稱。  因此每當參考該變數時，便會呼叫 Lambda 運算式。  您還可以同時宣告和叫用 Lambda 運算式，如下列範例所示。  
  
 [!CODE [VbVbalrLambdas#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrLambdas#3)]  
  
 Lambda 運算式可以傳回做為函式呼叫 \(Function Call\) 的值 \(請見本主題稍後[內容](#context)章節中的範例\)，或傳遞做為使用委派型別之參數的引數，如下範例所示。  
  
 [!CODE [VbVbalrLambdas#8](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrLambdas#8)]  
  
## Lambda 運算式語法  
 Lambda 運算式的語法和標準函式或副程式語法類似。  其差異如下：  
  
-   Lambda 運算式沒有名稱。  
  
-   Lambda 運算式不能有修飾詞 \(Modifier\)，例如 `Overloads` 或 `Overrides`。  
  
-   單行 Lambda 函式不會使用 `As` 子句來指定傳回型別。  而是從 Lambda 運算式評估之主體的值來推斷型別。  例如，如果 Lambda 運算式的主體是 `cust.City = "London"`，其傳回型別為 `Boolean`。  
  
-   在多行 Lambda 函式中，您可以使用 `As` 子句來指定傳回型別，也可以省略 `As` 子句，使傳回型別成為推斷型別。  省略多行 Lambda 函式的 `As` 子句時，傳回型別將推斷為多行 Lambda 函式中所有 `Return` 陳述式的主型別。  *主控項的型別*時，所有其他型別可以擴展為唯一的型別。  如果無法決定此唯一型別，主型別將成為陣列中所有其他型別可以縮小至的唯一型別。  如果無法決定所有這些型別，則主型別為 `Object`。  在這種情況下，如果 `Option Strict` 設為 `On`，就會發生編譯器錯誤。  
  
     比方說，如果運算式提供給`Return`陳述式都包含型別的值`Integer`， `Long`，以及`Double`，產生的陣列是類型`Double`。  `Integer` 和 `Long` 都會擴展為 `Double` 而且僅限為 `Double`。  因此，`Double` 是主型別。  如需詳細資訊，請參閱[Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
-   單行函式的主體必須是可以傳回值的運算式，而不是陳述式。  單行函式沒有 `Return` 陳述式。  單行函式傳回的值就是函式主體中運算式的值。  
  
-   單行副程式的主體必須是單行陳述式。  
  
-   單行函式和副程式不包含 `End Function` 或 `End Sub` 陳述式。  
  
-   您可以使用 `As` 關鍵字來指定 Lambda 運算式參數的資料型別，也可以推斷參數的資料型別。  所有參數都必須具有指定的資料型別，不然所有參數就都必須經過推斷。  
  
-   不允許 `Optional` 和 `Paramarray` 參數。  
  
-   不允許使用泛型參數。  
  
## 非同步 Lambda  
 您可以輕鬆地建立 lambda 運算式，並藉由將非同步處理的陳述式[Async](../../../../visual-basic/language-reference/modifiers/async.md)和[Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md)關鍵字。  例如，下列範例中，Windows Form 包含此事件處理常式會呼叫並執行的非同步方法，正等著你`ExampleMethodAsync`。  
  
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
  
 您可以新增相同的事件處理常式，藉由在非同步 lambda [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md)。  若要新增這個處理常式，請將`Async`之前 lambda 的參數清單，如下列範例所示的修飾詞。  
  
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
  
 如需有關如何建立和使用非同步方法的詳細資訊，請參閱[使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。  
  
##  <a name="context"></a> 內容  
 Lambda 運算式是和定義本身所在的範圍共用內容。  它的存取權限與包含範圍中撰寫的任何程式碼相同。  這包括對包含範圍中成員變數、函式和子函式、`Me` 及參數和區域變數的存取權。  
  
 對於包含範圍中的區域變數和參數的存取權期，可以延伸超過該範圍的存留期 \(Lifetime\)。  只要委派 \(Delegate\) 參考無法進行記憶體回收的 Lambda 運算式，就會保留對於原始環境中變數的存取權。  在下列範例中，變數 `target` 是 `makeTheGame` 的本機變數，而後者是 Lambda 運算式 `playTheGame` 在其中定義的方法。  請注意，在 `Main` 中指派給 `takeAGuess` 的傳回 Lambda 運算式，仍然可以存取本機變數 `target`。  
  
 [!CODE [VbVbalrLambdas#12](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrLambdas#12)]  
  
 下列範例示範巢狀 Lambda 運算式的廣泛存取權限。  當傳回的 Lambda 運算式是從 `Main` 執行為 `aDel` 時，它會存取下列項目：  
  
-   在其中進行定義的類別 \(Class\) 欄位：`aField`  
  
-   在其中進行定義的類別屬性：`aProp`  
  
-   在其中進行定義之方法 `functionWithNestedLambda` 的參數：`level1`  
  
-   `functionWithNestedLambda` 的本機變數：`localVar`  
  
-   形成巢狀之 Lambda 運算式的參數：`level2`  
  
 [!CODE [VbVbalrLambdas#9](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrLambdas#9)]  
  
## 轉換為委派型別  
 Lambda 運算式可以隱含地轉換為相容的委派型別。  如需一般相容性需求的詳細資訊，請參閱[Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  例如，下列程式碼範例顯示的 Lambda 運算式可隱含轉換為 `Func(Of Integer, Boolean)` 或相符的委派簽章。  
  
 [!CODE [VbVbalrLambdas#16](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrLambdas#16)]  
  
 下列程式碼範例顯示的 Lambda 運算式可隱含轉換為 `Sub(Of Double, String, Double)` 或相符的委派簽章。  
  
 [!CODE [VbVbalrLambdas#23](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrLambdas#23)]  
  
 當您將 Lambda 運算式指派為委派或者當做引數傳遞至程序時，可以指定參數名稱但略過其資料型別，以便從委派採用型別。  
  
## 範例  
  
-   下列範例定義 Lambda 運算式，在可為 Null 的引數具有指派值時傳回 `True`，而其值為 `Nothing` 時傳回 `False`。  
  
     [!CODE [VbVbalrLambdas#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrLambdas#4)]  
  
-   下列範例定義 Lambda 運算式，會傳回陣列中最後一個元素的索引。  
  
     [!CODE [VbVbalrLambdas#5](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrLambdas#5)]  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [How to: Pass Procedures to Another Procedure in Visual Basic](../Topic/How%20to:%20Pass%20Procedures%20to%20Another%20Procedure%20in%20Visual%20Basic.md)   
 [How to: Create a Lambda Expression](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-lambda-expression.md)   
 [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)