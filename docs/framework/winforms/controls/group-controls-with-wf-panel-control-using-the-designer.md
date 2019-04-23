---
title: HOW TO：使用設計工具以 Windows Forms Panel 控制項分組控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 662343af42f72816a5a673d2cd6d839a5dca9190
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341396"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="82424-102">HOW TO：使用設計工具以 Windows Forms Panel 控制項分組控制項</span><span class="sxs-lookup"><span data-stu-id="82424-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="82424-103">Windows Form<xref:System.Windows.Forms.Panel>控制項用來分組其他控制項。</span><span class="sxs-lookup"><span data-stu-id="82424-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="82424-104">有三個群組控制項的原因。</span><span class="sxs-lookup"><span data-stu-id="82424-104">There are three reasons to group controls.</span></span> <span data-ttu-id="82424-105">其中一個是視覺化群組相關的表單項目，清楚的使用者介面;另一個是以程式設計方式分組，選項按鈕： 例如，最後一個適用於在設計階段將控制項移動做為一個單位。</span><span class="sxs-lookup"><span data-stu-id="82424-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82424-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="82424-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="82424-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="82424-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="82424-108">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="82424-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="82424-109">若要建立的控制項群組</span><span class="sxs-lookup"><span data-stu-id="82424-109">To create a group of controls</span></span>  
  
1. <span data-ttu-id="82424-110">拖曳<xref:System.Windows.Forms.Panel>控制項從**Windows Forms**  索引標籤的 工具箱 拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="82424-110">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>  
  
2. <span data-ttu-id="82424-111">將其他控制項加入窗格中，每個面板內繪製。</span><span class="sxs-lookup"><span data-stu-id="82424-111">Add other controls to the panel, drawing each inside the panel.</span></span>  
  
     <span data-ttu-id="82424-112">如果您有現有的控制項，您想要包圍的面板中，您可以選取所有的控制項，它們剪到 剪貼簿上，選取<xref:System.Windows.Forms.Panel>控制項，然後再將它們貼到 面板 中。</span><span class="sxs-lookup"><span data-stu-id="82424-112">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="82424-113">您也可以將它們拖曳至面板。</span><span class="sxs-lookup"><span data-stu-id="82424-113">You can also drag them into the panel.</span></span>  
  
3. <span data-ttu-id="82424-114">（選擇性）如果您想要將框線加入至面板，設定其<xref:System.Windows.Forms.BorderStyle>屬性。</span><span class="sxs-lookup"><span data-stu-id="82424-114">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="82424-115">有三種選擇： <xref:System.Windows.Forms.BorderStyle.Fixed3D>， <xref:System.Windows.Forms.BorderStyle.FixedSingle>，和<xref:System.Windows.Forms.BorderStyle.None>。</span><span class="sxs-lookup"><span data-stu-id="82424-115">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82424-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82424-116">See also</span></span>

- [<span data-ttu-id="82424-117">Panel 控制項</span><span class="sxs-lookup"><span data-stu-id="82424-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="82424-118">Panel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="82424-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="82424-119">如何：設定面板背景</span><span class="sxs-lookup"><span data-stu-id="82424-119">How to: Set the Background of a Panel</span></span>](how-to-set-the-background-of-a-windows-forms-panel.md)
