---
title: 在 Visual Studio (Visual Basic) 中的偵錯運算式樹狀架構
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 9aead09e0e9469f13e2d6befbad444d3c7fecabd
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196018"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>在 Visual Studio (Visual Basic) 中的偵錯運算式樹狀架構
當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。 若要取得運算式樹狀結構的快速概觀，您可以使用`DebugView`屬性，代表運算式樹狀架構[使用特殊語法](debugview-syntax.md)。 (請注意，`DebugView` 僅適用於偵錯模式。)  

![Visual Studio 偵錯工具中的運算式樹狀架構 DebugView](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

由於 `DebugView` 是字串，所以您可以使用[內建的文字視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)跨多行檢視它，請從 `DebugView` 標籤旁的放大鏡圖示選取 [文字視覺化檢視]。

 ![套用至 'DebugView' 結果的文字視覺化檢視](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

或者，您可以安裝並使用[自訂視覺化檢視](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)的運算式樹狀架構，例如：

* [可讀取的運算式](https://github.com/agileobjects/ReadableExpressions) ([MIT 授權](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)，位於 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers))，將運算式樹狀架構轉譯為 C# 程式碼：

  ![可讀取的運算式視覺化檢視](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [運算式樹狀架構視覺化檢閱](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees)([MIT 授權](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) 提供的運算式樹狀結構、 屬性和相關的物件的圖形檢視，可以轉譯運算式樹狀架構，使用 Visual Basic 程式碼：

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
