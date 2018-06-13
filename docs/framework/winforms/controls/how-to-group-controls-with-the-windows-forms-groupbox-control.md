---
title: 如何：以 Windows Form GroupBox 控制項來群組控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: 718367e9da9efda20c79fbff3bd2f14f11c96ee1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531920"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="b224a-102">如何：以 Windows Form GroupBox 控制項來群組控制項</span><span class="sxs-lookup"><span data-stu-id="b224a-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="b224a-103">Windows Form<xref:System.Windows.Forms.GroupBox>控制項可用來將其他控制項組成群組。</span><span class="sxs-lookup"><span data-stu-id="b224a-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="b224a-104">群組控制項的三個原因有：</span><span class="sxs-lookup"><span data-stu-id="b224a-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="b224a-105">若要建立的清楚的使用者介面的相關的表單項目的視覺化群組。</span><span class="sxs-lookup"><span data-stu-id="b224a-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="b224a-106">若要建立以程式設計方式 （選項按鈕群組，例如）。</span><span class="sxs-lookup"><span data-stu-id="b224a-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="b224a-107">在設計階段，做為一個單位移動控制項。</span><span class="sxs-lookup"><span data-stu-id="b224a-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="b224a-108">若要建立的控制項群組</span><span class="sxs-lookup"><span data-stu-id="b224a-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="b224a-109">繪製<xref:System.Windows.Forms.GroupBox>控制項在表單上的。</span><span class="sxs-lookup"><span data-stu-id="b224a-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="b224a-110">將其他控制項加入群組方塊中，每個群組的方塊內繪製。</span><span class="sxs-lookup"><span data-stu-id="b224a-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="b224a-111">如果您有想要住在群組中的現有控制項，您可以選取所有控制項，剪下到剪貼簿中，都選取並<xref:System.Windows.Forms.GroupBox>控制項，然後再將它們貼至 [群組] 方塊。</span><span class="sxs-lookup"><span data-stu-id="b224a-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="b224a-112">您也可以將它們拖曳至 [群組] 方塊。</span><span class="sxs-lookup"><span data-stu-id="b224a-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="b224a-113">設定<xref:System.Windows.Forms.GroupBox.Text%2A>屬性群組方塊，以適當的標題。</span><span class="sxs-lookup"><span data-stu-id="b224a-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b224a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b224a-114">See Also</span></span>  
 <xref:System.Windows.Forms.GroupBox>  
 [<span data-ttu-id="b224a-115">GroupBox 控制項</span><span class="sxs-lookup"><span data-stu-id="b224a-115">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
