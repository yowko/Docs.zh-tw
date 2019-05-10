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
ms.openlocfilehash: ec74528ecb3d2ca1fca78c3a81e71a0093843b4d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651650"
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a><span data-ttu-id="b8f8d-102">HOW TO：實作自訂的 ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="b8f8d-102">How to: Implement a Custom ToolStripRenderer</span></span>
<span data-ttu-id="b8f8d-103">您可以實作衍生自 <xref:System.Windows.Forms.ToolStripRenderer> 的類別，自訂 <xref:System.Windows.Forms.ToolStrip> 控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="b8f8d-103">You can customize the appearance of a <xref:System.Windows.Forms.ToolStrip> control by implementing a class that derives from <xref:System.Windows.Forms.ToolStripRenderer>.</span></span> <span data-ttu-id="b8f8d-104">這可讓您彈性地建立與 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 和 <xref:System.Windows.Forms.ToolStripSystemRenderer> 類別所提供外觀不同的外觀。</span><span class="sxs-lookup"><span data-stu-id="b8f8d-104">This gives you the flexibility to create an appearance that differs from the appearance provided the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> and <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8f8d-105">範例</span><span class="sxs-lookup"><span data-stu-id="b8f8d-105">Example</span></span>  
 <span data-ttu-id="b8f8d-106">下列程式碼範例示範如何實作自訂 <xref:System.Windows.Forms.ToolStripRenderer> 類別。</span><span class="sxs-lookup"><span data-stu-id="b8f8d-106">The following code example demonstrates how to implement a custom <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="b8f8d-107">在此範例中，`GridStrip` 控制項會實作滑動並排顯示拼圖，這可讓使用者移動表格配置中的並排顯示，以形成影像。</span><span class="sxs-lookup"><span data-stu-id="b8f8d-107">In this example, the `GridStrip` control implements a sliding-tile puzzle, which allows the user to move tiles in a table layout to form an image.</span></span> <span data-ttu-id="b8f8d-108">自訂 <xref:System.Windows.Forms.ToolStrip> 控制項會以格線版面配置排列其 <xref:System.Windows.Forms.ToolStripButton> 控制項。</span><span class="sxs-lookup"><span data-stu-id="b8f8d-108">A custom <xref:System.Windows.Forms.ToolStrip> control arranges its <xref:System.Windows.Forms.ToolStripButton> controls in a grid layout.</span></span> <span data-ttu-id="b8f8d-109">版面配置包含一個空資料格，其中使用者可以使用拖放作業滑動相鄰的並排顯示。</span><span class="sxs-lookup"><span data-stu-id="b8f8d-109">The layout contains one empty cell, into which the user can slide an adjacent tile by using a drag-and-drop operation.</span></span> <span data-ttu-id="b8f8d-110">使用者可以移動的並排顯示會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="b8f8d-110">Tiles that the user can move are highlighted.</span></span>  
  
 <span data-ttu-id="b8f8d-111"> `GridStripRenderer` 類別自訂的三個層面 `GridStrip` 控制項的外觀：</span><span class="sxs-lookup"><span data-stu-id="b8f8d-111">The `GridStripRenderer` class customizes three aspects of the `GridStrip` control's appearance:</span></span>  
  
- <span data-ttu-id="b8f8d-112">`GridStrip` 框線</span><span class="sxs-lookup"><span data-stu-id="b8f8d-112">`GridStrip` border</span></span>  
  
- <span data-ttu-id="b8f8d-113"><xref:System.Windows.Forms.ToolStripButton> 框線</span><span class="sxs-lookup"><span data-stu-id="b8f8d-113"><xref:System.Windows.Forms.ToolStripButton> border</span></span>  
  
- <span data-ttu-id="b8f8d-114"><xref:System.Windows.Forms.ToolStripButton> 映像</span><span class="sxs-lookup"><span data-stu-id="b8f8d-114"><xref:System.Windows.Forms.ToolStripButton> image</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b8f8d-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b8f8d-115">Compiling the Code</span></span>  
 <span data-ttu-id="b8f8d-116">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b8f8d-116">This example requires:</span></span>  
  
- <span data-ttu-id="b8f8d-117">System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="b8f8d-117">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b8f8d-118">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="b8f8d-118">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b8f8d-119">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="b8f8d-119">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f8d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8f8d-120">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="b8f8d-121">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="b8f8d-121">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
