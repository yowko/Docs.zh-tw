---
title: HOW TO：使用設計工具停用 ToolStripMenuItems
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 9965825458afcd50b29699c3b89ed506078e04d9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338055"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="c93af-102">HOW TO：使用設計工具停用 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="c93af-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="c93af-103">您可以限制，或擴大使用者可能會進行啟用和停用功能表項目，以回應使用者活動的命令。</span><span class="sxs-lookup"><span data-stu-id="c93af-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="c93af-104">依預設會啟用功能表項目，當建立，但這可以透過調整<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="c93af-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="c93af-105">您可以使用這個屬性在設計階段**屬性**視窗或以程式設計方式在程式碼中設定它。</span><span class="sxs-lookup"><span data-stu-id="c93af-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="c93af-106">如需詳細資訊，請參閱[如何：停用 ToolStripMenuItems](how-to-disable-toolstripmenuitems.md)。</span><span class="sxs-lookup"><span data-stu-id="c93af-106">For more information, see [How to: Disable ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c93af-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="c93af-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c93af-108">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="c93af-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c93af-109">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="c93af-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="c93af-110">若要在設計階段停用功能表項目</span><span class="sxs-lookup"><span data-stu-id="c93af-110">To disable a menu item at design time</span></span>  
  
1. <span data-ttu-id="c93af-111">選取表單上的功能表項目，設定<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="c93af-111">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="c93af-112">停用功能表中的第一個或最上層功能表項目，就會停用功能表內包含的所有功能表項目。</span><span class="sxs-lookup"><span data-stu-id="c93af-112">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="c93af-113">同樣地，停用功能表項目具有子功能表項目停用的子功能表項目。</span><span class="sxs-lookup"><span data-stu-id="c93af-113">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="c93af-114">如果使用者無法使用指定的功能表上的所有命令，它會視為良好的程式設計作法，同時隱藏並停用整個功能表中，這帶來全新的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="c93af-114">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="c93af-115">您應該同時隱藏並停用 [] 功能表中，因為單獨隱藏不會防止存取功能表命令，透過攠摝坫。</span><span class="sxs-lookup"><span data-stu-id="c93af-115">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="c93af-116">設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性的最上層的功能表項目`false`隱藏整個功能表。</span><span class="sxs-lookup"><span data-stu-id="c93af-116">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c93af-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c93af-117">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="c93af-118">HOW TO：隱藏 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="c93af-118">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="c93af-119">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="c93af-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
