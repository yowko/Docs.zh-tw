---
title: "Visual Studio 中的偵錯運算式樹狀架構 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 14ab67e78a3b4c4819ddca36a406526e78f5485e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="23170-102">Visual Studio 中的偵錯運算式樹狀架構 (C#)</span><span class="sxs-lookup"><span data-stu-id="23170-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="23170-103">當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。</span><span class="sxs-lookup"><span data-stu-id="23170-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="23170-104">若要取得運算式樹狀結構的快速概觀，您可以使用 `DebugView` 屬性，它只適用於偵錯模式。</span><span class="sxs-lookup"><span data-stu-id="23170-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="23170-105">如需偵錯的詳細資訊，請參閱 [Visual Studio 偵錯](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="23170-105">For more information about debugging, see [Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="23170-106">為了更能代表運算式樹狀架構的內容，`DebugView` 屬性使用 Visual Studio 視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="23170-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="23170-107">如需詳細資訊，請參閱[建立自訂視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)。</span><span class="sxs-lookup"><span data-stu-id="23170-107">For more information, see [Create Custom Visualizers](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="23170-108">開啟運算式樹狀架構的視覺化檢視</span><span class="sxs-lookup"><span data-stu-id="23170-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="23170-109">在 [DataTips]****、[監看式]**** 視窗，或是在 [自動變數]**** 視窗或 [區域變數]**** 視窗中，按一下出現在運算式樹狀架構 `DebugView` 屬性旁邊的放大鏡圖示。</span><span class="sxs-lookup"><span data-stu-id="23170-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="23170-110">視覺化檢視的清單隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="23170-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="23170-111">按一下要使用的視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="23170-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="23170-112">如下列各節中所述，每個運算式類型會顯示在視覺化檢視中。</span><span class="sxs-lookup"><span data-stu-id="23170-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="23170-113">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="23170-113">ParameterExpressions</span></span>  
 <span data-ttu-id="23170-114">顯示 <xref:System.Linq.Expressions.ParameterExpression> 變數名稱時，其開頭會加上 "$" 符號。</span><span class="sxs-lookup"><span data-stu-id="23170-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="23170-115">如果參數沒有名稱，會指派自動產生的名稱給它，例如 `$var1` 或 `$var2`。</span><span class="sxs-lookup"><span data-stu-id="23170-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="23170-116">範例</span><span class="sxs-lookup"><span data-stu-id="23170-116">Examples</span></span>  
  
|<span data-ttu-id="23170-117">運算式</span><span class="sxs-lookup"><span data-stu-id="23170-117">Expression</span></span>|<span data-ttu-id="23170-118">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="23170-118">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="23170-119">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="23170-119">ConstantExpressions</span></span>  
 <span data-ttu-id="23170-120">對於代表整數值、字串和 `null` 的 <xref:System.Linq.Expressions.ConstantExpression> 物件，會顯示常數的值。</span><span class="sxs-lookup"><span data-stu-id="23170-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="23170-121">對於具有標準尾碼為 C# 常值的數值類型，尾碼會新增至值。</span><span class="sxs-lookup"><span data-stu-id="23170-121">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="23170-122">下表顯示各種不同之數值類型的相關聯尾碼。</span><span class="sxs-lookup"><span data-stu-id="23170-122">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="23170-123">類型</span><span class="sxs-lookup"><span data-stu-id="23170-123">Type</span></span>|<span data-ttu-id="23170-124">尾碼</span><span class="sxs-lookup"><span data-stu-id="23170-124">Suffix</span></span>|  
|----------|------------|  
|<span data-ttu-id="23170-125"><xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="23170-125"><xref:System.UInt32></span></span>|<span data-ttu-id="23170-126">U</span><span class="sxs-lookup"><span data-stu-id="23170-126">U</span></span>|  
|<span data-ttu-id="23170-127"><xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="23170-127"><xref:System.Int64></span></span>|<span data-ttu-id="23170-128">L</span><span class="sxs-lookup"><span data-stu-id="23170-128">L</span></span>|  
|<span data-ttu-id="23170-129"><xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="23170-129"><xref:System.UInt64></span></span>|<span data-ttu-id="23170-130">UL</span><span class="sxs-lookup"><span data-stu-id="23170-130">UL</span></span>|  
|<span data-ttu-id="23170-131"><xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="23170-131"><xref:System.Double></span></span>|<span data-ttu-id="23170-132">D</span><span class="sxs-lookup"><span data-stu-id="23170-132">D</span></span>|  
|<span data-ttu-id="23170-133"><xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="23170-133"><xref:System.Single></span></span>|<span data-ttu-id="23170-134">F</span><span class="sxs-lookup"><span data-stu-id="23170-134">F</span></span>|  
|<span data-ttu-id="23170-135"><xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="23170-135"><xref:System.Decimal></span></span>|<span data-ttu-id="23170-136">M</span><span class="sxs-lookup"><span data-stu-id="23170-136">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="23170-137">範例</span><span class="sxs-lookup"><span data-stu-id="23170-137">Examples</span></span>  
  
|<span data-ttu-id="23170-138">運算式</span><span class="sxs-lookup"><span data-stu-id="23170-138">Expression</span></span>|<span data-ttu-id="23170-139">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="23170-139">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="23170-140">10</span><span class="sxs-lookup"><span data-stu-id="23170-140">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="23170-141">10D</span><span class="sxs-lookup"><span data-stu-id="23170-141">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="23170-142">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="23170-142">BlockExpression</span></span>  
 <span data-ttu-id="23170-143">如果 <xref:System.Linq.Expressions.BlockExpression> 物件的類型與區塊中最後一個運算式的類型不同，類型會顯示於 `DebugInfo` 屬性中並加上角括弧 (\< 和 >)。</span><span class="sxs-lookup"><span data-stu-id="23170-143">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="23170-144">否則，不會顯示 <xref:System.Linq.Expressions.BlockExpression> 物件的類型。</span><span class="sxs-lookup"><span data-stu-id="23170-144">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="23170-145">範例</span><span class="sxs-lookup"><span data-stu-id="23170-145">Examples</span></span>  
  
|<span data-ttu-id="23170-146">運算式</span><span class="sxs-lookup"><span data-stu-id="23170-146">Expression</span></span>|<span data-ttu-id="23170-147">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="23170-147">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="23170-148">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="23170-148">LambdaExpression</span></span>  
 <span data-ttu-id="23170-149"><xref:System.Linq.Expressions.LambdaExpression> 物件會與其委派類型一起顯示。</span><span class="sxs-lookup"><span data-stu-id="23170-149"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="23170-150">如果 Lambda 運算式沒有名稱，會指派自動產生的名稱給它，例如 `#Lambda1` 或 `#Lambda2`。</span><span class="sxs-lookup"><span data-stu-id="23170-150">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="23170-151">範例</span><span class="sxs-lookup"><span data-stu-id="23170-151">Examples</span></span>  
  
|<span data-ttu-id="23170-152">運算式</span><span class="sxs-lookup"><span data-stu-id="23170-152">Expression</span></span>|<span data-ttu-id="23170-153">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="23170-153">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="23170-154">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="23170-154">LabelExpression</span></span>  
 <span data-ttu-id="23170-155">如果您指定 <xref:System.Linq.Expressions.LabelExpression> 物件的預設值，這個值會顯示在 <xref:System.Linq.Expressions.LabelTarget> 物件之前。</span><span class="sxs-lookup"><span data-stu-id="23170-155">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="23170-156">`.Label` 語彙基元表示標籤的開頭。</span><span class="sxs-lookup"><span data-stu-id="23170-156">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="23170-157">`.LabelTarget` 語彙基元表示要跳至的目標目的地。</span><span class="sxs-lookup"><span data-stu-id="23170-157">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="23170-158">如果標籤沒有名稱，會指派自動產生的名稱給它，例如 `#Label1` 或 `#Label2`。</span><span class="sxs-lookup"><span data-stu-id="23170-158">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="23170-159">範例</span><span class="sxs-lookup"><span data-stu-id="23170-159">Examples</span></span>  
  
|<span data-ttu-id="23170-160">運算式</span><span class="sxs-lookup"><span data-stu-id="23170-160">Expression</span></span>|<span data-ttu-id="23170-161">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="23170-161">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="23170-162">檢查的運算子</span><span class="sxs-lookup"><span data-stu-id="23170-162">Checked Operators</span></span>  
 <span data-ttu-id="23170-163">顯示檢查的運算子時，運算子前面會有 "#" 符號。</span><span class="sxs-lookup"><span data-stu-id="23170-163">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="23170-164">例如，已檢查的加法運算子會顯示為 `#+`。</span><span class="sxs-lookup"><span data-stu-id="23170-164">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="23170-165">範例</span><span class="sxs-lookup"><span data-stu-id="23170-165">Examples</span></span>  
  
|<span data-ttu-id="23170-166">運算式</span><span class="sxs-lookup"><span data-stu-id="23170-166">Expression</span></span>|<span data-ttu-id="23170-167">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="23170-167">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="23170-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23170-168">See Also</span></span>  
 <span data-ttu-id="23170-169">[運算式樹狀架構 (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="23170-169">[Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="23170-170"> [Visual Studio 偵錯](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="23170-170"> [Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span></span>  
<span data-ttu-id="23170-171"> [建立自訂視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)</span><span class="sxs-lookup"><span data-stu-id="23170-171"> [Create Custom Visualizers](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)</span></span>
