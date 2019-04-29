---
title: HOW TO：處理 ContextMenuStrip 開啟事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- context menus [Windows Forms], event handling
- ToolStrip control [Windows Forms]
- event handling [Windows Forms], context menus
- shortcut menus [Windows Forms], event handling
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
ms.openlocfilehash: 3001480959ef90cb31048cbcf70aeff1632979fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941293"
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a><span data-ttu-id="6d063-102">HOW TO：處理 ContextMenuStrip 開啟事件</span><span class="sxs-lookup"><span data-stu-id="6d063-102">How to: Handle the ContextMenuStrip Opening Event</span></span>
<span data-ttu-id="6d063-103">您可以自訂的行為您<xref:System.Windows.Forms.ContextMenuStrip>藉由處理控制項<xref:System.Windows.Forms.ToolStripDropDown.Opening>事件。</span><span class="sxs-lookup"><span data-stu-id="6d063-103">You can customize the behavior of your <xref:System.Windows.Forms.ContextMenuStrip> control by handling the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d063-104">範例</span><span class="sxs-lookup"><span data-stu-id="6d063-104">Example</span></span>  
 <span data-ttu-id="6d063-105">下列程式碼範例示範如何處理<xref:System.Windows.Forms.ToolStripDropDown.Opening>事件。</span><span class="sxs-lookup"><span data-stu-id="6d063-105">The following code example demonstrates how to handle the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span> <span data-ttu-id="6d063-106">事件處理常式中將項目以動態方式加入<xref:System.Windows.Forms.ContextMenuStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="6d063-106">The event handler adds items dynamically to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="6d063-107">完整的程式碼範例，請參閱[How to:以動態方式新增 ToolStrip 項目](how-to-add-toolstrip-items-dynamically.md)。</span><span class="sxs-lookup"><span data-stu-id="6d063-107">For the complete code example, see [How to: Add ToolStrip Items Dynamically](how-to-add-toolstrip-items-dynamically.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 <span data-ttu-id="6d063-108">設定<xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType>屬性設`true`以防止開啟的功能表。</span><span class="sxs-lookup"><span data-stu-id="6d063-108">Set the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> property to `true` to prevent the menu from opening.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d063-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d063-109">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [<span data-ttu-id="6d063-110">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="6d063-110">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
