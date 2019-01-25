---
title: HOW TO：群組 Windows Form RadioButton 控制項為一組的函式
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 2758ff2380431668b2c908dbddd5dbe2094ccd0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569332"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="e8d60-102">HOW TO：群組 Windows Form RadioButton 控制項為一組的函式</span><span class="sxs-lookup"><span data-stu-id="e8d60-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="e8d60-103">Windows Form<xref:System.Windows.Forms.RadioButton>控制項的設計，讓使用者在兩個或多個設定，其中只有一個可以指派給程序或物件之間的選擇。</span><span class="sxs-lookup"><span data-stu-id="e8d60-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="e8d60-104">比方說，一群<xref:System.Windows.Forms.RadioButton>控制項可能會顯示各種套件電訊廠商的訂單，但將使用的電訊廠商的其中之一。</span><span class="sxs-lookup"><span data-stu-id="e8d60-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="e8d60-105">因此只有一個<xref:System.Windows.Forms.RadioButton>一次可被選取，即使它是功能群組的一部分。</span><span class="sxs-lookup"><span data-stu-id="e8d60-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="e8d60-106">您藉由繪製這些容器內這類群組選項按鈕<xref:System.Windows.Forms.Panel>控制項，<xref:System.Windows.Forms.GroupBox>控制項或表單。</span><span class="sxs-lookup"><span data-stu-id="e8d60-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="e8d60-107">所有選項按鈕，會直接新增至表單變成一個群組。</span><span class="sxs-lookup"><span data-stu-id="e8d60-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="e8d60-108">若要新增個別的群組，您必須將它們放在面板或群組方塊內。</span><span class="sxs-lookup"><span data-stu-id="e8d60-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="e8d60-109">如需面板或群組方塊的詳細資訊，請參閱[Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)或是[GroupBox 控制項概觀](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="e8d60-109">For more information about panels or group boxes, see [Panel Control Overview](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) or [GroupBox Control Overview](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="e8d60-110">RadioButton 控制項群組設為獨立於其他組的函式</span><span class="sxs-lookup"><span data-stu-id="e8d60-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1.  <span data-ttu-id="e8d60-111">拖曳<xref:System.Windows.Forms.GroupBox>或是<xref:System.Windows.Forms.Panel>控制從**Windows Forms**索引標籤上**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="e8d60-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="e8d60-112">繪製<xref:System.Windows.Forms.RadioButton>上的控制項<xref:System.Windows.Forms.GroupBox>或<xref:System.Windows.Forms.Panel>控制項。</span><span class="sxs-lookup"><span data-stu-id="e8d60-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d60-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8d60-113">See also</span></span>
- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="e8d60-114">RadioButton 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e8d60-114">RadioButton Control Overview</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="e8d60-115">Panel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e8d60-115">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [<span data-ttu-id="e8d60-116">GroupBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e8d60-116">GroupBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="e8d60-117">CheckBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e8d60-117">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="e8d60-118">RadioButton 控制項</span><span class="sxs-lookup"><span data-stu-id="e8d60-118">RadioButton Control</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
