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
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>在 Visual Studio (Visual Basic) 中的偵錯運算式樹狀架構
當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。 若要取得運算式樹狀結構的快速概觀，您可以使用`DebugView`屬性，代表運算式樹狀架構使用特殊語法所述[下方](#debugview-syntax)。 (請注意，`DebugView`僅適用於偵錯模式。)  

![DebugView 中的 Visual Studio 偵錯工具中的運算式樹狀架構](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

由於`DebugView`是一個字串，您可以使用[內建文字視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)來檢視它跨多行，選取**文字視覺化檢視**旁邊的放大鏡圖示從`DebugView`標籤。

 ![文字視覺化檢視套用至 'DebugView' 的結果](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

或者，您可以安裝並使用[自訂視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)的運算式樹狀架構：

* [可讀取的運算式](https://github.com/agileobjects/ReadableExpressions)([MIT 授權](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)，網址[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers))，轉譯運算式樹狀架構，為C#的程式碼：

  ![可讀取的運算式視覺化檢視](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [運算式樹狀架構視覺化檢閱](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees)([MIT 授權](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) 提供的運算式樹狀結構、 屬性和相關的物件的圖形檢視，可以轉譯運算式樹狀架構，使用 Visual Basic 程式碼：

  ![ExpressionToString 視覺化檢視](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>開啟運算式樹狀架構的視覺化檢視  
  
1. 按一下放大鏡圖示旁邊的運算式樹狀目錄中顯示**DataTips**，則**監看式** 視窗中，**自動變數**視窗中，或**區域變數**  視窗。  
  
     一份可用的視覺化檢視會顯示。: 

      ![從 Visual Studio 開啟視覺化檢視](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. 按一下要使用的視覺化檢視。  

## <a name="debugview-syntax"></a>`DebugView` 語法 

如下列各節中所述，每個運算式類型會顯示在視覺化檢視中。

## <a name="parameterexpressions"></a>ParameterExpression

顯示 <xref:System.Linq.Expressions.ParameterExpression> 變數名稱時，其開頭會加上 "$" 符號。

如果參數沒有名稱，會指派自動產生的名稱給它，例如 `$var1` 或 `$var2`。

### <a name="examples"></a>範例

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer), "num")
    ```

    `DebugView` 屬性

    `$num`

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer))
    ```

    `DebugView` 屬性

    `$var1`

## <a name="constantexpressions"></a>ConstantExpression
 對於代表整數值、字串和 `null` 的 <xref:System.Linq.Expressions.ConstantExpression> 物件，會顯示常數的值。

### <a name="examples"></a>範例

- `Expression`

    ```vb
    Dim num as Integer= 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    `DebugView` 屬性

    10

- `Expression`

    ```vb
    Dim num As Double = 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    `DebugView` 屬性

    10D

## <a name="blockexpression"></a>BlockExpression

如果 <xref:System.Linq.Expressions.BlockExpression> 物件的類型與區塊中最後一個運算式的類型不同，類型會顯示於 `DebugInfo` 屬性中並加上角括弧 (\< 和 >)。 否則，不會顯示 <xref:System.Linq.Expressions.BlockExpression> 物件的類型。

### <a name="examples"></a>範例

- `Expression`

    ```vb
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
    ```

    `DebugView` 屬性

    `.Block() {`

    `"test"`

    `}`

- `Expression`

    ```vb
    Dim block As BlockExpression =
    Expression.Block(GetType(Object), Expression.Constant("test"))
    ```

    `DebugView` 屬性

    `.Block<System.Object>() {`

    `"test"`

    `}`

## <a name="lambdaexpression"></a>LambdaExpression

<xref:System.Linq.Expressions.LambdaExpression> 物件會與其委派類型一起顯示。

如果 Lambda 運算式沒有名稱，會指派自動產生的名稱給它，例如 `#Lambda1` 或 `#Lambda2`。

### <a name="examples"></a>範例

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))
    ```

    `DebugView` 屬性

    `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`

    `1`

    `}`

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLambda", Nothing)
    ```

    `DebugView` 屬性

    `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`

    `1`

    `}`

## <a name="labelexpression"></a>LabelExpression

如果您指定 <xref:System.Linq.Expressions.LabelExpression> 物件的預設值，這個值會顯示在 <xref:System.Linq.Expressions.LabelTarget> 物件之前。

`.Label` 語彙基元表示標籤的開頭。 `.LabelTarget` 語彙基元表示要跳至的目標目的地。

如果標籤沒有名稱，會指派自動產生的名稱給它，例如 `#Label1` 或 `#Label2`。

### <a name="examples"></a>範例

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
    Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1)))
    ```

    `DebugView` 屬性

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

    `DebugView` 屬性

    `.Block() {`

    `.Goto #Label1 { };`

    `.Label`

    `.LabelTarget #Label1:`

    `}`

## <a name="checked-operators"></a>檢查的運算子

顯示檢查的運算子時，運算子前面會有 "#" 符號。 例如，已檢查的加法運算子會顯示為 `#+`。

### <a name="examples"></a>範例

- `Expression`

    ```vb
    Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1), Expression.Constant(2))
    ```

    `DebugView` 屬性

    `1 #+ 2`

- `Expression`

    ```vb
    Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0), GetType(Integer))
    ```

    `DebugView` 屬性

    `#(System.Int32)10D`

## <a name="see-also"></a>另請參閱

- [運算式樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)
- [建立自訂視覺化檢視](/visualstudio/debugger/create-custom-visualizers-of-data)
