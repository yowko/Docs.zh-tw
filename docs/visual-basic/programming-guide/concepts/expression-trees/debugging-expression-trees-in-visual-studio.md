---
title: 在 Visual Studio (Visual Basic) 中的偵錯運算式樹狀架構
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 7fc97d898c5956b5a569036e6e0fe1174714576d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879861"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="9691d-102">在 Visual Studio (Visual Basic) 中的偵錯運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="9691d-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="9691d-103">當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。</span><span class="sxs-lookup"><span data-stu-id="9691d-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="9691d-104">若要取得運算式樹狀結構的快速概觀，您可以使用`DebugView`屬性，代表運算式樹狀架構使用特殊語法所述[下方](#debugview-syntax)。</span><span class="sxs-lookup"><span data-stu-id="9691d-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees using a special syntax described [below](#debugview-syntax).</span></span> <span data-ttu-id="9691d-105">(請注意，`DebugView`僅適用於偵錯模式。)</span><span class="sxs-lookup"><span data-stu-id="9691d-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![DebugView 中的 Visual Studio 偵錯工具中的運算式樹狀架構](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

<span data-ttu-id="9691d-107">由於`DebugView`是一個字串，您可以使用[內建文字視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)來檢視它跨多行，選取**文字視覺化檢視**旁邊的放大鏡圖示從`DebugView`標籤。</span><span class="sxs-lookup"><span data-stu-id="9691d-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![文字視覺化檢視套用至 'DebugView' 的結果](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

<span data-ttu-id="9691d-109">或者，您可以安裝並使用[自訂視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)的運算式樹狀架構：</span><span class="sxs-lookup"><span data-stu-id="9691d-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees:</span></span>

* <span data-ttu-id="9691d-110">[可讀取的運算式](https://github.com/agileobjects/ReadableExpressions)([MIT 授權](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)，網址[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers))，轉譯運算式樹狀架構，為C#的程式碼：</span><span class="sxs-lookup"><span data-stu-id="9691d-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![可讀取的運算式視覺化檢視](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="9691d-112">[運算式樹狀架構視覺化檢閱](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees)([MIT 授權](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) 提供的運算式樹狀結構、 屬性和相關的物件的圖形檢視，可以轉譯運算式樹狀架構，使用 Visual Basic 程式碼：</span><span class="sxs-lookup"><span data-stu-id="9691d-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects; and can render the expression tree using Visual Basic code:</span></span>

  ![ExpressionToString 視覺化檢視](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="9691d-114">開啟運算式樹狀架構的視覺化檢視</span><span class="sxs-lookup"><span data-stu-id="9691d-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="9691d-115">按一下放大鏡圖示旁邊的運算式樹狀目錄中顯示**DataTips**，則**監看式** 視窗中，**自動變數**視窗中，或**區域變數**  視窗。</span><span class="sxs-lookup"><span data-stu-id="9691d-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="9691d-116">一份可用的視覺化檢視會顯示。:</span><span class="sxs-lookup"><span data-stu-id="9691d-116">A list of available visualizers is displayed.:</span></span> 

      ![從 Visual Studio 開啟視覺化檢視](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. <span data-ttu-id="9691d-118">按一下要使用的視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="9691d-118">Click the visualizer you want to use.</span></span>  

## <a name="debugview-syntax"></a><span data-ttu-id="9691d-119">`DebugView` 語法</span><span class="sxs-lookup"><span data-stu-id="9691d-119">`DebugView` syntax</span></span> 

<span data-ttu-id="9691d-120">如下列各節中所述，每個運算式類型會顯示在視覺化檢視中。</span><span class="sxs-lookup"><span data-stu-id="9691d-120">Each expression type is displayed in the visualizer as described in the following sections.</span></span>

## <a name="parameterexpressions"></a><span data-ttu-id="9691d-121">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="9691d-121">ParameterExpressions</span></span>

<span data-ttu-id="9691d-122">顯示 <xref:System.Linq.Expressions.ParameterExpression> 變數名稱時，其開頭會加上 "$" 符號。</span><span class="sxs-lookup"><span data-stu-id="9691d-122"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="9691d-123">如果參數沒有名稱，會指派自動產生的名稱給它，例如 `$var1` 或 `$var2`。</span><span class="sxs-lookup"><span data-stu-id="9691d-123">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="9691d-124">範例</span><span class="sxs-lookup"><span data-stu-id="9691d-124">Examples</span></span>

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer), "num")
    ```

    <span data-ttu-id="9691d-125">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-125">`DebugView` property</span></span>

    `$num`

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer))
    ```

    <span data-ttu-id="9691d-126">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-126">`DebugView` property</span></span>

    `$var1`

## <a name="constantexpressions"></a><span data-ttu-id="9691d-127">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="9691d-127">ConstantExpressions</span></span>
 <span data-ttu-id="9691d-128">對於代表整數值、字串和 `null` 的 <xref:System.Linq.Expressions.ConstantExpression> 物件，會顯示常數的值。</span><span class="sxs-lookup"><span data-stu-id="9691d-128">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="9691d-129">範例</span><span class="sxs-lookup"><span data-stu-id="9691d-129">Examples</span></span>

- `Expression`

    ```vb
    Dim num as Integer= 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    <span data-ttu-id="9691d-130">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-130">`DebugView` property</span></span>

    <span data-ttu-id="9691d-131">10</span><span class="sxs-lookup"><span data-stu-id="9691d-131">10</span></span>

- `Expression`

    ```vb
    Dim num As Double = 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    <span data-ttu-id="9691d-132">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-132">`DebugView` property</span></span>

    <span data-ttu-id="9691d-133">10D</span><span class="sxs-lookup"><span data-stu-id="9691d-133">10D</span></span>

## <a name="blockexpression"></a><span data-ttu-id="9691d-134">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="9691d-134">BlockExpression</span></span>

<span data-ttu-id="9691d-135">如果 <xref:System.Linq.Expressions.BlockExpression> 物件的類型與區塊中最後一個運算式的類型不同，類型會顯示於 `DebugInfo` 屬性中並加上角括弧 (\< 和 >)。</span><span class="sxs-lookup"><span data-stu-id="9691d-135">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="9691d-136">否則，不會顯示 <xref:System.Linq.Expressions.BlockExpression> 物件的類型。</span><span class="sxs-lookup"><span data-stu-id="9691d-136">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="9691d-137">範例</span><span class="sxs-lookup"><span data-stu-id="9691d-137">Examples</span></span>

- `Expression`

    ```vb
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
    ```

    <span data-ttu-id="9691d-138">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-138">`DebugView` property</span></span>

    `.Block() {`

    `"test"`

    `}`

- `Expression`

    ```vb
    Dim block As BlockExpression =
    Expression.Block(GetType(Object), Expression.Constant("test"))
    ```

    <span data-ttu-id="9691d-139">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-139">`DebugView` property</span></span>

    `.Block<System.Object>() {`

    `"test"`

    `}`

## <a name="lambdaexpression"></a><span data-ttu-id="9691d-140">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="9691d-140">LambdaExpression</span></span>

<span data-ttu-id="9691d-141"><xref:System.Linq.Expressions.LambdaExpression> 物件會與其委派類型一起顯示。</span><span class="sxs-lookup"><span data-stu-id="9691d-141"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="9691d-142">如果 Lambda 運算式沒有名稱，會指派自動產生的名稱給它，例如 `#Lambda1` 或 `#Lambda2`。</span><span class="sxs-lookup"><span data-stu-id="9691d-142">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="9691d-143">範例</span><span class="sxs-lookup"><span data-stu-id="9691d-143">Examples</span></span>

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))
    ```

    <span data-ttu-id="9691d-144">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-144">`DebugView` property</span></span>

    `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`

    `1`

    `}`

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLambda", Nothing)
    ```

    <span data-ttu-id="9691d-145">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-145">`DebugView` property</span></span>

    `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`

    `1`

    `}`

