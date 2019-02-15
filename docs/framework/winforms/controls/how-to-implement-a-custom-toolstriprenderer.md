---
title: HOW TO：實作自訂的 ToolStripRenderer
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
ms.openlocfilehash: 4e471b2a02111bf33bb11b62c8311ac4dc214d46
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261331"
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a><span data-ttu-id="cf394-102">HOW TO：實作自訂的 ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="cf394-102">How to: Implement a Custom ToolStripRenderer</span></span>
<span data-ttu-id="cf394-103">您可以實作衍生自 <xref:System.Windows.Forms.ToolStripRenderer> 的類別，自訂 <xref:System.Windows.Forms.ToolStrip> 控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="cf394-103">You can customize the appearance of a <xref:System.Windows.Forms.ToolStrip> control by implementing a class that derives from <xref:System.Windows.Forms.ToolStripRenderer>.</span></span> <span data-ttu-id="cf394-104">這可讓您彈性地建立與 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 和 <xref:System.Windows.Forms.ToolStripSystemRenderer> 類別所提供外觀不同的外觀。</span><span class="sxs-lookup"><span data-stu-id="cf394-104">This gives you the flexibility to create an appearance that differs from the appearance provided the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> and <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf394-105">範例</span><span class="sxs-lookup"><span data-stu-id="cf394-105">Example</span></span>  
 <span data-ttu-id="cf394-106">下列程式碼範例示範如何實作自訂 <xref:System.Windows.Forms.ToolStripRenderer> 類別。</span><span class="sxs-lookup"><span data-stu-id="cf394-106">The following code example demonstrates how to implement a custom <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="cf394-107">在此範例中，`GridStrip` 控制項會實作滑動並排顯示拼圖，這可讓使用者移動表格配置中的並排顯示，以形成影像。</span><span class="sxs-lookup"><span data-stu-id="cf394-107">In this example, the `GridStrip` control implements a sliding-tile puzzle, which allows the user to move tiles in a table layout to form an image.</span></span> <span data-ttu-id="cf394-108">自訂 <xref:System.Windows.Forms.ToolStrip> 控制項會以格線版面配置排列其 <xref:System.Windows.Forms.ToolStripButton> 控制項。</span><span class="sxs-lookup"><span data-stu-id="cf394-108">A custom <xref:System.Windows.Forms.ToolStrip> control arranges its <xref:System.Windows.Forms.ToolStripButton> controls in a grid layout.</span></span> <span data-ttu-id="cf394-109">版面配置包含一個空資料格，其中使用者可以使用拖放作業滑動相鄰的並排顯示。</span><span class="sxs-lookup"><span data-stu-id="cf394-109">The layout contains one empty cell, into which the user can slide an adjacent tile by using a drag-and-drop operation.</span></span> <span data-ttu-id="cf394-110">使用者可以移動的並排顯示會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="cf394-110">Tiles that the user can move are highlighted.</span></span>  
  
 <span data-ttu-id="cf394-111"> `GridStripRenderer` 類別自訂的三個層面 `GridStrip` 控制項的外觀：</span><span class="sxs-lookup"><span data-stu-id="cf394-111">The `GridStripRenderer` class customizes three aspects of the `GridStrip` control's appearance:</span></span>  
  
-   <span data-ttu-id="cf394-112">`GridStrip` 框線</span><span class="sxs-lookup"><span data-stu-id="cf394-112">`GridStrip` border</span></span>  
  
-   <span data-ttu-id="cf394-113"><xref:System.Windows.Forms.ToolStripButton> 框線</span><span class="sxs-lookup"><span data-stu-id="cf394-113"><xref:System.Windows.Forms.ToolStripButton> border</span></span>  
  
-   <span data-ttu-id="cf394-114"><xref:System.Windows.Forms.ToolStripButton> 影像</span><span class="sxs-lookup"><span data-stu-id="cf394-114"><xref:System.Windows.Forms.ToolStripButton> image</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cf394-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="cf394-115">Compiling the Code</span></span>  
 <span data-ttu-id="cf394-116">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="cf394-116">This example requires:</span></span>  
  
-   <span data-ttu-id="cf394-117">System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="cf394-117">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="cf394-118">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="cf394-118">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="cf394-119">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="cf394-119">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf394-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf394-120">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="cf394-121">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="cf394-121">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
