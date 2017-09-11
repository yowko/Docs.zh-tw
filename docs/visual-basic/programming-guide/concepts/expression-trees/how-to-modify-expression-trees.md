---
title: "如何︰ 修改運算式樹狀架構 (Visual Basic) |Microsoft 文件"
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
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
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
ms.openlocfilehash: 2f0d383cbac639212519177fb1825875682f6233
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="e5bfa-102">如何︰ 修改運算式樹狀架構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5bfa-102">How to: Modify Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="e5bfa-103">本主題說明如何修改運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="e5bfa-104">運算式樹狀架構是不可變的也就是說，它們無法直接進行修改。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="e5bfa-105">若要變更運算式樹狀架構，您必須建立一份現有運算式樹狀架構，並建立複本時進行必要的變更。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="e5bfa-106">您可以使用<xref:System.Linq.Expressions.ExpressionVisitor>類別來周遊現有運算式樹狀架構，並複製造訪每個節點。</xref:System.Linq.Expressions.ExpressionVisitor></span><span class="sxs-lookup"><span data-stu-id="e5bfa-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="e5bfa-107">若要修改運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="e5bfa-107">To modify an expression tree</span></span>  
  
1.  <span data-ttu-id="e5bfa-108">建立新**主控台應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-108">Create a new **Console Application** project.</span></span>  
  
2.  <span data-ttu-id="e5bfa-109">新增`Imports`陳述式的檔案來`System.Linq.Expressions`命名空間。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3.  <span data-ttu-id="e5bfa-110">新增`AndAlsoModifier`類別，以您的專案。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
    ```vb  
    Public Class AndAlsoModifier  
        Inherits ExpressionVisitor  
  
        Public Function Modify(ByVal expr As Expression) As Expression  
            Return Visit(expr)  
        End Function  
  
        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression  
            If b.NodeType = ExpressionType.AndAlso Then  
                Dim left = Me.Visit(b.Left)  
                Dim right = Me.Visit(b.Right)  
  
                ' Make this binary expression an OrElse operation instead   
                ' of an AndAlso operation.  
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _  
                                             b.IsLiftedToNull, b.Method)  
            End If  
  
            Return MyBase.VisitBinary(b)  
        End Function  
    End Class  
    ```  
  
     <span data-ttu-id="e5bfa-111">此類別會繼承<xref:System.Linq.Expressions.ExpressionVisitor>類別，專門用來修改這些運算式表示條件式`AND`作業。</xref:System.Linq.Expressions.ExpressionVisitor></span><span class="sxs-lookup"><span data-stu-id="e5bfa-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="e5bfa-112">它會從在條件變更這些作業`AND`conditional `OR`。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="e5bfa-113">若要這樣做，類別覆寫<xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A>方法的基底型別，因為條件式`AND`運算式表示為二進位運算式。</xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A></span><span class="sxs-lookup"><span data-stu-id="e5bfa-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="e5bfa-114">在`VisitBinary`方法，如果傳遞給它的運算式代表條件式`AND`作業，程式碼會建構新的運算式，其中包含條件式`OR`而不是條件式運算子`AND`運算子。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="e5bfa-115">如果傳遞給運算式`VisitBinary`不代表條件式`AND`作業，方法會延後的基底類別實作。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="e5bfa-116">建構的節點類似，會傳入的運算式樹狀架構，但節點已取代的運算式樹狀架構及其子樹狀目錄的基底類別方法產生以遞迴方式訪客。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4.  <span data-ttu-id="e5bfa-117">新增`Imports`陳述式的檔案來`System.Linq.Expressions`命名空間。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5.  <span data-ttu-id="e5bfa-118">將程式碼加入`Main`方法來建立運算式樹狀架構，並將它傳遞給方法的 Module1.vb 檔案中將修改它。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
    ```vb  
    Dim expr As Expression(Of Func(Of String, Boolean)) = _  
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")  
  
    Console.WriteLine(expr)  
  
    Dim modifier As New AndAlsoModifier()  
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))  
  
    Console.WriteLine(modifiedExpr)  
  
    ' This code produces the following output:  
    ' name => ((name.Length > 10) && name.StartsWith("G"))  
    ' name => ((name.Length > 10) || name.StartsWith("G"))  
    ```  
  
     <span data-ttu-id="e5bfa-119">程式碼會建立包含條件運算式`AND`作業。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="e5bfa-120">然後它會建立的執行個體`AndAlsoModifier`類別，並將運算式傳遞至`Modify`這個類別的方法。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="e5bfa-121">原始和修改後的運算式樹狀結構會輸出到顯示變更。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6.  <span data-ttu-id="e5bfa-122">編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5bfa-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5bfa-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5bfa-123">See Also</span></span>  
 <span data-ttu-id="e5bfa-124">[如何︰ 執行運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span><span class="sxs-lookup"><span data-stu-id="e5bfa-124">[How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span></span>  
<span data-ttu-id="e5bfa-125"> [運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)</span><span class="sxs-lookup"><span data-stu-id="e5bfa-125"> [Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)</span></span>
