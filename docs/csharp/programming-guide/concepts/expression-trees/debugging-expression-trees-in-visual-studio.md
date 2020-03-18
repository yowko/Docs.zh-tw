---
title: Visual Studio 中的偵錯運算式樹狀架構 (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: cf1708d1155e48d8609baca2067baa66dae08c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169684"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Visual Studio 中的偵錯運算式樹狀架構 (C#)
當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。 若要取得運算式樹狀架構的快速概觀，您可以使用 `DebugView` 屬性，其代表[使用特殊語法](debugview-syntax.md)的運算式樹狀架構。 (請注意，`DebugView` 僅適用於偵錯模式。)  

![VS 調試器中運算式樹的調試視圖的螢幕截圖。](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

由於 `DebugView` 是字串，所以您可以使用[內建的文字視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)跨多行檢視它，請從 `DebugView` 標籤旁的放大鏡圖示選取 [文字視覺化檢視]****。

 ![應用於調試視圖結果的文本視覺化檢視的螢幕截圖。](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

或者，您可以安裝並使用適用於運算式樹狀架構的[自訂視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)，例如：

- [可讀取的運算式](https://github.com/agileobjects/ReadableExpressions) ([MIT 授權](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)，位於 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers))，將運算式樹狀架構轉譯為 C# 程式碼：

  ![可讀運算式視覺化檢視的螢幕截圖。](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [運算式樹狀架構視覺化檢視](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT 授權](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE))，提供運算式樹狀架構的圖形檢視、其屬性和相關物件：

  ![運算式樹視覺化檢視的螢幕截圖。](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>開啟運算式樹狀架構的視覺化檢視  
  
1. 在 [DataTips]****、[監看式]**** 視窗、[自動變數]**** 視窗或 [區域變數]**** 視窗中，按一下出現在運算式樹狀架構旁邊的放大鏡圖示。  

    可用的視覺化檢視清單隨即顯示：

    ![顯示視覺工作室視覺化檢視的打開的螢幕截圖。](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. 按一下要使用的視覺化檢視。  
  
## <a name="see-also"></a>另請參閱

- [運算式樹狀架構 (C#)](./index.md)
- [Visual Studio 偵錯](/visualstudio/debugger/debugger-feature-tour)
- [建立自訂視覺化檢視](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`語法](debugview-syntax.md)
