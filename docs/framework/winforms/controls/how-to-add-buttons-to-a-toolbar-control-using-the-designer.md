---
title: 作法：使用設計工具將按鈕新增至 ToolBar 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: 4d7a49633599aabc96153e4793e50c1a4d6d092d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666212"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a><span data-ttu-id="f624b-102">作法：使用設計工具將按鈕新增至 ToolBar 控制項</span><span class="sxs-lookup"><span data-stu-id="f624b-102">How to: Add Buttons to a ToolBar Control Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="f624b-103"><xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="f624b-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>

<span data-ttu-id="f624b-104"><xref:System.Windows.Forms.ToolBar>控制項的整數部分是您加入其中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="f624b-104">An integral part of the <xref:System.Windows.Forms.ToolBar> control is the buttons you add to it.</span></span> <span data-ttu-id="f624b-105">這些可以用來提供功能表命令的輕鬆存取, 或者將它們放在應用程式使用者介面的另一個區域, 以向您的使用者公開功能表結構中無法使用的命令。</span><span class="sxs-lookup"><span data-stu-id="f624b-105">These can be used to provide easy access to menu commands or, alternately, they can be placed in another area of the user interface of your application to expose commands to your users that are not available in the menu structure.</span></span>

<span data-ttu-id="f624b-106">下列程式需要具有包含<xref:System.Windows.Forms.ToolBar>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="f624b-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control.</span></span> <span data-ttu-id="f624b-107">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="f624b-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-buttons-at-design-time"></a><span data-ttu-id="f624b-108">若要在設計階段加入按鈕</span><span class="sxs-lookup"><span data-stu-id="f624b-108">To add buttons at design time</span></span>

1. <span data-ttu-id="f624b-109">選取 <xref:System.Windows.Forms.ToolBar> 控制項。</span><span class="sxs-lookup"><span data-stu-id="f624b-109">Select the <xref:System.Windows.Forms.ToolBar> control.</span></span>

2. <span data-ttu-id="f624b-110">在 [**屬性**] 視窗中, <xref:System.Windows.Forms.ToolBar.Buttons%2A>按一下屬性來選取它, 然後按一下省略號![([屬性視窗中 Visual Studio](./media/visual-studio-ellipsis-button.png)] 按鈕的省略號按鈕 (...), 以開啟**ToolBarButton集合編輯器**。</span><span class="sxs-lookup"><span data-stu-id="f624b-110">In the **Properties** window, click the <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it and click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **ToolBarButton Collection Editor**.</span></span>

3. <span data-ttu-id="f624b-111">使用 [**新增**] 和 [**移除**] 按鈕, 即可在<xref:System.Windows.Forms.ToolBar>控制項中加入和移除按鈕。</span><span class="sxs-lookup"><span data-stu-id="f624b-111">Use the **Add** and **Remove** buttons to add and remove buttons from the <xref:System.Windows.Forms.ToolBar> control.</span></span>

4. <span data-ttu-id="f624b-112">在編輯器右側窗格中的 [**屬性**] 視窗中, 設定個別按鈕的屬性。</span><span class="sxs-lookup"><span data-stu-id="f624b-112">Configure the properties of the individual buttons in the **Properties** window that appears in the pane on the right side of the editor.</span></span> <span data-ttu-id="f624b-113">下表顯示一些要考慮的重要屬性。</span><span class="sxs-lookup"><span data-stu-id="f624b-113">The following table shows some important properties to consider.</span></span>

    |<span data-ttu-id="f624b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="f624b-114">Property</span></span>|<span data-ttu-id="f624b-115">描述</span><span class="sxs-lookup"><span data-stu-id="f624b-115">Description</span></span>|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|<span data-ttu-id="f624b-116">設定要顯示在下拉式工具列按鈕中的功能表。</span><span class="sxs-lookup"><span data-stu-id="f624b-116">Sets the menu to be displayed in the drop-down toolbar button.</span></span> <span data-ttu-id="f624b-117">工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設定為<xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>。</span><span class="sxs-lookup"><span data-stu-id="f624b-117">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>.</span></span> <span data-ttu-id="f624b-118">這個屬性會將<xref:System.Windows.Forms.ContextMenu>類別的實例當做參考。</span><span class="sxs-lookup"><span data-stu-id="f624b-118">This property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span>|
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|<span data-ttu-id="f624b-119">設定是否要部分推送轉場樣式的工具列按鈕。</span><span class="sxs-lookup"><span data-stu-id="f624b-119">Sets whether a toggle-style toolbar button is partially pushed.</span></span> <span data-ttu-id="f624b-120">工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設定為<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>。</span><span class="sxs-lookup"><span data-stu-id="f624b-120">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.</span></span>|
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|<span data-ttu-id="f624b-121">設定轉場樣式的工具列按鈕目前是否處於已推送狀態。</span><span class="sxs-lookup"><span data-stu-id="f624b-121">Sets whether a toggle-style toolbar button is currently in the pushed state.</span></span> <span data-ttu-id="f624b-122">工具列按鈕的<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性必須設定為<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>或<xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>。</span><span class="sxs-lookup"><span data-stu-id="f624b-122">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> or <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.</span></span>|
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|<span data-ttu-id="f624b-123">設定工具列按鈕的樣式。</span><span class="sxs-lookup"><span data-stu-id="f624b-123">Sets the style of the toolbar button.</span></span> <span data-ttu-id="f624b-124">必須是<xref:System.Windows.Forms.ToolBarButtonStyle>列舉中的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="f624b-124">Must be one of the values in the <xref:System.Windows.Forms.ToolBarButtonStyle> enumeration.</span></span>|
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|<span data-ttu-id="f624b-125">按鈕所顯示的文字字串。</span><span class="sxs-lookup"><span data-stu-id="f624b-125">The text string displayed by the button.</span></span>|
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|<span data-ttu-id="f624b-126">顯示為按鈕工具提示的文字。</span><span class="sxs-lookup"><span data-stu-id="f624b-126">The text that appears as a ToolTip for the button.</span></span>|

5. <span data-ttu-id="f624b-127">按一下 **[確定**] 關閉對話方塊, 並建立您指定的面板。</span><span class="sxs-lookup"><span data-stu-id="f624b-127">Click **OK** to close the dialog box and create the panels you specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="f624b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f624b-128">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="f624b-129">如何：定義工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="f624b-129">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="f624b-130">如何：觸發工具列按鈕的功能表事件</span><span class="sxs-lookup"><span data-stu-id="f624b-130">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="f624b-131">工具列控制項概觀</span><span class="sxs-lookup"><span data-stu-id="f624b-131">ToolBar Control Overview</span></span>](toolbar-control-overview-windows-forms.md)
- [<span data-ttu-id="f624b-132">ToolBar 控制項</span><span class="sxs-lookup"><span data-stu-id="f624b-132">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
