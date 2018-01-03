---
title: "如何：在圖案間啟用定位處理 (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0b1e8b0378e65becd80324491632ecd8dbffdbbf
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a><span data-ttu-id="52b3b-102">如何：在圖案間啟用定位處理 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="52b3b-102">How to: Enable Tabbing Between Shapes (Visual Studio)</span></span>
<span data-ttu-id="52b3b-103">Line 和 shape 控制項沒有`TabStop`或`TabIndex`屬性，但您仍然可以啟用它們之間按下 tab 鍵。</span><span class="sxs-lookup"><span data-stu-id="52b3b-103">Line and shape controls do not have `TabStop` or `TabIndex` properties, but you can still enable tabbing among them.</span></span> <span data-ttu-id="52b3b-104">在下列範例中，按下 ctrl 鍵和 TAB 鍵將索引標籤之間圖形;按 TAB 鍵將索引標籤按鈕之間。</span><span class="sxs-lookup"><span data-stu-id="52b3b-104">In the following example, pressing both the CTRL and the TAB keys will tab between shapes; pressing only the TAB key will tab between the buttons.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52b3b-105">在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：</span><span class="sxs-lookup"><span data-stu-id="52b3b-105">Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="52b3b-106">您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。</span><span class="sxs-lookup"><span data-stu-id="52b3b-106">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="52b3b-107">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="52b3b-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="to-enable-tabbing-among-shapes"></a><span data-ttu-id="52b3b-108">若要啟用定位處理之間圖形</span><span class="sxs-lookup"><span data-stu-id="52b3b-108">To enable tabbing among shapes</span></span>  
  
1.  <span data-ttu-id="52b3b-109">將三個<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>控制項及兩個<xref:System.Windows.Forms.Button>控制從**工具箱**至表單。</span><span class="sxs-lookup"><span data-stu-id="52b3b-109">Drag three <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls and two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to a form.</span></span>  
  
2.  <span data-ttu-id="52b3b-110">在**程式碼編輯器**，新增`Imports`或`using`陳述式之模組的頂端：</span><span class="sxs-lookup"><span data-stu-id="52b3b-110">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  <span data-ttu-id="52b3b-111">在事件程序中加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="52b3b-111">Add the following code in an event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  <span data-ttu-id="52b3b-112">加入下列程式碼中的`Button1_PreviewKeyDown`事件程序：</span><span class="sxs-lookup"><span data-stu-id="52b3b-112">Add the following code in the `Button1_PreviewKeyDown` event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="52b3b-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="52b3b-113">See Also</span></span>  
 [<span data-ttu-id="52b3b-114">操作說明：使用 OvalShape 和 RectangleShape 控制項繪製圖案</span><span class="sxs-lookup"><span data-stu-id="52b3b-114">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [<span data-ttu-id="52b3b-115">操作說明：使用 LineShape 控制項繪製線條</span><span class="sxs-lookup"><span data-stu-id="52b3b-115">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [<span data-ttu-id="52b3b-116">Line 和 Shape 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="52b3b-116">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
