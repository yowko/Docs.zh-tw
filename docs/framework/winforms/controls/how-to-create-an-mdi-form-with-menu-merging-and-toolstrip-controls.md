---
title: HOW TO：建立具有功能表合併和 ToolStrip 控制項的 MDI 表單
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
ms.openlocfilehash: 0edcc27968c55908cda0e881ed66f83323316711
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591313"
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="ca11f-102">作法：建立具有功能表合併和 ToolStrip 控制項的 MDI 表單</span><span class="sxs-lookup"><span data-stu-id="ca11f-102">How to: Create an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="ca11f-103"><xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間支援多重文件介面 (MDI) 應用程式，而 <xref:System.Windows.Forms.MenuStrip> 控制項則支援功能表合併。</span><span class="sxs-lookup"><span data-stu-id="ca11f-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="ca11f-104">MDI 表單也可以由 <xref:System.Windows.Forms.ToolStrip> 控制項建立。</span><span class="sxs-lookup"><span data-stu-id="ca11f-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="ca11f-105">沒有這項功能在 Visual Studio 中的廣泛支援。</span><span class="sxs-lookup"><span data-stu-id="ca11f-105">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="ca11f-106">另請參閱[逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="ca11f-106">Also see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca11f-107">範例</span><span class="sxs-lookup"><span data-stu-id="ca11f-107">Example</span></span>  
 <span data-ttu-id="ca11f-108">下列程式碼範例示範如何在 MDI 表單上使用 <xref:System.Windows.Forms.ToolStripPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="ca11f-108">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="ca11f-109">這個表單也支援子功能表的功能表合併。</span><span class="sxs-lookup"><span data-stu-id="ca11f-109">The form also supports menu merging with child menus.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca11f-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ca11f-110">Compiling the Code</span></span>  
 <span data-ttu-id="ca11f-111">這個程式碼範例需要：</span><span class="sxs-lookup"><span data-stu-id="ca11f-111">This code example requires:</span></span>  
  
- <span data-ttu-id="ca11f-112">System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="ca11f-112">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca11f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca11f-113">See also</span></span>

- [<span data-ttu-id="ca11f-114">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="ca11f-114">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
