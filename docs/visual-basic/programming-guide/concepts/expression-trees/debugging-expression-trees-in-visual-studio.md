---
title: 在 Visual Studio 中偵測運算式樹狀架構 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 3334828475ef5d933ea660ea33ae264d4ccce172
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106872"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>在 Visual Studio 中偵測運算式樹狀架構 (Visual Basic)
當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。 若要取得運算式樹狀架構的快速概觀，您可以使用 `DebugView` 屬性，其代表[使用特殊語法](debugview-syntax.md)的運算式樹狀架構。 (請注意，`DebugView` 僅適用於偵錯模式。)  

![Visual Studio 偵錯工具中的運算式樹狀架構 DebugView](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

由於 `DebugView` 是字串，所以您可以使用[內建的文字視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)跨多行檢視它，請從 `DebugView` 標籤旁的放大鏡圖示選取 [文字視覺化檢視]。

 ![套用至 'DebugView' 結果的文字視覺化檢視](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

或者，您可以安裝並使用適用於運算式樹狀架構的[自訂視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)，例如：

- [可讀取的運算式](https://github.com/agileobjects/ReadableExpressions) ([MIT 授權](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)，位於 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers))，將運算式樹狀架構轉譯為 C# 程式碼：

  ![可讀取的運算式視覺化檢視](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

- [運算式樹狀架構視覺化](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees)([MIT 授權](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), 提供運算式樹狀結構、其屬性和相關物件的圖形化視圖;和可以使用 Visual Basic 程式碼來轉譯運算式樹狀架構:

  ![ExpressionToString 視覺化檢視](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>開啟運算式樹狀架構的視覺化檢視  
  
1. 在 [DataTips]、[監看式] 視窗、[自動變數] 視窗或 [區域變數] 視窗中，按一下出現在運算式樹狀架構旁邊的放大鏡圖示。  
  
     可用的視覺化檢視清單隨即顯示： 

      ![從 Visual Studio 開啟視覺化檢視](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. 按一下要使用的視覺化檢視。  

## <a name="see-also"></a>另請參閱

- [運算式樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)
- [建立自訂視覺化檢視](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView` 語法](debugview-syntax.md)
