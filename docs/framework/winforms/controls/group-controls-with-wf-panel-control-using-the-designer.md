---
title: 如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 1cf4519a9aaaa1c4f0df321ab38c3f543c87b2a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525619"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="d370c-102">如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項</span><span class="sxs-lookup"><span data-stu-id="d370c-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="d370c-103">Windows Form<xref:System.Windows.Forms.Panel>控制項可用來將其他控制項組成群組。</span><span class="sxs-lookup"><span data-stu-id="d370c-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="d370c-104">有群組控制項的三個原因。</span><span class="sxs-lookup"><span data-stu-id="d370c-104">There are three reasons to group controls.</span></span> <span data-ttu-id="d370c-105">其中一個是視覺化群組相關的表單項目，清楚的使用者介面。另一個是以程式設計方式分組，選項按鈕： 例如，上次是在設計階段將控制項移做為一個單位。</span><span class="sxs-lookup"><span data-stu-id="d370c-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d370c-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="d370c-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d370c-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="d370c-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d370c-108">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="d370c-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="d370c-109">若要建立的控制項群組</span><span class="sxs-lookup"><span data-stu-id="d370c-109">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="d370c-110">拖曳<xref:System.Windows.Forms.Panel>控制項從**Windows Form**  索引標籤的 工具箱 拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="d370c-110">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>  
  
2.  <span data-ttu-id="d370c-111">將其他控制項加入面板中，每個面板內繪製。</span><span class="sxs-lookup"><span data-stu-id="d370c-111">Add other controls to the panel, drawing each inside the panel.</span></span>  
  
     <span data-ttu-id="d370c-112">如果您有想要住在面板中的現有控制項，您可以選取所有控制項，剪下到剪貼簿中，都選取並<xref:System.Windows.Forms.Panel>控制項，然後再將它們貼至 [面板]。</span><span class="sxs-lookup"><span data-stu-id="d370c-112">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="d370c-113">您也可以將它們拖曳到 [面板]。</span><span class="sxs-lookup"><span data-stu-id="d370c-113">You can also drag them into the panel.</span></span>  
  
3.  <span data-ttu-id="d370c-114">（選擇性）如果您想要將框線加入至面板，設定其<xref:System.Windows.Forms.BorderStyle>屬性。</span><span class="sxs-lookup"><span data-stu-id="d370c-114">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="d370c-115">有三個選擇： <xref:System.Windows.Forms.BorderStyle.Fixed3D>， <xref:System.Windows.Forms.BorderStyle.FixedSingle>，和<xref:System.Windows.Forms.BorderStyle.None>。</span><span class="sxs-lookup"><span data-stu-id="d370c-115">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d370c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d370c-116">See Also</span></span>  
 [<span data-ttu-id="d370c-117">Panel 控制項</span><span class="sxs-lookup"><span data-stu-id="d370c-117">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [<span data-ttu-id="d370c-118">Panel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="d370c-118">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="d370c-119">操作說明：設定面板背景</span><span class="sxs-lookup"><span data-stu-id="d370c-119">How to: Set the Background of a Panel</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
