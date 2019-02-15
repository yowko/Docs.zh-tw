---
title: HOW TO：將按鈕加入至 ToolBar 控制項使用設計工具
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: e4332842a082f7359179dbf4d7539b42bbceb6fc
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305684"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a><span data-ttu-id="a68cd-102">HOW TO：將按鈕加入至 ToolBar 控制項使用設計工具</span><span class="sxs-lookup"><span data-stu-id="a68cd-102">How to: Add Buttons to a ToolBar Control Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="a68cd-103">
  <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="a68cd-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="a68cd-104">不可或缺的一部分<xref:System.Windows.Forms.ToolBar>控制項是您加入的按鈕。</span><span class="sxs-lookup"><span data-stu-id="a68cd-104">An integral part of the <xref:System.Windows.Forms.ToolBar> control is the buttons you add to it.</span></span> <span data-ttu-id="a68cd-105">這些可以用來讓您輕鬆存取功能表命令，或者，或者，他們可以放在您的應用程式的命令公開給您的使用者功能表結構中所沒有的使用者介面的另一個區域。</span><span class="sxs-lookup"><span data-stu-id="a68cd-105">These can be used to provide easy access to menu commands or, alternately, they can be placed in another area of the user interface of your application to expose commands to your users that are not available in the menu structure.</span></span>  
  
 <span data-ttu-id="a68cd-106">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="a68cd-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control.</span></span> <span data-ttu-id="a68cd-107">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="a68cd-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a68cd-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="a68cd-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a68cd-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="a68cd-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a68cd-110">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="a68cd-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-buttons-at-design-time"></a><span data-ttu-id="a68cd-111">若要在設計階段加入按鈕</span><span class="sxs-lookup"><span data-stu-id="a68cd-111">To add buttons at design time</span></span>  
  
1.  <span data-ttu-id="a68cd-112">選取 <xref:System.Windows.Forms.ToolBar> 控制項。</span><span class="sxs-lookup"><span data-stu-id="a68cd-112">Select the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2.  <span data-ttu-id="a68cd-113">在 [**屬性**] 視窗中，按一下<xref:System.Windows.Forms.ToolBar.Buttons%2A>屬性，以選取它，然後按一下**省略符號**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕，即可開啟**ToolBarButton 集合編輯器**。</span><span class="sxs-lookup"><span data-stu-id="a68cd-113">In the **Properties** window, click the <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it and click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="a68cd-114">使用**新增**並**移除**按鈕來新增和移除按鈕等，從<xref:System.Windows.Forms.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="a68cd-114">Use the **Add** and **Remove** buttons to add and remove buttons from the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
4.  <span data-ttu-id="a68cd-115">設定個別的按鈕中的屬性**屬性**出現在編輯器的右邊窗格中的視窗。</span><span class="sxs-lookup"><span data-stu-id="a68cd-115">Configure the properties of the individual buttons in the **Properties** window that appears in the pane on the right side of the editor.</span></span> <span data-ttu-id="a68cd-116">下表顯示一些要考慮的重要屬性。</span><span class="sxs-lookup"><span data-stu-id="a68cd-116">The following table shows some important properties to consider.</span></span>  
  
    |<span data-ttu-id="a68cd-117">屬性</span><span class="sxs-lookup"><span data-stu-id="a68cd-117">Property</span></span>|<span data-ttu-id="a68cd-118">描述</span><span class="sxs-lookup"><span data-stu-id="a68cd-118">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|<span data-ttu-id="a68cd-119">設定要顯示在下拉式工具列按鈕的功能表。</span><span class="sxs-lookup"><span data-stu-id="a68cd-119">Sets the menu to be displayed in the drop-down toolbar button.</span></span> <span data-ttu-id="a68cd-120">工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設為<xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>。</span><span class="sxs-lookup"><span data-stu-id="a68cd-120">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>.</span></span> <span data-ttu-id="a68cd-121">這個屬性可接受的執行個體<xref:System.Windows.Forms.ContextMenu>做為參考的類別。</span><span class="sxs-lookup"><span data-stu-id="a68cd-121">This property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|<span data-ttu-id="a68cd-122">設定是否部分壓下切換式工具列按鈕。</span><span class="sxs-lookup"><span data-stu-id="a68cd-122">Sets whether a toggle-style toolbar button is partially pushed.</span></span> <span data-ttu-id="a68cd-123">工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設為<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>。</span><span class="sxs-lookup"><span data-stu-id="a68cd-123">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|<span data-ttu-id="a68cd-124">設定是否切換式工具列按鈕目前為按下狀態。</span><span class="sxs-lookup"><span data-stu-id="a68cd-124">Sets whether a toggle-style toolbar button is currently in the pushed state.</span></span> <span data-ttu-id="a68cd-125">工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設為<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>或<xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>。</span><span class="sxs-lookup"><span data-stu-id="a68cd-125">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> or <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|<span data-ttu-id="a68cd-126">將工具列按鈕的樣式設定。</span><span class="sxs-lookup"><span data-stu-id="a68cd-126">Sets the style of the toolbar button.</span></span> <span data-ttu-id="a68cd-127">必須是其中一個值在<xref:System.Windows.Forms.ToolBarButtonStyle>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="a68cd-127">Must be one of the values in the <xref:System.Windows.Forms.ToolBarButtonStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|<span data-ttu-id="a68cd-128">按鈕所顯示的文字字串。</span><span class="sxs-lookup"><span data-stu-id="a68cd-128">The text string displayed by the button.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|<span data-ttu-id="a68cd-129">會顯示為按鈕的工具提示文字。</span><span class="sxs-lookup"><span data-stu-id="a68cd-129">The text that appears as a ToolTip for the button.</span></span>|  
  
5.  <span data-ttu-id="a68cd-130">按一下 **確定**關閉對話方塊並建立指定的面板。</span><span class="sxs-lookup"><span data-stu-id="a68cd-130">Click **OK** to close the dialog box and create the panels you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a68cd-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a68cd-131">See also</span></span>
- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="a68cd-132">如何：定義工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="a68cd-132">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="a68cd-133">如何：觸發程序的工具列按鈕的功能表事件</span><span class="sxs-lookup"><span data-stu-id="a68cd-133">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="a68cd-134">工具列控制項概觀</span><span class="sxs-lookup"><span data-stu-id="a68cd-134">ToolBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)
- [<span data-ttu-id="a68cd-135">ToolBar 控制項</span><span class="sxs-lookup"><span data-stu-id="a68cd-135">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
