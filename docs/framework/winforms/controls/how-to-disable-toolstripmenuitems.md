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
ms.openlocfilehash: 3c18935239a4355d5416a0a79d0fa9f5c504cc7e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720208"
---
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="1cf23-102">HOW TO：停用 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="1cf23-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="1cf23-103">您可以限制，或擴大使用者可能會進行啟用和停用功能表項目，以回應使用者活動的命令。</span><span class="sxs-lookup"><span data-stu-id="1cf23-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="1cf23-104">依預設會啟用功能表項目，當建立，但這可以透過調整<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="1cf23-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="1cf23-105">您可以使用這個屬性在設計階段**屬性**視窗或以程式設計方式在程式碼中設定它。</span><span class="sxs-lookup"><span data-stu-id="1cf23-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="1cf23-106">若要以程式設計方式停用功能表項目</span><span class="sxs-lookup"><span data-stu-id="1cf23-106">To disable a menu item programmatically</span></span>  
  
-   <span data-ttu-id="1cf23-107">在方法中您用來設定功能表項目的屬性，加入程式碼以設定<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="1cf23-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
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
    >  <span data-ttu-id="1cf23-108">停用功能表中的第一個或最上層功能表項目會隱藏在功能表中，包含的所有功能表項目，但不會不停用它們。</span><span class="sxs-lookup"><span data-stu-id="1cf23-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="1cf23-109">同樣地，停用功能表項目具有子功能表項目就會隱藏子功能表項目，但不會不停用它們。</span><span class="sxs-lookup"><span data-stu-id="1cf23-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="1cf23-110">如果使用者無法使用指定的功能表上的所有命令，它會視為良好的程式設計作法，同時隱藏並停用整個功能表中，這帶來全新的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="1cf23-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="1cf23-111">您應該隱藏及停用功能表，並停用每個項目和子功能表項目在功能表中，因為單獨隱藏並不會防止攠摝坫透過功能表命令的存取。</span><span class="sxs-lookup"><span data-stu-id="1cf23-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="1cf23-112">設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性的最上層的功能表項目`false`隱藏整個功能表。</span><span class="sxs-lookup"><span data-stu-id="1cf23-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf23-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cf23-113">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="1cf23-114">如何：隱藏 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="1cf23-114">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="1cf23-115">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="1cf23-115">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
