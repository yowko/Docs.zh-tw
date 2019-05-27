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
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Visual Studio 中的偵錯運算式樹狀架構 (C#)
當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。 若要取得運算式樹狀架構的快速概觀，您可以使用 `DebugView` 屬性，它使用[以下](#debugview-syntax)所述的特殊語法代表運算式樹狀架構。 (請注意，`DebugView` 僅適用於偵錯模式。)  

![Visual Studio 偵錯工具中的運算式樹狀架構 DebugView](media/debugging-expression-trees-in-visual-studio/debugview.png)

由於 `DebugView` 是字串，所以您可以使用[內建的文字視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)跨多行檢視它，請從 `DebugView` 標籤旁的放大鏡圖示選取 [文字視覺化檢視]。

 ![套用至 'DebugView' 結果的文字視覺化檢視](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

或者，您可以安裝並使用[自訂的視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)來處理運算式樹狀架構：

* [可讀取的運算式](https://github.com/agileobjects/ReadableExpressions) ([MIT 授權](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)，位於 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers))，將運算式樹狀架構轉譯為 C# 程式碼：

  ![可讀取的運算式視覺化檢視](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [運算式樹狀架構視覺化檢視](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT 授權](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE))，提供運算式樹狀架構的圖形檢視、其屬性和相關物件：

  ![ExpressionToString 視覺化檢視](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>開啟運算式樹狀架構的視覺化檢視  
  
1. 在 [DataTips]、[監看式] 視窗、[自動變數] 視窗或 [區域變數] 視窗中，按一下出現在運算式樹狀架構旁邊的放大鏡圖示。  
  
     可用的視覺化檢視清單隨即顯示： 

      ![從 Visual Studio 開啟視覺化檢視](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. 按一下要使用的視覺化檢視。  

## <a name="debugview-syntax"></a>`DebugView` 語法 

如下列各節所述，`DebugView` 屬性會顯示每個運算式型別。  
  
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

- [運算式樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)
- [建立自訂視覺化檢視](/visualstudio/debugger/create-custom-visualizers-of-data)
