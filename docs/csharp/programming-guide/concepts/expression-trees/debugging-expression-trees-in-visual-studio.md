---
title: "Visual Studio 中的偵錯運算式樹狀架構 (C#)"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0cf40b38ca9a6f743aca2894506e1d0ea80c9d57
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Visual Studio 中的偵錯運算式樹狀架構 (C#)
當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。 若要取得運算式樹狀結構的快速概觀，您可以使用 `DebugView` 屬性，它只適用於偵錯模式。 如需偵錯的詳細資訊，請參閱 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)。  
  
 為了更能代表運算式樹狀架構的內容，`DebugView` 屬性使用 Visual Studio 視覺化檢視。 如需詳細資訊，請參閱[建立自訂視覺化檢視](/visualstudio/debugger/create-custom-visualizers-of-data)。  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>開啟運算式樹狀架構的視覺化檢視  
  
1.  在 [DataTips]、[監看式] 視窗，或是在 [自動變數] 視窗或 [區域變數] 視窗中，按一下出現在運算式樹狀架構 `DebugView` 屬性旁邊的放大鏡圖示。  
  
     視覺化檢視的清單隨即顯示。  
  
2.  按一下要使用的視覺化檢視。  
  
 如下列各節中所述，每個運算式類型會顯示在視覺化檢視中。  
  
## <a name="parameterexpressions"></a>ParameterExpression  
 顯示 <xref:System.Linq.Expressions.ParameterExpression> 變數名稱時，其開頭會加上 "$" 符號。  
  
 如果參數沒有名稱，會指派自動產生的名稱給它，例如 `$var1` 或 `$var2`。  
  
### <a name="examples"></a>範例  
  
|運算式|`DebugView` 屬性|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a>ConstantExpression  
 對於代表整數值、字串和 `null` 的 <xref:System.Linq.Expressions.ConstantExpression> 物件，會顯示常數的值。  
  
 對於具有標準尾碼為 C# 常值的數值類型，尾碼會新增至值。 下表顯示各種不同之數值類型的相關聯尾碼。  
  
|類型|尾碼|  
|----------|------------|  
|<xref:System.UInt32>|U|  
|<xref:System.Int64>|L|  
|<xref:System.UInt64>|UL|  
|<xref:System.Double>|D|  
|<xref:System.Single>|F|  
|<xref:System.Decimal>|M|  
  
### <a name="examples"></a>範例  
  
|運算式|`DebugView` 屬性|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|10|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|10D|  
  
## <a name="blockexpression"></a>BlockExpression  
 如果 <xref:System.Linq.Expressions.BlockExpression> 物件的類型與區塊中最後一個運算式的類型不同，類型會顯示於 `DebugInfo` 屬性中並加上角括弧 (\< 和 >)。 否則，不會顯示 <xref:System.Linq.Expressions.BlockExpression> 物件的類型。  
  
### <a name="examples"></a>範例  
  
|運算式|`DebugView` 屬性|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression> 物件會與其委派類型一起顯示。  
  
 如果 Lambda 運算式沒有名稱，會指派自動產生的名稱給它，例如 `#Lambda1` 或 `#Lambda2`。  
  
### <a name="examples"></a>範例  
  
|運算式|`DebugView` 屬性|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a>LabelExpression  
 如果您指定 <xref:System.Linq.Expressions.LabelExpression> 物件的預設值，這個值會顯示在 <xref:System.Linq.Expressions.LabelTarget> 物件之前。  
  
 `.Label` 語彙基元表示標籤的開頭。 `.LabelTarget` 語彙基元表示要跳至的目標目的地。  
  
 如果標籤沒有名稱，會指派自動產生的名稱給它，例如 `#Label1` 或 `#Label2`。  
  
### <a name="examples"></a>範例  
  
|運算式|`DebugView` 屬性|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a>檢查的運算子  
 顯示檢查的運算子時，運算子前面會有 "#" 符號。 例如，已檢查的加法運算子會顯示為 `#+`。  
  
### <a name="examples"></a>範例  
  
|運算式|`DebugView` 屬性|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a>另請參閱  
 [運算式樹狀架構 (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)   
 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)   
 [建立自訂視覺化檢視](/visualstudio/debugger/create-custom-visualizers-of-data)

