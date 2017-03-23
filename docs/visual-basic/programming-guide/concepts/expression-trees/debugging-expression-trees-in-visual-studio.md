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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: efbd8c19947c45b3ba15ce7b574000d56526ef45
ms.lasthandoff: 03/13/2017

---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>在 Visual Studio (Visual Basic) 中的偵錯運算式樹狀架構
當您偵錯您的應用程式時，您可以分析的結構與內容的運算式樹狀架構。 若要取得運算式樹狀結構的快速概觀，您可以使用`DebugView`屬性，亦即只適用於偵錯模式。 如需有關偵錯的詳細資訊，請參閱[Visual Studio 偵錯](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)。  
  
 若要更能代表內容的運算式樹狀架構，`DebugView`屬性會使用 Visual Studio 視覺化檢視。 如需詳細資訊，請參閱[建立自訂視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)。  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>若要開啟運算式樹狀架構視覺化檢視  
  
1.  按一下放大鏡圖示旁邊出現`DebugView`屬性的運算式樹狀架構中**DataTips**、**監看式** 視窗中，**自動變數** 視窗中，或**區域變數**視窗。  
  
     視覺化檢視的清單隨即顯示。  
  
2.  按一下要使用的視覺化檢視。  
  
 下列各節中所述，每個運算式型別會顯示在視覺化檢視。  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 <xref:System.Linq.Expressions.ParameterExpression>變數名稱會加上"$"符號開頭。</xref:System.Linq.Expressions.ParameterExpression>  
  
 如果參數沒有名稱，指派自動產生的名稱，例如`$var1`或`$var2`。  
  
### <a name="examples"></a>範例  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     `DebugView` 屬性  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     `DebugView` 屬性  
  
     `$var1`  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 如<xref:System.Linq.Expressions.ConstantExpression>整數值的字串表示的物件和`null`，就會顯示常數的值。</xref:System.Linq.Expressions.ConstantExpression>  
  
### <a name="examples"></a>範例  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     `DebugView` 屬性  
  
     10  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     `DebugView` 屬性  
  
     10 D  
  
## <a name="blockexpression"></a>BlockExpression  
 如果類型<xref:System.Linq.Expressions.BlockExpression>區塊中的最後一個運算式的型別不同的物件，型別會顯示於`DebugInfo`角括弧括住的屬性 (\<和 >)。</xref:System.Linq.Expressions.BlockExpression> 否則，類型<xref:System.Linq.Expressions.BlockExpression>不會顯示物件。</xref:System.Linq.Expressions.BlockExpression>  
  
### <a name="examples"></a>範例  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     `DebugView` 屬性  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     `DebugView` 屬性  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression>會顯示物件，以及其委派類型。</xref:System.Linq.Expressions.LambdaExpression>  
  
 如果 lambda 運算式並沒有名稱，它指派自動產生的名稱，例如`#Lambda1`或`#Lambda2`。  
  
### <a name="examples"></a>範例  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     `DebugView` 屬性  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     `DebugView` 屬性  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a>LabelExpression  
 如果您指定的預設值<xref:System.Linq.Expressions.LabelExpression>物件，這個值會顯示前<xref:System.Linq.Expressions.LabelTarget>物件。</xref:System.Linq.Expressions.LabelTarget> </xref:System.Linq.Expressions.LabelExpression>  
  
 `.Label`語彙基元表示標籤的開頭。 `.LabelTarget`權杖指出跳至目標目的地。  
  
 如果標籤沒有名稱，指派自動產生的名稱，例如`#Label1`或`#Label2`。  
  
### <a name="examples"></a>範例  
  
-   `Expression`  
  
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
  
-   `Expression`  
  
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
 檢查的運算子中會顯示以"#"符號前面的運算子。 例如，已檢查的加法運算子會顯示為`#+`。  
  
### <a name="examples"></a>範例  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     `DebugView` 屬性  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     `DebugView` 屬性  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a>另請參閱  
 [運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)   
 [Visual Studio 偵錯](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)   
 [建立自訂的視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)
