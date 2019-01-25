---
title: 在 Visual Studio (Visual Basic) 中的偵錯運算式樹狀架構
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: b060a65a38c4ab295a54f972678f273ada218d06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617352"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="52378-102">在 Visual Studio (Visual Basic) 中的偵錯運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="52378-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="52378-103">當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。</span><span class="sxs-lookup"><span data-stu-id="52378-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="52378-104">若要取得運算式樹狀結構的快速概觀，您可以使用 `DebugView` 屬性，它只適用於偵錯模式。</span><span class="sxs-lookup"><span data-stu-id="52378-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="52378-105">如需偵錯的詳細資訊，請參閱 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="52378-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="52378-106">為了更能代表運算式樹狀架構的內容，`DebugView` 屬性使用 Visual Studio 視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="52378-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="52378-107">如需詳細資訊，請參閱[建立自訂視覺化檢視](/visualstudio/debugger/create-custom-visualizers-of-data)。</span><span class="sxs-lookup"><span data-stu-id="52378-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="52378-108">開啟運算式樹狀架構的視覺化檢視</span><span class="sxs-lookup"><span data-stu-id="52378-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="52378-109">在 [DataTips]、[監看式] 視窗，或是在 [自動變數] 視窗或 [區域變數] 視窗中，按一下出現在運算式樹狀架構 `DebugView` 屬性旁邊的放大鏡圖示。</span><span class="sxs-lookup"><span data-stu-id="52378-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="52378-110">視覺化檢視的清單隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="52378-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="52378-111">按一下要使用的視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="52378-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="52378-112">如下列各節中所述，每個運算式類型會顯示在視覺化檢視中。</span><span class="sxs-lookup"><span data-stu-id="52378-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="52378-113">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="52378-113">ParameterExpressions</span></span>  
 <span data-ttu-id="52378-114">顯示 <xref:System.Linq.Expressions.ParameterExpression> 變數名稱時，其開頭會加上 "$" 符號。</span><span class="sxs-lookup"><span data-stu-id="52378-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="52378-115">如果參數沒有名稱，會指派自動產生的名稱給它，例如 `$var1` 或 `$var2`。</span><span class="sxs-lookup"><span data-stu-id="52378-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="52378-116">範例</span><span class="sxs-lookup"><span data-stu-id="52378-116">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     <span data-ttu-id="52378-117">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="52378-117">`DebugView` property</span></span>  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     <span data-ttu-id="52378-118">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="52378-118">`DebugView` property</span></span>  
  
     `$var1`  
  
## <a name="constantexpressions"></a><span data-ttu-id="52378-119">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="52378-119">ConstantExpressions</span></span>  
 <span data-ttu-id="52378-120">對於代表整數值、字串和 `null` 的 <xref:System.Linq.Expressions.ConstantExpression> 物件，會顯示常數的值。</span><span class="sxs-lookup"><span data-stu-id="52378-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="52378-121">範例</span><span class="sxs-lookup"><span data-stu-id="52378-121">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="52378-122">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="52378-122">`DebugView` property</span></span>  
  
     <span data-ttu-id="52378-123">10</span><span class="sxs-lookup"><span data-stu-id="52378-123">10</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="52378-124">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="52378-124">`DebugView` property</span></span>  
  
     <span data-ttu-id="52378-125">10D</span><span class="sxs-lookup"><span data-stu-id="52378-125">10D</span></span>  
  
## <a name="blockexpression"></a><span data-ttu-id="52378-126">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="52378-126">BlockExpression</span></span>  
 <span data-ttu-id="52378-127">如果 <xref:System.Linq.Expressions.BlockExpression> 物件的類型與區塊中最後一個運算式的類型不同，類型會顯示於 `DebugInfo` 屬性中並加上角括弧 (\< 和 >)。</span><span class="sxs-lookup"><span data-stu-id="52378-127">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="52378-128">否則，不會顯示 <xref:System.Linq.Expressions.BlockExpression> 物件的類型。</span><span class="sxs-lookup"><span data-stu-id="52378-128">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="52378-129">範例</span><span class="sxs-lookup"><span data-stu-id="52378-129">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="52378-130">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="52378-130">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="52378-131">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="52378-131">`DebugView` property</span></span>  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a><span data-ttu-id="52378-132">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="52378-132">LambdaExpression</span></span>  
 <span data-ttu-id="52378-133"><xref:System.Linq.Expressions.LambdaExpression> 物件會與其委派類型一起顯示。</span><span class="sxs-lookup"><span data-stu-id="52378-133"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="52378-134">如果 Lambda 運算式沒有名稱，會指派自動產生的名稱給它，例如 `#Lambda1` 或 `#Lambda2`。</span><span class="sxs-lookup"><span data-stu-id="52378-134">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="52378-135">範例</span><span class="sxs-lookup"><span data-stu-id="52378-135">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     <span data-ttu-id="52378-136">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="52378-136">`DebugView` property</span></span>  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     <span data-ttu-id="52378-137">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="52378-137">`DebugView` property</span></span>  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a><span data-ttu-id="52378-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="52378-138">LabelExpression</span></span>  
 <span data-ttu-id="52378-139">如果您指定 <xref:System.Linq.Expressions.LabelExpression> 物件的預設值，這個值會顯示在 <xref:System.Linq.Expressions.LabelTarget> 物件之前。</span><span class="sxs-lookup"><span data-stu-id="52378-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="52378-140">`.Label` 語彙基元表示標籤的開頭。</span><span class="sxs-lookup"><span data-stu-id="52378-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="52378-141">`.LabelTarget` 語彙基元表示要跳至的目標目的地。</span><span class="sxs-lookup"><span data-stu-id="52378-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="52378-142">如果標籤沒有名稱，會指派自動產生的名稱給它，例如 `#Label1` 或 `#Label2`。</span><span class="sxs-lookup"><span data-stu-id="52378-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="52378-143">範例</span><span class="sxs-lookup"><span data-stu-id="52378-143">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     <span data-ttu-id="52378-144">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="52378-144">`DebugView` property</span></span>  
  
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
  
     <span data-ttu-id="52378-145">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="52378-145">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a><span data-ttu-id="52378-146">檢查的運算子</span><span class="sxs-lookup"><span data-stu-id="52378-146">Checked Operators</span></span>  
 <span data-ttu-id="52378-147">顯示檢查的運算子時，運算子前面會有 "#" 符號。</span><span class="sxs-lookup"><span data-stu-id="52378-147">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="52378-148">例如，已檢查的加法運算子會顯示為 `#+`。</span><span class="sxs-lookup"><span data-stu-id="52378-148">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="52378-149">範例</span><span class="sxs-lookup"><span data-stu-id="52378-149">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     <span data-ttu-id="52378-150">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="52378-150">`DebugView` property</span></span>  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     <span data-ttu-id="52378-151">`DebugView` 屬性</span><span class="sxs-lookup"><span data-stu-id="52378-151">`DebugView` property</span></span>  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a><span data-ttu-id="52378-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52378-152">See also</span></span>
- [<span data-ttu-id="52378-153">運算式樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52378-153">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="52378-154">Visual Studio 偵錯</span><span class="sxs-lookup"><span data-stu-id="52378-154">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="52378-155">建立自訂視覺化檢視</span><span class="sxs-lookup"><span data-stu-id="52378-155">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
