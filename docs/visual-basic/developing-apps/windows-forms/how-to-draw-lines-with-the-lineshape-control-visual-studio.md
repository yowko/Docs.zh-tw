---
title: "如何：使用 LineShape 控制項繪製線條 (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42e7f01a57a514ad1dc64e3d4451ce38ea199f93
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a><span data-ttu-id="5fe6c-102">如何：使用 LineShape 控制項繪製線條 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5fe6c-102">How to: Draw Lines with the LineShape Control (Visual Studio)</span></span>
<span data-ttu-id="5fe6c-103">您可以使用<xref:Microsoft.VisualBasic.PowerPacks.LineShape>控制項在表單或容器上繪製水平、 垂直或對角線，在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="5fe6c-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control to draw horizontal, vertical, or diagonal lines on a form or container, both at design time and at run time.</span></span>  
  
 <span data-ttu-id="5fe6c-104">**請注意**您的電腦可能會顯示不同的名稱或位置的某些 Visual Studio 使用者介面項目中的下列指示。</span><span class="sxs-lookup"><span data-stu-id="5fe6c-104">**Note** Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="5fe6c-105">您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。</span><span class="sxs-lookup"><span data-stu-id="5fe6c-105">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="5fe6c-106">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="5fe6c-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-line-at-design-time"></a><span data-ttu-id="5fe6c-107">在設計階段繪製線條</span><span class="sxs-lookup"><span data-stu-id="5fe6c-107">To draw a line at design time</span></span>  
  
1.  <span data-ttu-id="5fe6c-108">拖曳<xref:Microsoft.VisualBasic.PowerPacks.LineShape>控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**拖曳到表單或容器控制項。</span><span class="sxs-lookup"><span data-stu-id="5fe6c-108">Drag the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control from the **Visual Basic PowerPacks** tab in the **Toolbox** drag to a form or container control.</span></span>  
  
2.  <span data-ttu-id="5fe6c-109">拖曳調整大小並移動控點大小和位置的行。</span><span class="sxs-lookup"><span data-stu-id="5fe6c-109">Drag the sizing and move handles to size and position the line.</span></span>  
  
     <span data-ttu-id="5fe6c-110">您可以調整大小，並藉由變更調整線條`X1`， `X2`， `Y1`，和`Y2`中的屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="5fe6c-110">You can also size and position the line by changing the `X1`, `X2`, `Y1`, and `Y2` properties in the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="5fe6c-111">在**屬性**視窗中，選擇性地設定其他屬性如`BorderStyle`或`BorderColor`若要變更線條的外觀。</span><span class="sxs-lookup"><span data-stu-id="5fe6c-111">In the **Properties** window, optionally set additional properties such as `BorderStyle` or `BorderColor` to change the appearance of the line.</span></span>  
  
### <a name="to-draw-a-line-at-run-time"></a><span data-ttu-id="5fe6c-112">若要在執行階段繪製一條線</span><span class="sxs-lookup"><span data-stu-id="5fe6c-112">To draw a line at run time</span></span>  
  
1.  <span data-ttu-id="5fe6c-113">在 [專案] 功能表上，按一下 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="5fe6c-113">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="5fe6c-114">在**加入參考**對話方塊中，選取**Microsoft.VisualBasic.PowerPacks.VS**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="5fe6c-114">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="5fe6c-115">在**程式碼編輯器**，新增`Imports`或`using`陳述式之模組的頂端：</span><span class="sxs-lookup"><span data-stu-id="5fe6c-115">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="5fe6c-116">在 `Event` 程序中加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="5fe6c-116">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5fe6c-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="5fe6c-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [<span data-ttu-id="5fe6c-118">Line 和 Shape 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="5fe6c-118">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="5fe6c-119">操作說明：使用 OvalShape 和 RectangleShape 控制項繪製圖案</span><span class="sxs-lookup"><span data-stu-id="5fe6c-119">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
