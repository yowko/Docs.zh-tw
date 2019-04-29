---
title: HOW TO：使用設計工具定義工具列按鈕的圖示
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 19d0b284238ed662b25627d6077c1ebe6ecc6e86
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757429"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="fe967-102">HOW TO：使用設計工具定義工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="fe967-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="fe967-103"><xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="fe967-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="fe967-104"><xref:System.Windows.Forms.ToolBar> 按鈕可顯示使用者能方便識別其中的圖示。</span><span class="sxs-lookup"><span data-stu-id="fe967-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="fe967-105">這透過將影像加入至達成<xref:System.Windows.Forms.ImageList>元件，並將它與<xref:System.Windows.Forms.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="fe967-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
 <span data-ttu-id="fe967-106">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ToolBar>控制項和<xref:System.Windows.Forms.ImageList>元件。</span><span class="sxs-lookup"><span data-stu-id="fe967-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="fe967-107">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="fe967-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe967-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="fe967-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fe967-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="fe967-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fe967-110">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="fe967-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="fe967-111">若要在設計階段設定的工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="fe967-111">To set an icon for a toolbar button at design time</span></span>  
  
1. <span data-ttu-id="fe967-112">新增映像發佈至<xref:System.Windows.Forms.ImageList>元件。</span><span class="sxs-lookup"><span data-stu-id="fe967-112">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="fe967-113">如需詳細資訊，請參閱[如何：新增或移除 ImageList 影像與設計工具](how-to-add-or-remove-imagelist-images-with-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="fe967-113">For more information, see [How to: Add or Remove ImageList Images with the Designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>  
  
2. <span data-ttu-id="fe967-114">選取<xref:System.Windows.Forms.ToolBar>您表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="fe967-114">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>  
  
3. <span data-ttu-id="fe967-115">在 **屬性**視窗中，將<xref:System.Windows.Forms.ToolBar>控制項的<xref:System.Windows.Forms.ToolBar.ImageList%2A>屬性設<xref:System.Windows.Forms.ImageList>元件。</span><span class="sxs-lookup"><span data-stu-id="fe967-115">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
4. <span data-ttu-id="fe967-116">按一下 <xref:System.Windows.Forms.ToolBar>控制項的<xref:System.Windows.Forms.ToolBar.Buttons%2A>屬性來加以選取，然後按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕，開啟**ToolBarButton 集合編輯器**。</span><span class="sxs-lookup"><span data-stu-id="fe967-116">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
5. <span data-ttu-id="fe967-117">使用**新增** 按鈕，將按鈕加入<xref:System.Windows.Forms.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="fe967-117">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
6. <span data-ttu-id="fe967-118">在**屬性**出現在右側窗格中的視窗**ToolBarButton 集合編輯器**，將<xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A>的每個工具列按鈕，以在清單中，值的其中一個屬性的您加入的映像會取自<xref:System.Windows.Forms.ImageList>元件。</span><span class="sxs-lookup"><span data-stu-id="fe967-118">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe967-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe967-119">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="fe967-120">如何：觸發程序的工具列按鈕的功能表事件</span><span class="sxs-lookup"><span data-stu-id="fe967-120">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="fe967-121">ToolBar 控制項</span><span class="sxs-lookup"><span data-stu-id="fe967-121">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="fe967-122">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="fe967-122">ImageList Component</span></span>](imagelist-component-windows-forms.md)
