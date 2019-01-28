---
title: HOW TO：新增和移除使用 Windows Form TabControl 使用設計工具的索引標籤
ms.date: 03/30/2017
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabPage control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 480633db-413a-45d2-9c8f-0427cc13adbe
ms.openlocfilehash: 0bc766091ce6927a657535172ce4ca053325868e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683699"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="e5bd8-102">HOW TO：新增和移除使用 Windows Form TabControl 使用設計工具的索引標籤</span><span class="sxs-lookup"><span data-stu-id="e5bd8-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="e5bd8-103">當您將<xref:System.Windows.Forms.TabControl>控制項在表單中，它必須包含兩個索引標籤預設。</span><span class="sxs-lookup"><span data-stu-id="e5bd8-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="e5bd8-104">您可以新增或移除使用設計工具索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e5bd8-104">You can add or remove tabs using the designer.</span></span>  
  
 <span data-ttu-id="e5bd8-105">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.TabControl>控制項。</span><span class="sxs-lookup"><span data-stu-id="e5bd8-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="e5bd8-106">如需這類專案的設定資訊，請參閱[How to:建立 Windows 應用程式專案](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to:將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="e5bd8-106">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5bd8-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="e5bd8-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e5bd8-108">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="e5bd8-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e5bd8-109">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="e5bd8-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="e5bd8-110">若要新增或移除使用設計工具索引標籤</span><span class="sxs-lookup"><span data-stu-id="e5bd8-110">To add or remove a tab using the designer</span></span>  
  
-   <span data-ttu-id="e5bd8-111">在控制項的智慧標籤上，按一下**加入索引標籤**或**移除索引標籤**</span><span class="sxs-lookup"><span data-stu-id="e5bd8-111">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>  
  
     <span data-ttu-id="e5bd8-112">-或-</span><span class="sxs-lookup"><span data-stu-id="e5bd8-112">-or-</span></span>  
  
     <span data-ttu-id="e5bd8-113">在 [**屬性**] 視窗中，按一下**省略符號** 按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.TabControl.TabPages%2A>屬性，以開啟**TabPage 集合編輯器**。</span><span class="sxs-lookup"><span data-stu-id="e5bd8-113">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="e5bd8-114">按一下 [**新增**或是**移除**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e5bd8-114">Click the **Add** or **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5bd8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5bd8-115">See also</span></span>
- [<span data-ttu-id="e5bd8-116">TabControl 控制項</span><span class="sxs-lookup"><span data-stu-id="e5bd8-116">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="e5bd8-117">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e5bd8-117">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="e5bd8-118">如何：將控制項加入索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="e5bd8-118">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="e5bd8-119">如何：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="e5bd8-119">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)
- [<span data-ttu-id="e5bd8-120">如何：變更 Windows Form TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="e5bd8-120">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
