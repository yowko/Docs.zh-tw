---
title: HOW TO：啟用 ContextMenuStrip 控制項的核取邊界和影像邊界
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ShowCheckMargin property [Windows Forms]
- ShowImageMargin property [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: eb584e71-59da-4012-aaca-dbe1c7c7a156
ms.openlocfilehash: bf8440704a7e457d0c987c933cc26e0e12e9565f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591700"
---
# <a name="how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls"></a><span data-ttu-id="5cef3-102">作法：啟用 ContextMenuStrip 控制項的核取邊界和影像邊界</span><span class="sxs-lookup"><span data-stu-id="5cef3-102">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>
<span data-ttu-id="5cef3-103">您可以利用核取記號和自訂影像在您的 <xref:System.Windows.Forms.MenuStrip> 控制項中自訂 <xref:System.Windows.Forms.ToolStripMenuItem> 物件。</span><span class="sxs-lookup"><span data-stu-id="5cef3-103">You can customize the <xref:System.Windows.Forms.ToolStripMenuItem> objects in your <xref:System.Windows.Forms.MenuStrip> control with check marks and custom images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cef3-104">範例</span><span class="sxs-lookup"><span data-stu-id="5cef3-104">Example</span></span>  
 <span data-ttu-id="5cef3-105">下列程式碼範例示範如何建立具有核取記號和自訂影像的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="5cef3-105">The following code example demonstrates how to create menu items that have check marks and custom images.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
 <span data-ttu-id="5cef3-106">當核取記號和自訂映像出現在功能表項目時，設定 <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A?displayProperty=nameWithType> 屬性來指定。</span><span class="sxs-lookup"><span data-stu-id="5cef3-106">Set the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A?displayProperty=nameWithType> properties to specify when check marks and custom images appear in your menu items.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5cef3-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5cef3-107">Compiling the Code</span></span>  
 <span data-ttu-id="5cef3-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="5cef3-108">This example requires:</span></span>  
  
- <span data-ttu-id="5cef3-109">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="5cef3-109">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cef3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cef3-110">See also</span></span>

- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="5cef3-111">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="5cef3-111">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
