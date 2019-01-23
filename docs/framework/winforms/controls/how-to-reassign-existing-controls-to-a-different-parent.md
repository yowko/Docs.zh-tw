---
title: HOW TO：重新指派至不同的父代的現有控制項
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: fa1bd6c0274fdf702072e062e6eeab7078375491
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600254"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="0a2c5-102">HOW TO：重新指派至不同的父代的現有控制項</span><span class="sxs-lookup"><span data-stu-id="0a2c5-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="0a2c5-103">您可以將表單上現有的控制項指派給新的容器控制項。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-103">You can assign controls that exist on your form to a new container control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a2c5-104">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0a2c5-105">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0a2c5-106">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="0a2c5-107">將現有控制項重新指派至不同的父代</span><span class="sxs-lookup"><span data-stu-id="0a2c5-107">To reassign existing controls to a different parent</span></span>  
  
1.  <span data-ttu-id="0a2c5-108">從 [工具箱] <xref:System.Windows.Forms.Button>**將三個** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-108">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>  
  
     <span data-ttu-id="0a2c5-109">將它們放在相鄰的位置，但不要對齊。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-109">Position them near to each other, but leave them unaligned.</span></span>  
  
2.  <span data-ttu-id="0a2c5-110">按一下 [工具箱] 的 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-110">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>  
  
     <span data-ttu-id="0a2c5-111">請勿將圖示拖曳到表單上。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-111">Do not drag the icon onto the form.</span></span>  
  
3.  <span data-ttu-id="0a2c5-112">將滑鼠指標靠近三個 <xref:System.Windows.Forms.Button> 控制項。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-112">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
     <span data-ttu-id="0a2c5-113">指標會變成十字形狀並附有 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-113">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>  
  
4.  <span data-ttu-id="0a2c5-114">按住滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-114">Click and hold the mouse button.</span></span>  
  
5.  <span data-ttu-id="0a2c5-115">拖曳滑鼠指標以繪製 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的外框。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-115">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="0a2c5-116">繪製三個 <xref:System.Windows.Forms.Button> 控制項的外框。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-116">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
7.  <span data-ttu-id="0a2c5-117">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-117">Release the mouse button.</span></span>  
  
     <span data-ttu-id="0a2c5-118">三個 <xref:System.Windows.Forms.Button> 控制項現在都已插入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="0a2c5-118">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a2c5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a2c5-119">See also</span></span>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="0a2c5-120">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="0a2c5-120">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="0a2c5-121">逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="0a2c5-121">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="0a2c5-122">逐步解說：使用對齊線的 Windows Form 上排列控制項</span><span class="sxs-lookup"><span data-stu-id="0a2c5-122">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
