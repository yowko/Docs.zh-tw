---
title: "如何：啟用 TAB 鍵來移至 ToolStrip 控制項之外"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5f4583a0381af6f0f85f9c2e2aea1d122f5174ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a><span data-ttu-id="6bea5-102">如何：啟用 TAB 鍵來移至 ToolStrip 控制項之外</span><span class="sxs-lookup"><span data-stu-id="6bea5-102">How to: Enable the TAB Key to Move Out of a ToolStrip Control</span></span>
<span data-ttu-id="6bea5-103">使用下列程序可讓使用者按下 TAB 鍵以移出<xref:System.Windows.Forms.ToolStrip>定位順序中的下一個控制項。</span><span class="sxs-lookup"><span data-stu-id="6bea5-103">Use the following procedure to enable the user to press the TAB key to move out of a <xref:System.Windows.Forms.ToolStrip> to the next control in the tab order.</span></span>  
  
 <span data-ttu-id="6bea5-104"><xref:System.Windows.Forms.ToolStrip>接受第一次按下 TAB 鍵，和箭號索引鍵選取項目內<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="6bea5-104">The <xref:System.Windows.Forms.ToolStrip> accepts the first press of the TAB key, and the arrow keys select items within the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="6bea5-105">當使用者在第二次按下 TAB 鍵時，它將使用者帶至下一個控制項定位順序中。</span><span class="sxs-lookup"><span data-stu-id="6bea5-105">When the user presses the TAB key a second time, it takes the user to the next control in the tab order.</span></span>  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a><span data-ttu-id="6bea5-106">若要讓使用者按下 TAB 鍵，從 ToolStrip 移動到下一個控制項</span><span class="sxs-lookup"><span data-stu-id="6bea5-106">To enable the user to press the TAB key to move out of a ToolStrip to the next control</span></span>  
  
-   <span data-ttu-id="6bea5-107">設定<xref:System.Windows.Forms.ToolStrip.TabStop%2A>屬性<xref:System.Windows.Forms.ToolStrip>至`true`。</span><span class="sxs-lookup"><span data-stu-id="6bea5-107">Set the <xref:System.Windows.Forms.ToolStrip.TabStop%2A> property of the <xref:System.Windows.Forms.ToolStrip> to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bea5-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bea5-108">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.TabStop%2A>  
 [<span data-ttu-id="6bea5-109">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="6bea5-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
