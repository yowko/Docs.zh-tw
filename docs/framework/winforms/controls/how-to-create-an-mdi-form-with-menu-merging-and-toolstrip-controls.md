---
title: HOW TO：使用功能表合併和 ToolStrip 控制項建立 MDI 表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
ms.openlocfilehash: 2a6b8669717e8f07d9c7acd624e77a5c35a4eb7e
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583455"
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="78065-102">HOW TO：使用功能表合併和 ToolStrip 控制項建立 MDI 表單</span><span class="sxs-lookup"><span data-stu-id="78065-102">How to: Create an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="78065-103">
  <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間支援多重文件介面 (MDI) 應用程式，而 <xref:System.Windows.Forms.MenuStrip> 控制項則支援功能表合併。</span><span class="sxs-lookup"><span data-stu-id="78065-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="78065-104">MDI 表單也可以由 <xref:System.Windows.Forms.ToolStrip> 控制項建立。</span><span class="sxs-lookup"><span data-stu-id="78065-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="78065-105">沒有這項功能在 Visual Studio 中的廣泛支援。</span><span class="sxs-lookup"><span data-stu-id="78065-105">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="78065-106">另請參閱[逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="78065-106">Also see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="78065-107">範例</span><span class="sxs-lookup"><span data-stu-id="78065-107">Example</span></span>  
 <span data-ttu-id="78065-108">下列程式碼範例示範如何在 MDI 表單上使用 <xref:System.Windows.Forms.ToolStripPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="78065-108">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="78065-109">這個表單也支援子功能表的功能表合併。</span><span class="sxs-lookup"><span data-stu-id="78065-109">The form also supports menu merging with child menus.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="78065-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="78065-110">Compiling the Code</span></span>  
 <span data-ttu-id="78065-111">這個程式碼範例需要：</span><span class="sxs-lookup"><span data-stu-id="78065-111">This code example requires:</span></span>  
  
-   <span data-ttu-id="78065-112">System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="78065-112">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="78065-113">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="78065-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="78065-114">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="78065-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78065-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78065-115">See also</span></span>
- [<span data-ttu-id="78065-116">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="78065-116">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
