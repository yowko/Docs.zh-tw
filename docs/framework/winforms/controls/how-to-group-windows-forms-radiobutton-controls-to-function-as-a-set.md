---
title: 將選項按鈕控制項當做一組來運作
description: 瞭解如何將 Windows Forms 選項按鈕控制項分組，以獨立于其他集合運作。
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325925"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="98bba-103">如何：將 Windows Form RadioButton 控制項群組成集合使用</span><span class="sxs-lookup"><span data-stu-id="98bba-103">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="98bba-104">Windows Forms <xref:System.Windows.Forms.RadioButton> 控制項的設計目的是要讓使用者在兩個或多個設定之間做選擇，其中只有一個可以指派給程式或物件。</span><span class="sxs-lookup"><span data-stu-id="98bba-104">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="98bba-105">例如，一組 <xref:System.Windows.Forms.RadioButton> 控制項可能會顯示訂單的套件的選擇，但只會使用其中一個電信公司。</span><span class="sxs-lookup"><span data-stu-id="98bba-105">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="98bba-106">因此 <xref:System.Windows.Forms.RadioButton> ，一次只能選取一個，即使它是功能群組的一部分也一樣。</span><span class="sxs-lookup"><span data-stu-id="98bba-106">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="98bba-107">在 <xref:System.Windows.Forms.Panel> 控制項、 <xref:System.Windows.Forms.GroupBox> 控制項或表單之類的容器內繪製選項按鈕，即可將其分組。</span><span class="sxs-lookup"><span data-stu-id="98bba-107">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="98bba-108">直接新增至表單的所有選項按鈕都會變成一個群組。</span><span class="sxs-lookup"><span data-stu-id="98bba-108">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="98bba-109">若要加入不同的群組，您必須將它們放在面板或群組方塊中。</span><span class="sxs-lookup"><span data-stu-id="98bba-109">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="98bba-110">如需面板或群組方塊的詳細資訊，請參閱[面板控制項總覽](panel-control-overview-windows-forms.md)或[分組控制項總覽](groupbox-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="98bba-110">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="98bba-111">將選項按鈕控制群組成群組，以獨立于其他集合運作</span><span class="sxs-lookup"><span data-stu-id="98bba-111">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="98bba-112">從 [ <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> **工具箱**] 的 [ **Windows Forms** ] 索引標籤，將或控制項拖曳到表單上。</span><span class="sxs-lookup"><span data-stu-id="98bba-112">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="98bba-113"><xref:System.Windows.Forms.RadioButton>在或控制項上繪製控制項 <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> 。</span><span class="sxs-lookup"><span data-stu-id="98bba-113">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98bba-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98bba-114">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="98bba-115">RadioButton 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="98bba-115">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="98bba-116">Panel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="98bba-116">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="98bba-117">GroupBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="98bba-117">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="98bba-118">CheckBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="98bba-118">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="98bba-119">RadioButton 控制項</span><span class="sxs-lookup"><span data-stu-id="98bba-119">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
