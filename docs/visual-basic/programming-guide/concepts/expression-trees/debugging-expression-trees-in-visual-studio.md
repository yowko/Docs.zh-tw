---
title: 在 Visual Studio 中對運算式樹狀架構進行偵錯
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 3811958353d1d55ce74da41c6a45dbe730cc9790
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375430"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>在 Visual Studio 中偵測運算式樹狀架構（Visual Basic）
當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。 若要取得運算式樹狀架構的快速概觀，您可以使用 `DebugView` 屬性，其代表[使用特殊語法](debugview-syntax.md)的運算式樹狀架構。 (請注意，`DebugView` 僅適用於偵錯模式。)  

![運算式樹狀架構 DebugView 的螢幕擷取畫面。](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

由於 `DebugView` 是字串，所以您可以使用[內建的文字視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)跨多行檢視它，請從 `DebugView` 標籤旁的放大鏡圖示選取 [文字視覺化檢視]****。

 ![適用于 DebugView 結果的文字視覺化螢幕擷取畫面。](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

或者，您可以安裝並使用適用於運算式樹狀架構的[自訂視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)，例如：

- [可讀取的運算式](https://github.com/agileobjects/ReadableExpressions)（[MIT 授權](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)（可在[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)使用），會將運算式樹狀架構轉譯為 themeable c # 程式碼，並具有各種呈現選項：

  ![可讀取的運算式視覺化檢視的螢幕擷取畫面。](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [運算式樹狀架構視覺化檢視](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md)（[MIT 授權](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)）提供運算式樹狀結構和其個別節點的樹狀檢視;和可以使用 Visual Basic 語法來轉譯運算式樹狀架構：

  ![運算式樹狀架構視覺化檢視的螢幕擷取畫面。](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>開啟運算式樹狀架構的視覺化檢視  
  
1. 在 [DataTips]****、[監看式]**** 視窗、[自動變數]**** 視窗或 [區域變數]**** 視窗中，按一下出現在運算式樹狀架構旁邊的放大鏡圖示。  
  
    可用的視覺化檢視清單隨即顯示：

    ![使用者從 Visual Studio 開啟視覺化檢視的螢幕擷取畫面。](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. 按一下要使用的視覺化檢視。  

## <a name="see-also"></a>另請參閱

- [運算式樹狀結構 (Visual Basic)](index.md)
- [Visual Studio 偵錯](/visualstudio/debugger/debugger-feature-tour)
- [建立自訂視覺化檢視](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`語法](debugview-syntax.md)
