---
title: 作法：使用設計工具停用 ToolStripMenuItems
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: fd80a6543c83ae957cd9c51b068d0702559f0925
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040262"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="56e9d-102">作法：使用設計工具停用 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="56e9d-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="56e9d-103">您可以啟用和停用功能表項目以回應使用者活動, 以限制或放寬使用者可能進行的命令。</span><span class="sxs-lookup"><span data-stu-id="56e9d-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="56e9d-104">建立功能表項目時, 預設會啟用這些專案, 但可透過<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性來調整。</span><span class="sxs-lookup"><span data-stu-id="56e9d-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="56e9d-105">您可以在設計階段于 [**屬性**] 視窗中操作這個屬性, 或是在程式碼中設定它以程式設計方式。</span><span class="sxs-lookup"><span data-stu-id="56e9d-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="56e9d-106">如需詳細資訊，請參閱[如何：停用](how-to-disable-toolstripmenuitems.md)ToolStripMenuItems。</span><span class="sxs-lookup"><span data-stu-id="56e9d-106">For more information, see [How to: Disable ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span></span>

## <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="56e9d-107">若要在設計階段停用功能表項目</span><span class="sxs-lookup"><span data-stu-id="56e9d-107">To disable a menu item at design time</span></span>

1. <span data-ttu-id="56e9d-108">在表單上選取功能表項目時, 將<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性設定為。 `false`</span><span class="sxs-lookup"><span data-stu-id="56e9d-108">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>

    > [!TIP]
    >  <span data-ttu-id="56e9d-109">停用功能表中的第一個或最上層功能表項目, 會停用功能表中包含的所有功能表項目。</span><span class="sxs-lookup"><span data-stu-id="56e9d-109">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="56e9d-110">同樣地, 停用具有子功能表專案的功能表項目會停用子功能表專案。</span><span class="sxs-lookup"><span data-stu-id="56e9d-110">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="56e9d-111">如果指定功能表上的所有命令都無法供使用者使用, 就會被視為良好的程式設計實務, 可以隱藏和停用整個功能表, 因為這會呈現全新的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="56e9d-111">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="56e9d-112">您應該隱藏和停用功能表, 因為單獨隱藏並不會阻止透過快速鍵存取功能表命令。</span><span class="sxs-lookup"><span data-stu-id="56e9d-112">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="56e9d-113">將最上層功能表項目的`false` 屬性設定為,以隱藏整個功能表。<xref:System.Windows.Forms.ToolStripItem.Visible%2A></span><span class="sxs-lookup"><span data-stu-id="56e9d-113">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="56e9d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56e9d-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="56e9d-115">如何：隱藏 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="56e9d-115">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="56e9d-116">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="56e9d-116">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
