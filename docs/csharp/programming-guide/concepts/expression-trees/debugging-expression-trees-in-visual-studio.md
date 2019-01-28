---
title: Visual Studio 中的偵錯運算式樹狀架構 (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 308b377af00a3d12523f8f8d469c50808f216030
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632149"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="f07ad-102">Visual Studio 中的偵錯運算式樹狀架構 (C#)</span><span class="sxs-lookup"><span data-stu-id="f07ad-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="f07ad-103">當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。</span><span class="sxs-lookup"><span data-stu-id="f07ad-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="f07ad-104">若要取得運算式樹狀結構的快速概觀，您可以使用 `DebugView` 屬性，它只適用於偵錯模式。</span><span class="sxs-lookup"><span data-stu-id="f07ad-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="f07ad-105">如需偵錯的詳細資訊，請參閱 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="f07ad-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="f07ad-106">為了更能代表運算式樹狀架構的內容，`DebugView` 屬性使用 Visual Studio 視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="f07ad-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="f07ad-107">如需詳細資訊，請參閱[建立自訂視覺化檢視](/visualstudio/debugger/create-custom-visualizers-of-data)。</span><span class="sxs-lookup"><span data-stu-id="f07ad-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="f07ad-108">開啟運算式樹狀架構的視覺化檢視</span><span class="sxs-lookup"><span data-stu-id="f07ad-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="f07ad-109">在 [DataTips]、[監看式] 視窗，或是在 [自動變數] 視窗或 [區域變數] 視窗中，按一下出現在運算式樹狀架構 `DebugView` 屬性旁邊的放大鏡圖示。</span><span class="sxs-lookup"><span data-stu-id="f07ad-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="f07ad-110">視覺化檢視的清單隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="f07ad-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="f07ad-111">按一下要使用的視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="f07ad-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="f07ad-112">如下列各節中所述，每個運算式類型會顯示在視覺化檢視中。</span><span class="sxs-lookup"><span data-stu-id="f07ad-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="f07ad-113">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="f07ad-113">ParameterExpressions</span></span>  
 <span data-ttu-id="f07ad-114">顯示 <xref:System.Linq.Expressions.ParameterExpression> 變數名稱時，其開頭會加上 "$" 符號。</span><span class="sxs-lookup"><span data-stu-id="f07ad-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="f07ad-115">如果參數沒有名稱，會指派自動產生的名稱給它，例如 `$var1` 或 `$var2`。</span><span class="sxs-lookup"><span data-stu-id="f07ad-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="f07ad-116">範例</span><span class="sxs-lookup"><span data-stu-id="f07ad-116">Examples</span></span>  
  
|<span data-ttu-id="f07ad-117">運算式</span><span class="sxs-lookup"><span data-stu-id="f07ad-117">Expression</span></span>|<span data-ttu-id="f07ad-118">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="f07ad-118">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="f07ad-119">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="f07ad-119">ConstantExpressions</span></span>  
 <span data-ttu-id="f07ad-120">對於代表整數值、字串和 `null` 的 <xref:System.Linq.Expressions.ConstantExpression> 物件，會顯示常數的值。</span><span class="sxs-lookup"><span data-stu-id="f07ad-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="f07ad-121">對於具有標準尾碼為 C# 常值的數值類型，尾碼會新增至值。</span><span class="sxs-lookup"><span data-stu-id="f07ad-121">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="f07ad-122">下表顯示各種不同之數值類型的相關聯尾碼。</span><span class="sxs-lookup"><span data-stu-id="f07ad-122">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="f07ad-123">類型</span><span class="sxs-lookup"><span data-stu-id="f07ad-123">Type</span></span>|<span data-ttu-id="f07ad-124">尾碼</span><span class="sxs-lookup"><span data-stu-id="f07ad-124">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="f07ad-125">U</span><span class="sxs-lookup"><span data-stu-id="f07ad-125">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="f07ad-126">L</span><span class="sxs-lookup"><span data-stu-id="f07ad-126">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="f07ad-127">UL</span><span class="sxs-lookup"><span data-stu-id="f07ad-127">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="f07ad-128">D</span><span class="sxs-lookup"><span data-stu-id="f07ad-128">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="f07ad-129">F</span><span class="sxs-lookup"><span data-stu-id="f07ad-129">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="f07ad-130">M</span><span class="sxs-lookup"><span data-stu-id="f07ad-130">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="f07ad-131">範例</span><span class="sxs-lookup"><span data-stu-id="f07ad-131">Examples</span></span>  
  
|<span data-ttu-id="f07ad-132">運算式</span><span class="sxs-lookup"><span data-stu-id="f07ad-132">Expression</span></span>|<span data-ttu-id="f07ad-133">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="f07ad-133">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="f07ad-134">10</span><span class="sxs-lookup"><span data-stu-id="f07ad-134">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="f07ad-135">10D</span><span class="sxs-lookup"><span data-stu-id="f07ad-135">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="f07ad-136">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="f07ad-136">BlockExpression</span></span>  
 <span data-ttu-id="f07ad-137">如果 <xref:System.Linq.Expressions.BlockExpression> 物件的類型與區塊中最後一個運算式的類型不同，類型會顯示於 `DebugInfo` 屬性中並加上角括弧 (\< 和 >)。</span><span class="sxs-lookup"><span data-stu-id="f07ad-137">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="f07ad-138">否則，不會顯示 <xref:System.Linq.Expressions.BlockExpression> 物件的類型。</span><span class="sxs-lookup"><span data-stu-id="f07ad-138">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="f07ad-139">範例</span><span class="sxs-lookup"><span data-stu-id="f07ad-139">Examples</span></span>  
  
|<span data-ttu-id="f07ad-140">運算式</span><span class="sxs-lookup"><span data-stu-id="f07ad-140">Expression</span></span>|<span data-ttu-id="f07ad-141">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="f07ad-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="f07ad-142">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="f07ad-142">LambdaExpression</span></span>  
 <span data-ttu-id="f07ad-143"><xref:System.Linq.Expressions.LambdaExpression> 物件會與其委派類型一起顯示。</span><span class="sxs-lookup"><span data-stu-id="f07ad-143"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="f07ad-144">如果 Lambda 運算式沒有名稱，會指派自動產生的名稱給它，例如 `#Lambda1` 或 `#Lambda2`。</span><span class="sxs-lookup"><span data-stu-id="f07ad-144">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="f07ad-145">範例</span><span class="sxs-lookup"><span data-stu-id="f07ad-145">Examples</span></span>  
  
|<span data-ttu-id="f07ad-146">運算式</span><span class="sxs-lookup"><span data-stu-id="f07ad-146">Expression</span></span>|<span data-ttu-id="f07ad-147">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="f07ad-147">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="f07ad-148">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="f07ad-148">LabelExpression</span></span>  
 <span data-ttu-id="f07ad-149">如果您指定 <xref:System.Linq.Expressions.LabelExpression> 物件的預設值，這個值會顯示在 <xref:System.Linq.Expressions.LabelTarget> 物件之前。</span><span class="sxs-lookup"><span data-stu-id="f07ad-149">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="f07ad-150">`.Label` 語彙基元表示標籤的開頭。</span><span class="sxs-lookup"><span data-stu-id="f07ad-150">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="f07ad-151">`.LabelTarget` 語彙基元表示要跳至的目標目的地。</span><span class="sxs-lookup"><span data-stu-id="f07ad-151">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="f07ad-152">如果標籤沒有名稱，會指派自動產生的名稱給它，例如 `#Label1` 或 `#Label2`。</span><span class="sxs-lookup"><span data-stu-id="f07ad-152">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="f07ad-153">範例</span><span class="sxs-lookup"><span data-stu-id="f07ad-153">Examples</span></span>  
  
|<span data-ttu-id="f07ad-154">運算式</span><span class="sxs-lookup"><span data-stu-id="f07ad-154">Expression</span></span>|<span data-ttu-id="f07ad-155">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="f07ad-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="f07ad-156">檢查的運算子</span><span class="sxs-lookup"><span data-stu-id="f07ad-156">Checked Operators</span></span>  
 <span data-ttu-id="f07ad-157">顯示檢查的運算子時，運算子前面會有 "#" 符號。</span><span class="sxs-lookup"><span data-stu-id="f07ad-157">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="f07ad-158">例如，已檢查的加法運算子會顯示為 `#+`。</span><span class="sxs-lookup"><span data-stu-id="f07ad-158">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="f07ad-159">範例</span><span class="sxs-lookup"><span data-stu-id="f07ad-159">Examples</span></span>  
  
|<span data-ttu-id="f07ad-160">運算式</span><span class="sxs-lookup"><span data-stu-id="f07ad-160">Expression</span></span>|<span data-ttu-id="f07ad-161">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="f07ad-161">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="f07ad-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f07ad-162">See also</span></span>

- [<span data-ttu-id="f07ad-163">運算式樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="f07ad-163">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="f07ad-164">Visual Studio 偵錯</span><span class="sxs-lookup"><span data-stu-id="f07ad-164">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="f07ad-165">建立自訂視覺化檢視</span><span class="sxs-lookup"><span data-stu-id="f07ad-165">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
