---
title: 作法：使用設計工具隱藏 ToolStripMenuItems
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 968d34a5f79d469ef62beaa8ac96742d73391b22
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039750"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="8715f-102">HOW TO：使用設計工具隱藏 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="8715f-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="8715f-103">隱藏功能表項目是控制應用程式的使用者介面 (UI) 和限制使用者命令的一種方式。</span><span class="sxs-lookup"><span data-stu-id="8715f-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="8715f-104">當所有功能表項目都無法使用時, 通常會想要隱藏整個功能表。</span><span class="sxs-lookup"><span data-stu-id="8715f-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="8715f-105">這會為使用者提供較少的分散注意力。</span><span class="sxs-lookup"><span data-stu-id="8715f-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="8715f-106">此外, 您可能會想要隱藏和停用功能表或功能表項目, 因為單獨隱藏並不會防止使用者使用快速鍵來存取功能表命令。</span><span class="sxs-lookup"><span data-stu-id="8715f-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="8715f-107">如需停用功能表項目的詳細資訊[, 請參閱如何:使用設計](how-to-disable-toolstripmenuitems-using-the-designer.md)工具停用 ToolStripMenuItems。</span><span class="sxs-lookup"><span data-stu-id="8715f-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="8715f-108">隱藏最上層功能表及其子功能表專案</span><span class="sxs-lookup"><span data-stu-id="8715f-108">To hide a top-level menu and its submenu items</span></span>

1. <span data-ttu-id="8715f-109">選取最上層功能表項目, 並將其<xref:System.Windows.Forms.ToolStripItem.Visible%2A>或<xref:System.Windows.Forms.ToolStripItem.Available%2A>屬性設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="8715f-109">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>

     <span data-ttu-id="8715f-110">當您隱藏最上層功能表項目時, 也會隱藏該功能表中的所有功能表項目。</span><span class="sxs-lookup"><span data-stu-id="8715f-110">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="8715f-111">如果您在 [設定<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStripItem.Visible%2A>為`false`] 後按一下 [以外的位置], 整個最上層功能表項目和其子功能表專案就會從您的表單中消失, 因此會顯示動作的執行時間效果。</span><span class="sxs-lookup"><span data-stu-id="8715f-111">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="8715f-112">若要在設計階段顯示隱藏的最上層功能表項目, 請按一下<xref:System.Windows.Forms.MenuStrip> **元件**匣中的、[**檔大綱**] 或屬性方格頂端的。</span><span class="sxs-lookup"><span data-stu-id="8715f-112">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>

> [!NOTE]
>  <span data-ttu-id="8715f-113">除了合併案例中的多重文件介面 (MDI) 子功能表以外, 您幾乎不會隱藏整個功能表。</span><span class="sxs-lookup"><span data-stu-id="8715f-113">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>

## <a name="to-hide-a-submenu-item"></a><span data-ttu-id="8715f-114">若要隱藏子功能表專案</span><span class="sxs-lookup"><span data-stu-id="8715f-114">To hide a submenu item</span></span>

1. <span data-ttu-id="8715f-115">選取子功能表專案, 並將<xref:System.Windows.Forms.ToolStripItem.Visible%2A>其屬性`false`設定為。</span><span class="sxs-lookup"><span data-stu-id="8715f-115">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>

     <span data-ttu-id="8715f-116">當您隱藏子功能表專案時, 它在設計階段仍會顯示在您的表單上, 讓您可以輕鬆地選取它以進行進一步的工作。</span><span class="sxs-lookup"><span data-stu-id="8715f-116">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="8715f-117">它實際上會在執行時間隱藏。</span><span class="sxs-lookup"><span data-stu-id="8715f-117">It will actually be hidden at run time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8715f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8715f-118">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [<span data-ttu-id="8715f-119">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="8715f-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="8715f-120">如何：使用設計工具停用 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="8715f-120">How to: Disable ToolStripMenuItems Using the Designer</span></span>](how-to-disable-toolstripmenuitems-using-the-designer.md)
