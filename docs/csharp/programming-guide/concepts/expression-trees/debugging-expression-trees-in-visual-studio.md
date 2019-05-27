---
title: Visual Studio 中的偵錯運算式樹狀架構 (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 4017e2c2592dc1d6067b428fc1d47f37775abf85
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877190"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="8122f-102">Visual Studio 中的偵錯運算式樹狀架構 (C#)</span><span class="sxs-lookup"><span data-stu-id="8122f-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="8122f-103">當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。</span><span class="sxs-lookup"><span data-stu-id="8122f-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="8122f-104">若要取得運算式樹狀架構的快速概觀，您可以使用 `DebugView` 屬性，它使用[以下](#debugview-syntax)所述的特殊語法代表運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="8122f-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees using a special syntax described [below](#debugview-syntax).</span></span> <span data-ttu-id="8122f-105">(請注意，`DebugView` 僅適用於偵錯模式。)</span><span class="sxs-lookup"><span data-stu-id="8122f-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Visual Studio 偵錯工具中的運算式樹狀架構 DebugView](media/debugging-expression-trees-in-visual-studio/debugview.png)

<span data-ttu-id="8122f-107">由於 `DebugView` 是字串，所以您可以使用[內建的文字視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)跨多行檢視它，請從 `DebugView` 標籤旁的放大鏡圖示選取 [文字視覺化檢視]。</span><span class="sxs-lookup"><span data-stu-id="8122f-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![套用至 'DebugView' 結果的文字視覺化檢視](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

<span data-ttu-id="8122f-109">或者，您可以安裝並使用[自訂的視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)來處理運算式樹狀架構：</span><span class="sxs-lookup"><span data-stu-id="8122f-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees:</span></span>

* <span data-ttu-id="8122f-110">[可讀取的運算式](https://github.com/agileobjects/ReadableExpressions) ([MIT 授權](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)，位於 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers))，將運算式樹狀架構轉譯為 C# 程式碼：</span><span class="sxs-lookup"><span data-stu-id="8122f-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![可讀取的運算式視覺化檢視](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="8122f-112">[運算式樹狀架構視覺化檢視](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT 授權](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE))，提供運算式樹狀架構的圖形檢視、其屬性和相關物件：</span><span class="sxs-lookup"><span data-stu-id="8122f-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![ExpressionToString 視覺化檢視](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="8122f-114">開啟運算式樹狀架構的視覺化檢視</span><span class="sxs-lookup"><span data-stu-id="8122f-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="8122f-115">在 [DataTips]、[監看式] 視窗、[自動變數] 視窗或 [區域變數] 視窗中，按一下出現在運算式樹狀架構旁邊的放大鏡圖示。</span><span class="sxs-lookup"><span data-stu-id="8122f-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="8122f-116">可用的視覺化檢視清單隨即顯示：</span><span class="sxs-lookup"><span data-stu-id="8122f-116">A list of available visualizers is displayed.:</span></span> 

      ![從 Visual Studio 開啟視覺化檢視](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. <span data-ttu-id="8122f-118">按一下要使用的視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="8122f-118">Click the visualizer you want to use.</span></span>  

## <a name="debugview-syntax"></a><span data-ttu-id="8122f-119">`DebugView` 語法</span><span class="sxs-lookup"><span data-stu-id="8122f-119">`DebugView` syntax</span></span> 

<span data-ttu-id="8122f-120">如下列各節所述，`DebugView` 屬性會顯示每個運算式型別。</span><span class="sxs-lookup"><span data-stu-id="8122f-120">Each expression type is displayed by the `DebugView` property as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="8122f-121">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="8122f-121">ParameterExpressions</span></span>  
 <span data-ttu-id="8122f-122">顯示 <xref:System.Linq.Expressions.ParameterExpression> 變數名稱時，其開頭會加上 "$" 符號。</span><span class="sxs-lookup"><span data-stu-id="8122f-122"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="8122f-123">如果參數沒有名稱，會指派自動產生的名稱給它，例如 `$var1` 或 `$var2`。</span><span class="sxs-lookup"><span data-stu-id="8122f-123">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="8122f-124">範例</span><span class="sxs-lookup"><span data-stu-id="8122f-124">Examples</span></span>  
  
|<span data-ttu-id="8122f-125">運算式</span><span class="sxs-lookup"><span data-stu-id="8122f-125">Expression</span></span>|<span data-ttu-id="8122f-126">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="8122f-126">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="8122f-127">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="8122f-127">ConstantExpressions</span></span>  
 <span data-ttu-id="8122f-128">對於代表整數值、字串和 `null` 的 <xref:System.Linq.Expressions.ConstantExpression> 物件，會顯示常數的值。</span><span class="sxs-lookup"><span data-stu-id="8122f-128">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="8122f-129">對於具有標準尾碼為 C# 常值的數值類型，尾碼會新增至值。</span><span class="sxs-lookup"><span data-stu-id="8122f-129">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="8122f-130">下表顯示各種不同之數值類型的相關聯尾碼。</span><span class="sxs-lookup"><span data-stu-id="8122f-130">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="8122f-131">類型</span><span class="sxs-lookup"><span data-stu-id="8122f-131">Type</span></span>|<span data-ttu-id="8122f-132">尾碼</span><span class="sxs-lookup"><span data-stu-id="8122f-132">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="8122f-133">U</span><span class="sxs-lookup"><span data-stu-id="8122f-133">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="8122f-134">L</span><span class="sxs-lookup"><span data-stu-id="8122f-134">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="8122f-135">UL</span><span class="sxs-lookup"><span data-stu-id="8122f-135">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="8122f-136">D</span><span class="sxs-lookup"><span data-stu-id="8122f-136">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="8122f-137">F</span><span class="sxs-lookup"><span data-stu-id="8122f-137">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="8122f-138">M</span><span class="sxs-lookup"><span data-stu-id="8122f-138">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="8122f-139">範例</span><span class="sxs-lookup"><span data-stu-id="8122f-139">Examples</span></span>  
  
|<span data-ttu-id="8122f-140">運算式</span><span class="sxs-lookup"><span data-stu-id="8122f-140">Expression</span></span>|<span data-ttu-id="8122f-141">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="8122f-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="8122f-142">10</span><span class="sxs-lookup"><span data-stu-id="8122f-142">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="8122f-143">10D</span><span class="sxs-lookup"><span data-stu-id="8122f-143">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="8122f-144">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="8122f-144">BlockExpression</span></span>  
 <span data-ttu-id="8122f-145">如果 <xref:System.Linq.Expressions.BlockExpression> 物件的類型與區塊中最後一個運算式的類型不同，類型會顯示於 `DebugInfo` 屬性中並加上角括弧 (\< 和 >)。</span><span class="sxs-lookup"><span data-stu-id="8122f-145">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="8122f-146">否則，不會顯示 <xref:System.Linq.Expressions.BlockExpression> 物件的類型。</span><span class="sxs-lookup"><span data-stu-id="8122f-146">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="8122f-147">範例</span><span class="sxs-lookup"><span data-stu-id="8122f-147">Examples</span></span>  
  
|<span data-ttu-id="8122f-148">運算式</span><span class="sxs-lookup"><span data-stu-id="8122f-148">Expression</span></span>|<span data-ttu-id="8122f-149">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="8122f-149">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="8122f-150">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="8122f-150">LambdaExpression</span></span>  
 <span data-ttu-id="8122f-151"><xref:System.Linq.Expressions.LambdaExpression> 物件會與其委派類型一起顯示。</span><span class="sxs-lookup"><span data-stu-id="8122f-151"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="8122f-152">如果 Lambda 運算式沒有名稱，會指派自動產生的名稱給它，例如 `#Lambda1` 或 `#Lambda2`。</span><span class="sxs-lookup"><span data-stu-id="8122f-152">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="8122f-153">範例</span><span class="sxs-lookup"><span data-stu-id="8122f-153">Examples</span></span>  
  
|<span data-ttu-id="8122f-154">運算式</span><span class="sxs-lookup"><span data-stu-id="8122f-154">Expression</span></span>|<span data-ttu-id="8122f-155">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="8122f-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="8122f-156">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="8122f-156">LabelExpression</span></span>  
 <span data-ttu-id="8122f-157">如果您指定 <xref:System.Linq.Expressions.LabelExpression> 物件的預設值，這個值會顯示在 <xref:System.Linq.Expressions.LabelTarget> 物件之前。</span><span class="sxs-lookup"><span data-stu-id="8122f-157">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="8122f-158">`.Label` 語彙基元表示標籤的開頭。</span><span class="sxs-lookup"><span data-stu-id="8122f-158">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="8122f-159">`.LabelTarget` 語彙基元表示要跳至的目標目的地。</span><span class="sxs-lookup"><span data-stu-id="8122f-159">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="8122f-160">如果標籤沒有名稱，會指派自動產生的名稱給它，例如 `#Label1` 或 `#Label2`。</span><span class="sxs-lookup"><span data-stu-id="8122f-160">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="8122f-161">範例</span><span class="sxs-lookup"><span data-stu-id="8122f-161">Examples</span></span>  
  
|<span data-ttu-id="8122f-162">運算式</span><span class="sxs-lookup"><span data-stu-id="8122f-162">Expression</span></span>|<span data-ttu-id="8122f-163">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="8122f-163">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="8122f-164">檢查的運算子</span><span class="sxs-lookup"><span data-stu-id="8122f-164">Checked Operators</span></span>  
 <span data-ttu-id="8122f-165">顯示檢查的運算子時，運算子前面會有 "#" 符號。</span><span class="sxs-lookup"><span data-stu-id="8122f-165">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="8122f-166">例如，已檢查的加法運算子會顯示為 `#+`。</span><span class="sxs-lookup"><span data-stu-id="8122f-166">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="8122f-167">範例</span><span class="sxs-lookup"><span data-stu-id="8122f-167">Examples</span></span>  
  
|<span data-ttu-id="8122f-168">運算式</span><span class="sxs-lookup"><span data-stu-id="8122f-168">Expression</span></span>|<span data-ttu-id="8122f-169">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="8122f-169">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="8122f-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8122f-170">See also</span></span>

- [<span data-ttu-id="8122f-171">運算式樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="8122f-171">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="8122f-172">Visual Studio 偵錯</span><span class="sxs-lookup"><span data-stu-id="8122f-172">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="8122f-173">建立自訂視覺化檢視</span><span class="sxs-lookup"><span data-stu-id="8122f-173">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