## <a name="labelexpression"></a><span data-ttu-id="9691d-146">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="9691d-146">LabelExpression</span></span>

<span data-ttu-id="9691d-147">如果您指定 <xref:System.Linq.Expressions.LabelExpression> 物件的預設值，這個值會顯示在 <xref:System.Linq.Expressions.LabelTarget> 物件之前。</span><span class="sxs-lookup"><span data-stu-id="9691d-147">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>

<span data-ttu-id="9691d-148">`.Label` 語彙基元表示標籤的開頭。</span><span class="sxs-lookup"><span data-stu-id="9691d-148">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="9691d-149">`.LabelTarget` 語彙基元表示要跳至的目標目的地。</span><span class="sxs-lookup"><span data-stu-id="9691d-149">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="9691d-150">如果標籤沒有名稱，會指派自動產生的名稱給它，例如 `#Label1` 或 `#Label2`。</span><span class="sxs-lookup"><span data-stu-id="9691d-150">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="9691d-151">範例</span><span class="sxs-lookup"><span data-stu-id="9691d-151">Examples</span></span>

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
    Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1)))
    ```

    <span data-ttu-id="9691d-152">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-152">`DebugView` property</span></span>

    `.Block() {`

    `.Goto SampleLabel { 0 };`

    `.Label`

    `-1`

    `.LabelTarget SampleLabel:`

    `}`

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label()
    Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target), Expression.Label(target))
    ```

    <span data-ttu-id="9691d-153">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-153">`DebugView` property</span></span>

    `.Block() {`

    `.Goto #Label1 { };`

    `.Label`

    `.LabelTarget #Label1:`

    `}`

## <a name="checked-operators"></a><span data-ttu-id="9691d-154">檢查的運算子</span><span class="sxs-lookup"><span data-stu-id="9691d-154">Checked Operators</span></span>

<span data-ttu-id="9691d-155">顯示檢查的運算子時，運算子前面會有 "#" 符號。</span><span class="sxs-lookup"><span data-stu-id="9691d-155">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="9691d-156">例如，已檢查的加法運算子會顯示為 `#+`。</span><span class="sxs-lookup"><span data-stu-id="9691d-156">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="9691d-157">範例</span><span class="sxs-lookup"><span data-stu-id="9691d-157">Examples</span></span>

- `Expression`

    ```vb
    Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1), Expression.Constant(2))
    ```

    <span data-ttu-id="9691d-158">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-158">`DebugView` property</span></span>

    `1 #+ 2`

- `Expression`

    ```vb
    Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0), GetType(Integer))
    ```

    <span data-ttu-id="9691d-159">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="9691d-159">`DebugView` property</span></span>

    `#(System.Int32)10D`

## <a name="see-also"></a><span data-ttu-id="9691d-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9691d-160">See also</span></span>

- [<span data-ttu-id="9691d-161">運算式樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9691d-161">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="9691d-162">Visual Studio 偵錯</span><span class="sxs-lookup"><span data-stu-id="9691d-162">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="9691d-163">建立自訂視覺化檢視</span><span class="sxs-lookup"><span data-stu-id="9691d-163">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
