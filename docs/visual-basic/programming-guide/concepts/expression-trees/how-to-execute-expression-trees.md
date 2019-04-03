---
title: HOW TO：執行運算式樹狀架構 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: cccb0b301e1da6d82c616d56604ad46dfde83e2a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837492"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="97741-102">HOW TO：執行運算式樹狀架構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97741-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="97741-103">本主題示範如何執行運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="97741-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="97741-104">執行運算式樹狀架構可能會傳回一個值，或者只是執行某個動作，例如呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="97741-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="97741-105">您只能執行代表 Lambda 運算式的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="97741-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="97741-106">代表 Lambda 運算式的運算式樹狀架構為 <xref:System.Linq.Expressions.LambdaExpression> 或 <xref:System.Linq.Expressions.Expression%601> 類型。</span><span class="sxs-lookup"><span data-stu-id="97741-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="97741-107">若要執行這些運算式樹狀架構，請呼叫 <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> 方法建立可執行委派，然後叫用該委派。</span><span class="sxs-lookup"><span data-stu-id="97741-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97741-108">如果不知道委派的類型，也就是 lambda 運算式是類型 <xref:System.Linq.Expressions.LambdaExpression> 而非 <xref:System.Linq.Expressions.Expression%601>，您必須對委派呼叫 <xref:System.Delegate.DynamicInvoke%2A> 方法，而不是直接叫用它。</span><span class="sxs-lookup"><span data-stu-id="97741-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="97741-109">如果運算式樹狀架構不代表 Lambda 運算式，您可以呼叫 <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> 方法，建立新的 Lambda 運算式，以原始的運算式樹狀架構當做其主體。</span><span class="sxs-lookup"><span data-stu-id="97741-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="97741-110">然後，您可以如本節稍早所述來執行此 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="97741-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97741-111">範例</span><span class="sxs-lookup"><span data-stu-id="97741-111">Example</span></span>  
 <span data-ttu-id="97741-112">下列程式碼範例示範如何藉由建立和執行 Lambda 運算式，來執行代表數字自乘至乘冪的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="97741-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="97741-113">顯示的結果會是已自乘至乘冪的數字。</span><span class="sxs-lookup"><span data-stu-id="97741-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="97741-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="97741-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="97741-115">如果 System.Core.dll 的專案參考原本未參考，請新增這項參考。</span><span class="sxs-lookup"><span data-stu-id="97741-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="97741-116">加入 System.Linq.Expressions 命名空間。</span><span class="sxs-lookup"><span data-stu-id="97741-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97741-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97741-117">See also</span></span>

- [<span data-ttu-id="97741-118">運算式樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97741-118">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="97741-119">如何：修改運算式樹狀架構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97741-119">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
