---
title: 作法：使用設計工具定義工具列按鈕的圖示
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 49e93f12bebbf409e6b3a06634556b9103c85f44
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666210"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="5e1fc-102">HOW TO：使用設計工具定義工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="5e1fc-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="5e1fc-103"><xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="5e1fc-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>

<span data-ttu-id="5e1fc-104"><xref:System.Windows.Forms.ToolBar>按鈕可以在其中顯示圖示, 供使用者輕鬆識別。</span><span class="sxs-lookup"><span data-stu-id="5e1fc-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="5e1fc-105">這可以透過將影像新增至<xref:System.Windows.Forms.ImageList>元件, 並將它<xref:System.Windows.Forms.ToolBar>與控制項產生關聯來達成。</span><span class="sxs-lookup"><span data-stu-id="5e1fc-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>

<span data-ttu-id="5e1fc-106">下列程式需要具有包含<xref:System.Windows.Forms.ToolBar>控制項和<xref:System.Windows.Forms.ImageList>元件之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="5e1fc-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="5e1fc-107">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="5e1fc-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="5e1fc-108">在設計階段設定工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="5e1fc-108">To set an icon for a toolbar button at design time</span></span>

1. <span data-ttu-id="5e1fc-109">將影像新增至<xref:System.Windows.Forms.ImageList>元件。</span><span class="sxs-lookup"><span data-stu-id="5e1fc-109">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="5e1fc-110">如需詳細資訊，請參閱[如何：使用設計](how-to-add-or-remove-imagelist-images-with-the-designer.md)工具加入或移除 ImageList 影像。</span><span class="sxs-lookup"><span data-stu-id="5e1fc-110">For more information, see [How to: Add or Remove ImageList Images with the Designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>

2. <span data-ttu-id="5e1fc-111">選取窗<xref:System.Windows.Forms.ToolBar>體上的控制項。</span><span class="sxs-lookup"><span data-stu-id="5e1fc-111">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>

3. <span data-ttu-id="5e1fc-112">在 [**屬性**] 視窗中, <xref:System.Windows.Forms.ToolBar>將控制項<xref:System.Windows.Forms.ToolBar.ImageList%2A> <xref:System.Windows.Forms.ImageList>的屬性設定為元件。</span><span class="sxs-lookup"><span data-stu-id="5e1fc-112">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>

4. <span data-ttu-id="5e1fc-113"><xref:System.Windows.Forms.ToolBar.Buttons%2A> ![ ](./media/visual-studio-ellipsis-button.png)按一下控制項的屬性來選取它, 然後按一下省略號 ([屬性視窗中 Visual Studio] 按鈕的省略號按鈕 (...), 以開啟 [ **ToolBarButton 集合編輯器**]。 <xref:System.Windows.Forms.ToolBar></span><span class="sxs-lookup"><span data-stu-id="5e1fc-113">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **ToolBarButton Collection Editor**.</span></span>

5. <span data-ttu-id="5e1fc-114">使用 [**加入**] 按鈕, 將按鈕<xref:System.Windows.Forms.ToolBar>加入控制項。</span><span class="sxs-lookup"><span data-stu-id="5e1fc-114">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>

6. <span data-ttu-id="5e1fc-115">在 [ **ToolBarButton 集合編輯器**] 右側窗格中出現的 [ <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> **屬性**] 視窗中, 將每個工具列按鈕的屬性設定為清單中的其中一個值, 這是從您新增至的影像所繪製<xref:System.Windows.Forms.ImageList>元件。</span><span class="sxs-lookup"><span data-stu-id="5e1fc-115">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e1fc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e1fc-116">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="5e1fc-117">如何：觸發工具列按鈕的功能表事件</span><span class="sxs-lookup"><span data-stu-id="5e1fc-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="5e1fc-118">ToolBar 控制項</span><span class="sxs-lookup"><span data-stu-id="5e1fc-118">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="5e1fc-119">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="5e1fc-119">ImageList Component</span></span>](imagelist-component-windows-forms.md)
