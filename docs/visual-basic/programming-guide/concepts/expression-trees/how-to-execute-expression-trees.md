---
title: "如何︰ 執行運算式樹狀架構 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4cc2c9890c1f5efbc4036d94eef1adb05094ae40
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="c1f39-102">如何︰ 執行運算式樹狀架構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1f39-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="c1f39-103">本主題說明如何執行運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="c1f39-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="c1f39-104">執行運算式樹狀架構可能會傳回值，或只是執行動作，例如呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="c1f39-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="c1f39-105">您可以執行 lambda 運算式表示運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="c1f39-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="c1f39-106">運算式樹狀結構，代表 lambda 運算式的型別<xref:System.Linq.Expressions.LambdaExpression>或<xref:System.Linq.Expressions.Expression%601>。</xref:System.Linq.Expressions.Expression%601> </xref:System.Linq.Expressions.LambdaExpression></span><span class="sxs-lookup"><span data-stu-id="c1f39-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="c1f39-107">若要執行這些運算式樹狀架構，呼叫<xref:System.Linq.Expressions.LambdaExpression.Compile%2A>方法以建立可執行的委派，然後叫用委派。</xref:System.Linq.Expressions.LambdaExpression.Compile%2A></span><span class="sxs-lookup"><span data-stu-id="c1f39-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1f39-108">如果不知道委派型別，也就是 lambda 運算式為類型<xref:System.Linq.Expressions.LambdaExpression>而非<xref:System.Linq.Expressions.Expression%601>，您必須呼叫<xref:System.Delegate.DynamicInvoke%2A>方法而不是直接叫用該委派。</xref:System.Delegate.DynamicInvoke%2A> </xref:System.Linq.Expressions.Expression%601> </xref:System.Linq.Expressions.LambdaExpression></span><span class="sxs-lookup"><span data-stu-id="c1f39-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="c1f39-109">如果運算式樹狀架構不代表 lambda 運算式，您可以建立新的 lambda 運算式做為其主體中，具有原始的運算式樹狀架構，藉由呼叫<xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>方法。</xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29></span><span class="sxs-lookup"><span data-stu-id="c1f39-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="c1f39-110">然後，您可以執行 lambda 運算式，如本節先前所述。</span><span class="sxs-lookup"><span data-stu-id="c1f39-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1f39-111">範例</span><span class="sxs-lookup"><span data-stu-id="c1f39-111">Example</span></span>  
 <span data-ttu-id="c1f39-112">下列程式碼範例示範如何執行運算式樹狀架構代表某個數字乘冪提高藉由建立 lambda 運算式，並執行它。</span><span class="sxs-lookup"><span data-stu-id="c1f39-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="c1f39-113">結果，代表數字乘冪，會顯示。</span><span class="sxs-lookup"><span data-stu-id="c1f39-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1f39-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c1f39-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="c1f39-115">如果沒有參考，加入專案參考 system.core.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="c1f39-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="c1f39-116">包括 System.Linq.Expressions 命名空間。</span><span class="sxs-lookup"><span data-stu-id="c1f39-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1f39-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1f39-117">See Also</span></span>  
 <span data-ttu-id="c1f39-118">[運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="c1f39-118">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="c1f39-119"> [如何︰ 修改運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)</span><span class="sxs-lookup"><span data-stu-id="c1f39-119"> [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)</span></span>
