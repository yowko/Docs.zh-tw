---
title: "如何：處理 ContextMenuStrip Opening 事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5de244abd35c83bce329882d679df8303ef3a833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a><span data-ttu-id="715c3-102">如何：處理 ContextMenuStrip Opening 事件</span><span class="sxs-lookup"><span data-stu-id="715c3-102">How to: Handle the ContextMenuStrip Opening Event</span></span>
<span data-ttu-id="715c3-103">您可以自訂的行為您<xref:System.Windows.Forms.ContextMenuStrip>處理控制項<xref:System.Windows.Forms.ToolStripDropDown.Opening>事件。</span><span class="sxs-lookup"><span data-stu-id="715c3-103">You can customize the behavior of your <xref:System.Windows.Forms.ContextMenuStrip> control by handling the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="715c3-104">範例</span><span class="sxs-lookup"><span data-stu-id="715c3-104">Example</span></span>  
 <span data-ttu-id="715c3-105">下列程式碼範例示範如何處理<xref:System.Windows.Forms.ToolStripDropDown.Opening>事件。</span><span class="sxs-lookup"><span data-stu-id="715c3-105">The following code example demonstrates how to handle the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span> <span data-ttu-id="715c3-106">此事件處理常式將項目動態加入<xref:System.Windows.Forms.ContextMenuStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="715c3-106">The event handler adds items dynamically to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="715c3-107">完整的程式碼範例，請參閱[如何： 加入 ToolStrip 項目在動態](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md)。</span><span class="sxs-lookup"><span data-stu-id="715c3-107">For the complete code example, see [How to: Add ToolStrip Items Dynamically](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 <span data-ttu-id="715c3-108">設定<xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType>屬性`true`以防止開啟功能表。</span><span class="sxs-lookup"><span data-stu-id="715c3-108">Set the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> property to `true` to prevent the menu from opening.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="715c3-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="715c3-109">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [<span data-ttu-id="715c3-110">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="715c3-110">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
