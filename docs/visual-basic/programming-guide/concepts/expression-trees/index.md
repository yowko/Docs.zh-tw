---
title: 運算式樹狀架構 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: ac37dd63041ba0a0a8ee08651fe62334c3c30049
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="expression-trees-visual-basic"></a>運算式樹狀架構 (Visual Basic)
運算式樹狀架構代表類似樹狀目錄之資料結構中的程式碼，其中，每個節點都是一個運算式，例如，方法呼叫或二進位運算 (如 `x < y`)。  
  
 您可以編譯和執行運算式樹狀架構所代表的程式碼。 這會啟用動態修改可執行程式碼、在各種資料庫中執行 LINQ 查詢，以及建立動態查詢。 如需 LINQ 中之運算式樹狀架構的詳細資訊，請參閱[如何︰使用運算式樹狀架構建置動態查詢 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)。  
  
 運算式樹狀架構也用於動態語言執行階段中，以提供動態語言與 .NET Framework 之間的互通性，並讓編譯器寫入器發出運算式樹狀架構，而不是 Microsoft Intermediate Language (MSIL)。 如需 DLR 的詳細資訊，請參閱 [Dynamic Language Runtime 概觀](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)。  
  
 您可以根據匿名 Lambda 運算式讓 C# 或 Visual Basic 編譯器建立運算式樹狀架構，也可以使用 <xref:System.Linq.Expressions> 命名空間以手動建立運算式樹狀架構。  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a>從 Lambda 運算式建立運算式樹狀架構  
 將 Lambda 運算式指派給類型為 <xref:System.Linq.Expressions.Expression%601> 的變數時，編譯器會發出程式碼，以建置代表 Lambda 運算式的運算式樹狀架構。  
  
 Visual Basic 編譯器只能從運算式 Lambda (或單行 Lambda) 產生運算式樹狀架構。 它無法剖析陳述式 Lambda (或多行 Lambda)。 如需 Visual Basic 中之 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 下列程式碼範例示範如何讓 Visual Basic 編譯器建立代表 Lambda 運算式 `Function(num) num < 5` 的運算式樹狀架構。  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a>使用 API 建立運算式樹狀架構  
 若要使用 API 建立運算式樹狀架構，請使用 <xref:System.Linq.Expressions.Expression> 類別。 這個類別包含可建立之特定類型運算式樹狀架構節點的靜態 factory 方法，例如，<xref:System.Linq.Expressions.ParameterExpression> (代表變數或參數) 或 <xref:System.Linq.Expressions.MethodCallExpression> (代表方法呼叫)。 <xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression> 和其他運算式特定類型也定義在 <xref:System.Linq.Expressions> 命名空間中。 這些類型衍生自抽象類型 <xref:System.Linq.Expressions.Expression>。  
  
 下列程式碼範例示範如何使用 API 建立代表 Lambda 運算式 `Function(num) num < 5` 的運算式樹狀架構。  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 在.NET Framework 4 或更新版中，運算式樹狀架構 API 也可用於指派及控制流程運算式，例如迴圈、條件式區塊及 `try-catch` 區塊。 使用 API 建立的運算式樹狀架構，可以比使用 Visual Basic 編譯器從 Lambda 運算式建立的運算式樹狀架構更加複雜。 下列範例示範如何建立可計算數字階乘的運算式樹狀架構。  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.   
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

如需詳細資訊，請參閱[在 Visual Studio 2010 中使用運算式樹狀架構產生動態方法 (英文)](http://go.microsoft.com/fwlink/p/?LinkId=169513)，這也適用於更新版本的 Visual Studio。
  
## <a name="parsing-expression-trees"></a>剖析運算式樹狀架構  
 下列程式碼範例示範如何將代表 Lambda 運算式 `Function(num) num < 5` 的運算式樹狀架構分解成各部組件。  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a>運算式樹狀架構的不變性  
 運算式樹狀架構應該是不變的。 這表示，如果您要修改運算式樹狀架構，則必須複製現有運算式樹狀架構，並取代其中的節點，以建構新的運算式樹狀架構。 您可以使用運算式樹狀架構訪問項來周遊現有運算式樹狀架構。 如需詳細資訊，請參閱[如何︰修改運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)。  
  
## <a name="compiling-expression-trees"></a>編譯運算式樹狀架構  
 <xref:System.Linq.Expressions.Expression%601> 類型提供 <xref:System.Linq.Expressions.Expression%601.Compile%2A> 方法，以將運算式樹狀架構所代表的程式碼編譯為可執行委派。  
  
 下列程式碼範例示範如何編譯運算式樹狀架構，並執行產生的程式碼。  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 如需詳細資訊，請參閱[如何：執行運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq.Expressions>  
 [如何： 執行運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [如何： 修改運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)  
 [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Dynamic Language Runtime 概觀](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)  
 [程式設計概念 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/index.md)
