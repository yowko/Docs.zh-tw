---
title: 具有分組控制項的群組控制項
description: 瞭解如何使用 Windows Forms 分組控制項群組控制項，讓您可以建立相關元素的視覺化群組。
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: f84c495a18f4ae5e04367f024a1e2849f1ed59f9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618060"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="094f2-103">如何：以 Windows Form GroupBox 控制項來群組控制項</span><span class="sxs-lookup"><span data-stu-id="094f2-103">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="094f2-104">Windows Forms <xref:System.Windows.Forms.GroupBox> 控制項是用來將其他控制項分組。</span><span class="sxs-lookup"><span data-stu-id="094f2-104">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="094f2-105">群組控制項的原因有三個：</span><span class="sxs-lookup"><span data-stu-id="094f2-105">There are three reasons to group controls:</span></span>  
  
- <span data-ttu-id="094f2-106">為明確的使用者介面建立相關表單元素的視覺化群組。</span><span class="sxs-lookup"><span data-stu-id="094f2-106">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
- <span data-ttu-id="094f2-107">建立程式設計群組（例如選項按鈕）。</span><span class="sxs-lookup"><span data-stu-id="094f2-107">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
- <span data-ttu-id="094f2-108">用於在設計階段將控制項移動為一個單位。</span><span class="sxs-lookup"><span data-stu-id="094f2-108">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="094f2-109">若要建立控制項群組</span><span class="sxs-lookup"><span data-stu-id="094f2-109">To create a group of controls</span></span>  
  
1. <span data-ttu-id="094f2-110"><xref:System.Windows.Forms.GroupBox>在表單上繪製控制項。</span><span class="sxs-lookup"><span data-stu-id="094f2-110">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="094f2-111">將其他控制項新增至 [群組] 方塊，並在 [群組方塊] 內繪製每個控制項。</span><span class="sxs-lookup"><span data-stu-id="094f2-111">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="094f2-112">如果您有想要放在群組方塊中的現有控制項，您可以選取所有控制項、將其剪下至剪貼簿、選取 <xref:System.Windows.Forms.GroupBox> 控制項，然後將它們貼到 [群組] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="094f2-112">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="094f2-113">您也可以將它們拖曳到 [群組] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="094f2-113">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="094f2-114">將 <xref:System.Windows.Forms.GroupBox.Text%2A> [群組方塊] 的屬性設定為適當的標題。</span><span class="sxs-lookup"><span data-stu-id="094f2-114">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="094f2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="094f2-115">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="094f2-116">GroupBox 控制項</span><span class="sxs-lookup"><span data-stu-id="094f2-116">GroupBox Control</span></span>](groupbox-control-windows-forms.md)
