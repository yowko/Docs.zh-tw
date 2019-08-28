---
title: HOW TO：停用 ToolStripMenuItems
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
ms.openlocfilehash: f86a2934e799e4604693491dacbecc517d44d810
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046217"
---
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="38abb-102">作法：停用 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="38abb-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="38abb-103">您可以啟用和停用功能表項目以回應使用者活動, 以限制或放寬使用者可能進行的命令。</span><span class="sxs-lookup"><span data-stu-id="38abb-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="38abb-104">建立功能表項目時, 預設會啟用這些專案, 但可透過<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性來調整。</span><span class="sxs-lookup"><span data-stu-id="38abb-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="38abb-105">您可以在設計階段于 [**屬性**] 視窗中操作這個屬性, 或是在程式碼中設定它以程式設計方式。</span><span class="sxs-lookup"><span data-stu-id="38abb-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="38abb-106">以程式設計方式停用功能表項目</span><span class="sxs-lookup"><span data-stu-id="38abb-106">To disable a menu item programmatically</span></span>  
  
- <span data-ttu-id="38abb-107">在您設定功能表項目屬性的方法中, 加入程式碼以將<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性設定為。 `false`</span><span class="sxs-lookup"><span data-stu-id="38abb-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="38abb-108">停用功能表中的第一個或最上層功能表項目, 會隱藏功能表中包含的所有功能表項目, 但不會停用它們。</span><span class="sxs-lookup"><span data-stu-id="38abb-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="38abb-109">同樣地, 停用具有子功能表專案的功能表項目會隱藏子功能表專案, 但不會停用它們。</span><span class="sxs-lookup"><span data-stu-id="38abb-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="38abb-110">如果指定功能表上的所有命令都無法供使用者使用, 就會被視為良好的程式設計實務, 可以隱藏和停用整個功能表, 因為這會呈現全新的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="38abb-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="38abb-111">您應該隱藏和停用功能表, 並停用功能表中的每個專案和子功能表專案, 因為單獨隱藏並不會阻止透過快速鍵存取功能表命令。</span><span class="sxs-lookup"><span data-stu-id="38abb-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="38abb-112">將最上層功能表項目的`false` 屬性設定為,以隱藏整個功能表。<xref:System.Windows.Forms.ToolStripItem.Visible%2A></span><span class="sxs-lookup"><span data-stu-id="38abb-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38abb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38abb-113">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="38abb-114">如何：隱藏 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="38abb-114">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="38abb-115">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="38abb-115">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
