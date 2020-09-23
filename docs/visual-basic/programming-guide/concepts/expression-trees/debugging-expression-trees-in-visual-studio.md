---
title: 在 Visual Studio 中對運算式樹狀架構進行偵錯
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: ae37f9b8ca05ba915d394922b73c519273e2d415
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086565"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="6d98d-102">在 Visual Studio (Visual Basic 中偵測運算式樹狀架構) </span><span class="sxs-lookup"><span data-stu-id="6d98d-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>

<span data-ttu-id="6d98d-103">當您針對應用程式進行偵錯時，可以分析運算式樹狀架構的結構與內容。</span><span class="sxs-lookup"><span data-stu-id="6d98d-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="6d98d-104">若要取得運算式樹狀架構的快速概觀，您可以使用 `DebugView` 屬性，其代表[使用特殊語法](debugview-syntax.md)的運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="6d98d-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="6d98d-105">(請注意，`DebugView` 僅適用於偵錯模式。)</span><span class="sxs-lookup"><span data-stu-id="6d98d-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![運算式樹狀架構 DebugView 的螢幕擷取畫面。](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

<span data-ttu-id="6d98d-107">由於 `DebugView` 是字串，所以您可以使用[內建的文字視覺化檢視](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)跨多行檢視它，請從 `DebugView` 標籤旁的放大鏡圖示選取 [文字視覺化檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6d98d-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![將文字視覺化套用至 DebugView 結果的螢幕擷取畫面。](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

<span data-ttu-id="6d98d-109">或者，您可以安裝並使用適用於運算式樹狀架構的[自訂視覺化檢視](/visualstudio/debugger/create-custom-visualizers-of-data)，例如：</span><span class="sxs-lookup"><span data-stu-id="6d98d-109">Alternatively, you can install and use [a custom visualizer](/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="6d98d-110">可[讀取的運算式](https://github.com/agileobjects/ReadableExpressions) ([MIT 授權](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)（可在[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) 取得）將運算式樹狀架構轉譯為 themeable c # 程式碼，並提供各種轉譯選項：</span><span class="sxs-lookup"><span data-stu-id="6d98d-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![可讀取的運算式視覺化程式的螢幕擷取畫面。](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="6d98d-112">[運算式樹狀架構視覺化](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT 授權](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) 提供運算式樹狀架構和其個別節點的樹狀檢視;和可以使用 Visual Basic 語法來轉譯運算式樹狀架構：</span><span class="sxs-lookup"><span data-stu-id="6d98d-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes; and can render the expression tree using Visual Basic syntax:</span></span>

  ![運算式樹狀架構視覺化程式的螢幕擷取畫面。](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="6d98d-114">開啟運算式樹狀架構的視覺化檢視</span><span class="sxs-lookup"><span data-stu-id="6d98d-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="6d98d-115">在 [DataTips]\*\*\*\*、[監看式]\*\*\*\* 視窗、[自動變數]\*\*\*\* 視窗或 [區域變數]\*\*\*\* 視窗中，按一下出現在運算式樹狀架構旁邊的放大鏡圖示。</span><span class="sxs-lookup"><span data-stu-id="6d98d-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
    <span data-ttu-id="6d98d-116">可用的視覺化檢視清單隨即顯示：</span><span class="sxs-lookup"><span data-stu-id="6d98d-116">A list of available visualizers is displayed.:</span></span>

    ![從 Visual Studio 開啟視覺化程式之使用者的螢幕擷取畫面。](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. <span data-ttu-id="6d98d-118">按一下要使用的視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="6d98d-118">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="6d98d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d98d-119">See also</span></span>

- [<span data-ttu-id="6d98d-120">運算式樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d98d-120">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="6d98d-121">Visual Studio 偵錯</span><span class="sxs-lookup"><span data-stu-id="6d98d-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="6d98d-122">建立自訂視覺化檢視</span><span class="sxs-lookup"><span data-stu-id="6d98d-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="6d98d-123">`DebugView` 語法</span><span class="sxs-lookup"><span data-stu-id="6d98d-123">`DebugView` syntax</span></span>](debugview-syntax.md)
