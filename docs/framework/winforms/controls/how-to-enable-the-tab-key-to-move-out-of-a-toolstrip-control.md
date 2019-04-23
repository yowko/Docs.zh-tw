---
title: HOW TO：讓 TAB 鍵移至 ToolStrip 控制項之外
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: d4de7345a4e3ce122c4e1fc0a92f09b447204eb6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113161"
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a><span data-ttu-id="416d5-102">HOW TO：讓 TAB 鍵移至 ToolStrip 控制項之外</span><span class="sxs-lookup"><span data-stu-id="416d5-102">How to: Enable the TAB Key to Move Out of a ToolStrip Control</span></span>
<span data-ttu-id="416d5-103">使用下列程序以啟用使用者按下 TAB 鍵來移出<xref:System.Windows.Forms.ToolStrip>定位順序中的下一個控制項。</span><span class="sxs-lookup"><span data-stu-id="416d5-103">Use the following procedure to enable the user to press the TAB key to move out of a <xref:System.Windows.Forms.ToolStrip> to the next control in the tab order.</span></span>  
  
 <span data-ttu-id="416d5-104"><xref:System.Windows.Forms.ToolStrip>接受第一次按下 TAB 鍵和箭號索引鍵選取項目內<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="416d5-104">The <xref:System.Windows.Forms.ToolStrip> accepts the first press of the TAB key, and the arrow keys select items within the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="416d5-105">當使用者按下 TAB 鍵一次時，它將使用者帶到下一個控制項定位順序中。</span><span class="sxs-lookup"><span data-stu-id="416d5-105">When the user presses the TAB key a second time, it takes the user to the next control in the tab order.</span></span>  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a><span data-ttu-id="416d5-106">若要啟用使用者按下 TAB 鍵來移出 ToolStrip 以的下一個控制項</span><span class="sxs-lookup"><span data-stu-id="416d5-106">To enable the user to press the TAB key to move out of a ToolStrip to the next control</span></span>  
  
-   <span data-ttu-id="416d5-107">設定<xref:System.Windows.Forms.ToolStrip.TabStop%2A>的屬性<xref:System.Windows.Forms.ToolStrip>至`true`。</span><span class="sxs-lookup"><span data-stu-id="416d5-107">Set the <xref:System.Windows.Forms.ToolStrip.TabStop%2A> property of the <xref:System.Windows.Forms.ToolStrip> to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="416d5-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="416d5-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.TabStop%2A>
- [<span data-ttu-id="416d5-109">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="416d5-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
