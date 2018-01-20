---
title: "如何：使用設計工具在工具列控制項中加入按鈕"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5339d946f771b7ba187813dd67860aaa63a21eb3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a><span data-ttu-id="644fe-102">如何：使用設計工具在工具列控制項中加入按鈕</span><span class="sxs-lookup"><span data-stu-id="644fe-102">How to: Add Buttons to a ToolBar Control Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="644fe-103"><xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="644fe-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="644fe-104">不可或缺的一部分<xref:System.Windows.Forms.ToolBar>控制項是您加入的按鈕。</span><span class="sxs-lookup"><span data-stu-id="644fe-104">An integral part of the <xref:System.Windows.Forms.ToolBar> control is the buttons you add to it.</span></span> <span data-ttu-id="644fe-105">這些可以用來讓您輕鬆存取功能表命令或者，或者，也可置於另一個區域中的命令公開給您的使用者無法使用功能表結構中的應用程式的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="644fe-105">These can be used to provide easy access to menu commands or, alternately, they can be placed in another area of the user interface of your application to expose commands to your users that are not available in the menu structure.</span></span>  
  
 <span data-ttu-id="644fe-106">下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="644fe-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control.</span></span> <span data-ttu-id="644fe-107">設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="644fe-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="644fe-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="644fe-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="644fe-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="644fe-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="644fe-110">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="644fe-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-buttons-at-design-time"></a><span data-ttu-id="644fe-111">若要在設計階段加入按鈕</span><span class="sxs-lookup"><span data-stu-id="644fe-111">To add buttons at design time</span></span>  
  
1.  <span data-ttu-id="644fe-112">選取 <xref:System.Windows.Forms.ToolBar> 控制項。</span><span class="sxs-lookup"><span data-stu-id="644fe-112">Select the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2.  <span data-ttu-id="644fe-113">在**屬性**視窗中，按一下 <xref:System.Windows.Forms.ToolBar.Buttons%2A>屬性來選取它，然後按一下 **省略**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕來開啟**ToolBarButton 集合編輯器**。</span><span class="sxs-lookup"><span data-stu-id="644fe-113">In the **Properties** window, click the <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it and click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="644fe-114">使用**新增**和**移除**按鈕來加入和移除按鈕等，從<xref:System.Windows.Forms.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="644fe-114">Use the **Add** and **Remove** buttons to add and remove buttons from the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
4.  <span data-ttu-id="644fe-115">設定的屬性中的個別按鈕**屬性**出現在編輯器的右側窗格中的視窗。</span><span class="sxs-lookup"><span data-stu-id="644fe-115">Configure the properties of the individual buttons in the **Properties** window that appears in the pane on the right side of the editor.</span></span> <span data-ttu-id="644fe-116">下表顯示一些要考慮的重要屬性。</span><span class="sxs-lookup"><span data-stu-id="644fe-116">The following table shows some important properties to consider.</span></span>  
  
    |<span data-ttu-id="644fe-117">屬性</span><span class="sxs-lookup"><span data-stu-id="644fe-117">Property</span></span>|<span data-ttu-id="644fe-118">描述</span><span class="sxs-lookup"><span data-stu-id="644fe-118">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|<span data-ttu-id="644fe-119">設定要顯示在下拉式清單工具列按鈕的功能表。</span><span class="sxs-lookup"><span data-stu-id="644fe-119">Sets the menu to be displayed in the drop-down toolbar button.</span></span> <span data-ttu-id="644fe-120">工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設定為<xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>。</span><span class="sxs-lookup"><span data-stu-id="644fe-120">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>.</span></span> <span data-ttu-id="644fe-121">這個屬性可接受的執行個體<xref:System.Windows.Forms.ContextMenu>類別做為參考。</span><span class="sxs-lookup"><span data-stu-id="644fe-121">This property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|<span data-ttu-id="644fe-122">設定是否為部分壓下切換樣式工具列按鈕。</span><span class="sxs-lookup"><span data-stu-id="644fe-122">Sets whether a toggle-style toolbar button is partially pushed.</span></span> <span data-ttu-id="644fe-123">工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設定為<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>。</span><span class="sxs-lookup"><span data-stu-id="644fe-123">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|<span data-ttu-id="644fe-124">設定切換樣式工具列按鈕目前是否在按下的狀態。</span><span class="sxs-lookup"><span data-stu-id="644fe-124">Sets whether a toggle-style toolbar button is currently in the pushed state.</span></span> <span data-ttu-id="644fe-125">工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設定為<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>或<xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>。</span><span class="sxs-lookup"><span data-stu-id="644fe-125">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> or <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|<span data-ttu-id="644fe-126">工具列按鈕的樣式設定。</span><span class="sxs-lookup"><span data-stu-id="644fe-126">Sets the style of the toolbar button.</span></span> <span data-ttu-id="644fe-127">必須是其中一個值在<xref:System.Windows.Forms.ToolBarButtonStyle>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="644fe-127">Must be one of the values in the <xref:System.Windows.Forms.ToolBarButtonStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|<span data-ttu-id="644fe-128">按鈕所顯示的文字字串。</span><span class="sxs-lookup"><span data-stu-id="644fe-128">The text string displayed by the button.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|<span data-ttu-id="644fe-129">顯示按鈕的工具提示文字。</span><span class="sxs-lookup"><span data-stu-id="644fe-129">The text that appears as a ToolTip for the button.</span></span>|  
  
5.  <span data-ttu-id="644fe-130">按一下**確定**關閉對話方塊並建立指定的面板。</span><span class="sxs-lookup"><span data-stu-id="644fe-130">Click **OK** to close the dialog box and create the panels you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="644fe-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="644fe-131">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="644fe-132">操作說明：定義工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="644fe-132">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [<span data-ttu-id="644fe-133">操作說明：觸發工具列按鈕的功能表事件</span><span class="sxs-lookup"><span data-stu-id="644fe-133">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [<span data-ttu-id="644fe-134">工具列控制項概觀</span><span class="sxs-lookup"><span data-stu-id="644fe-134">ToolBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [<span data-ttu-id="644fe-135">ToolBar 控制項</span><span class="sxs-lookup"><span data-stu-id="644fe-135">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
