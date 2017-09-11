---
title: "偵錯運算式樹狀架構，在 Visual Studio (Visual Basic) |Microsoft 文件"
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
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 84de749afad6abb748d0622561f8ee7cd399ed54
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="4231a-102">在 Visual Studio (Visual Basic) 中的偵錯運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="4231a-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="4231a-103">當您偵錯您的應用程式時，您可以分析的結構與內容的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="4231a-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="4231a-104">若要取得運算式樹狀結構的快速概觀，您可以使用`DebugView`屬性，亦即只適用於偵錯模式。</span><span class="sxs-lookup"><span data-stu-id="4231a-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="4231a-105">如需有關偵錯的詳細資訊，請參閱[Visual Studio 偵錯](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="4231a-105">For more information about debugging, see [Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="4231a-106">若要更能代表內容的運算式樹狀架構，`DebugView`屬性會使用 Visual Studio 視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="4231a-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="4231a-107">如需詳細資訊，請參閱[建立自訂視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)。</span><span class="sxs-lookup"><span data-stu-id="4231a-107">For more information, see [Create Custom Visualizers](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="4231a-108">若要開啟運算式樹狀架構視覺化檢視</span><span class="sxs-lookup"><span data-stu-id="4231a-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="4231a-109">按一下放大鏡圖示旁邊出現`DebugView`屬性的運算式樹狀架構中**DataTips**、**監看式** 視窗中，**自動變數** 視窗中，或**區域變數**視窗。</span><span class="sxs-lookup"><span data-stu-id="4231a-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="4231a-110">視覺化檢視的清單隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="4231a-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="4231a-111">按一下要使用的視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="4231a-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="4231a-112">下列各節中所述，每個運算式型別會顯示在視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="4231a-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="4231a-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="4231a-113">ParameterExpressions</span></span>  
 <span data-ttu-id="4231a-114"><xref:System.Linq.Expressions.ParameterExpression>變數名稱會加上"$"符號開頭。</xref:System.Linq.Expressions.ParameterExpression></span><span class="sxs-lookup"><span data-stu-id="4231a-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="4231a-115">如果參數沒有名稱，指派自動產生的名稱，例如`$var1`或`$var2`。</span><span class="sxs-lookup"><span data-stu-id="4231a-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="4231a-116">範例</span><span class="sxs-lookup"><span data-stu-id="4231a-116">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     <span data-ttu-id="4231a-117">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="4231a-117">`DebugView` property</span></span>  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     <span data-ttu-id="4231a-118">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="4231a-118">`DebugView` property</span></span>  
  
     `$var1`  
  
## <a name="constantexpressions"></a><span data-ttu-id="4231a-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="4231a-119">ConstantExpressions</span></span>  
 <span data-ttu-id="4231a-120">如<xref:System.Linq.Expressions.ConstantExpression>整數值的字串表示的物件和`null`，就會顯示常數的值。</xref:System.Linq.Expressions.ConstantExpression></span><span class="sxs-lookup"><span data-stu-id="4231a-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="4231a-121">範例</span><span class="sxs-lookup"><span data-stu-id="4231a-121">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="4231a-122">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="4231a-122">`DebugView` property</span></span>  
  
     <span data-ttu-id="4231a-123">10</span><span class="sxs-lookup"><span data-stu-id="4231a-123">10</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="4231a-124">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="4231a-124">`DebugView` property</span></span>  
  
     <span data-ttu-id="4231a-125">10 D</span><span class="sxs-lookup"><span data-stu-id="4231a-125">10D</span></span>  
  
## <a name="blockexpression"></a><span data-ttu-id="4231a-126">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="4231a-126">BlockExpression</span></span>  
 <span data-ttu-id="4231a-127">如果類型<xref:System.Linq.Expressions.BlockExpression>區塊中的最後一個運算式的型別不同的物件，型別會顯示於`DebugInfo`角括弧括住的屬性 (\<和 >)。</xref:System.Linq.Expressions.BlockExpression></span><span class="sxs-lookup"><span data-stu-id="4231a-127">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="4231a-128">否則，類型<xref:System.Linq.Expressions.BlockExpression>不會顯示物件。</xref:System.Linq.Expressions.BlockExpression></span><span class="sxs-lookup"><span data-stu-id="4231a-128">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="4231a-129">範例</span><span class="sxs-lookup"><span data-stu-id="4231a-129">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="4231a-130">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="4231a-130">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="4231a-131">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="4231a-131">`DebugView` property</span></span>  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a><span data-ttu-id="4231a-132">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="4231a-132">LambdaExpression</span></span>  
 <span data-ttu-id="4231a-133"><xref:System.Linq.Expressions.LambdaExpression>會顯示物件，以及其委派類型。</xref:System.Linq.Expressions.LambdaExpression></span><span class="sxs-lookup"><span data-stu-id="4231a-133"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="4231a-134">如果 lambda 運算式並沒有名稱，它指派自動產生的名稱，例如`#Lambda1`或`#Lambda2`。</span><span class="sxs-lookup"><span data-stu-id="4231a-134">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="4231a-135">範例</span><span class="sxs-lookup"><span data-stu-id="4231a-135">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     <span data-ttu-id="4231a-136">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="4231a-136">`DebugView` property</span></span>  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     <span data-ttu-id="4231a-137">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="4231a-137">`DebugView` property</span></span>  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a><span data-ttu-id="4231a-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="4231a-138">LabelExpression</span></span>  
 <span data-ttu-id="4231a-139">如果您指定的預設值<xref:System.Linq.Expressions.LabelExpression>物件，這個值會顯示前<xref:System.Linq.Expressions.LabelTarget>物件。</xref:System.Linq.Expressions.LabelTarget> </xref:System.Linq.Expressions.LabelExpression></span><span class="sxs-lookup"><span data-stu-id="4231a-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="4231a-140">`.Label`語彙基元表示標籤的開頭。</span><span class="sxs-lookup"><span data-stu-id="4231a-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="4231a-141">`.LabelTarget`權杖指出跳至目標目的地。</span><span class="sxs-lookup"><span data-stu-id="4231a-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="4231a-142">如果標籤沒有名稱，指派自動產生的名稱，例如`#Label1`或`#Label2`。</span><span class="sxs-lookup"><span data-stu-id="4231a-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="4231a-143">範例</span><span class="sxs-lookup"><span data-stu-id="4231a-143">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     <span data-ttu-id="4231a-144">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="4231a-144">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto SampleLabel { 0 };`  
  
     `.Label`  
  
     `-1`  
  
     `.LabelTarget SampleLabel:`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label()  
    Dim block As BlockExpression = Expression.Block(  
    Expression.Goto(target), Expression.Label(target))  
    ```  
  
     <span data-ttu-id="4231a-145">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="4231a-145">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a><span data-ttu-id="4231a-146">檢查的運算子</span><span class="sxs-lookup"><span data-stu-id="4231a-146">Checked Operators</span></span>  
 <span data-ttu-id="4231a-147">檢查的運算子中會顯示以"#"符號前面的運算子。</span><span class="sxs-lookup"><span data-stu-id="4231a-147">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="4231a-148">例如，已檢查的加法運算子會顯示為`#+`。</span><span class="sxs-lookup"><span data-stu-id="4231a-148">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="4231a-149">範例</span><span class="sxs-lookup"><span data-stu-id="4231a-149">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     <span data-ttu-id="4231a-150">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="4231a-150">`DebugView` property</span></span>  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     <span data-ttu-id="4231a-151">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="4231a-151">`DebugView` property</span></span>  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a><span data-ttu-id="4231a-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4231a-152">See Also</span></span>  
 <span data-ttu-id="4231a-153">[運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="4231a-153">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="4231a-154"> [Visual Studio 偵錯](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="4231a-154"> [Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span></span>  
<span data-ttu-id="4231a-155"> [建立自訂的視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)</span><span class="sxs-lookup"><span data-stu-id="4231a-155"> [Create Custom Visualizers](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)</span></span>
