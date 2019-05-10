---
title: HOW TO：偵測滑鼠指標何時移至 ToolStripItem
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: f01a9acb3a566be40d65fb075c8487d4e9cb6e73
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623647"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="02f84-102">HOW TO：偵測滑鼠指標何時移至 ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="02f84-102">How to: Detect When the Mouse Pointer Is Over a ToolStripItem</span></span>
<span data-ttu-id="02f84-103">使用下列程序來偵測當滑鼠指標移<xref:System.Windows.Forms.ToolStripItem>。</span><span class="sxs-lookup"><span data-stu-id="02f84-103">Use the following procedure to detect when the mouse pointer is over a <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="02f84-104">偵測當滑鼠指標 toolstripitem 上時</span><span class="sxs-lookup"><span data-stu-id="02f84-104">To detect when the pointer is over a ToolStripItem</span></span>  
  
- <span data-ttu-id="02f84-105">使用<xref:System.Windows.Forms.ToolStripItem.Selected%2A>屬性中的項目<xref:System.Windows.Forms.ToolStripItem.CanSelect%2A>是`true`。</span><span class="sxs-lookup"><span data-stu-id="02f84-105">Use the <xref:System.Windows.Forms.ToolStripItem.Selected%2A> property for items in which <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> is `true`.</span></span>  
  
     <span data-ttu-id="02f84-106">這會讓您不需要同步處理<xref:System.Windows.Forms.ToolStripItem.MouseEnter>和<xref:System.Windows.Forms.ToolStripItem.MouseLeave>事件。</span><span class="sxs-lookup"><span data-stu-id="02f84-106">This will prevent you from having to synchronize the <xref:System.Windows.Forms.ToolStripItem.MouseEnter> and <xref:System.Windows.Forms.ToolStripItem.MouseLeave> events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f84-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02f84-107">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [<span data-ttu-id="02f84-108">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="02f84-108">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
