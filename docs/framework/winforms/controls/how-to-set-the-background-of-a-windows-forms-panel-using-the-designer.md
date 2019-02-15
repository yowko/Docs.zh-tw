---
title: HOW TO：設定使用設計工具的 Windows Form 面板的背景
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 9901b9989afc3602fe4326a2f2360ce894df40e4
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303292"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="cf6eb-102">HOW TO：設定使用設計工具的 Windows Form 面板的背景</span><span class="sxs-lookup"><span data-stu-id="cf6eb-102">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>
<span data-ttu-id="cf6eb-103">Windows Form<xref:System.Windows.Forms.Panel>控制項可以顯示的背景色彩和背景影像。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="cf6eb-104"><xref:System.Windows.Forms.Control.BackColor%2A>屬性會設定包含在窗格中，例如標籤和選項按鈕控制項的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="cf6eb-105">如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>未設定屬性，<xref:System.Windows.Forms.Control.BackColor%2A>選取項目將會填滿所有面板。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="cf6eb-106">如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性設定，將控制項台中包含後面顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>  
  
 <span data-ttu-id="cf6eb-107">下列程序需要**Windows 應用程式**專案，其表單包含<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="cf6eb-108">如需有關如何設定這類專案的資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-108">For information about how to set up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf6eb-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cf6eb-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cf6eb-111">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="cf6eb-112">若要在 Windows Form 設計工具設定背景</span><span class="sxs-lookup"><span data-stu-id="cf6eb-112">To set the background in the Windows Forms Designer</span></span>  
  
1.  <span data-ttu-id="cf6eb-113">選取 <xref:System.Windows.Forms.Panel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-113">Select the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
2.  <span data-ttu-id="cf6eb-114">在 **屬性**視窗中，按一下旁邊的箭號按鈕<xref:System.Windows.Forms.Control.BackColor%2A>屬性以顯示具有三個索引標籤的視窗。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>  
  
3.  <span data-ttu-id="cf6eb-115">選取 **自訂**索引標籤，顯示色的調色盤。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-115">Select the **Custom** tab to display a palette of colors.</span></span>  
  
4.  <span data-ttu-id="cf6eb-116">選取  **Web**或是**系統**tab 鍵移至顯示的預先定義的色彩名稱清單，然後再選取色彩。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-116">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>  
  
5.  <span data-ttu-id="cf6eb-117">在 **屬性**視窗中，按一下旁邊的箭號按鈕<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-117">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>  
  
6.  <span data-ttu-id="cf6eb-118">在 **開啟**對話方塊方塊中，選取您想要顯示的檔案。</span><span class="sxs-lookup"><span data-stu-id="cf6eb-118">In the **Open** dialog box, select the file that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf6eb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf6eb-119">See also</span></span>
- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="cf6eb-120">Panel 控制項</span><span class="sxs-lookup"><span data-stu-id="cf6eb-120">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
- [<span data-ttu-id="cf6eb-121">Panel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="cf6eb-121">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [<span data-ttu-id="cf6eb-122">如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項</span><span class="sxs-lookup"><span data-stu-id="cf6eb-122">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
