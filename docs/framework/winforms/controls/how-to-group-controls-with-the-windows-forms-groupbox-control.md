---
title: 具有分組控制項的群組控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: bb7476c410d2802b5d32cc9842a778f290765e32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736660"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="e33af-102">如何：以 Windows Form GroupBox 控制項來群組控制項</span><span class="sxs-lookup"><span data-stu-id="e33af-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="e33af-103">Windows Forms <xref:System.Windows.Forms.GroupBox> 控制項用來分組其他控制項。</span><span class="sxs-lookup"><span data-stu-id="e33af-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="e33af-104">群組控制項的原因有三個：</span><span class="sxs-lookup"><span data-stu-id="e33af-104">There are three reasons to group controls:</span></span>  
  
- <span data-ttu-id="e33af-105">為明確的使用者介面建立相關表單元素的視覺化群組。</span><span class="sxs-lookup"><span data-stu-id="e33af-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
- <span data-ttu-id="e33af-106">建立程式設計群組（例如選項按鈕）。</span><span class="sxs-lookup"><span data-stu-id="e33af-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
- <span data-ttu-id="e33af-107">用於在設計階段將控制項移動為一個單位。</span><span class="sxs-lookup"><span data-stu-id="e33af-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="e33af-108">若要建立控制項群組</span><span class="sxs-lookup"><span data-stu-id="e33af-108">To create a group of controls</span></span>  
  
1. <span data-ttu-id="e33af-109">在表單上繪製 <xref:System.Windows.Forms.GroupBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="e33af-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="e33af-110">將其他控制項新增至 [群組] 方塊，並在 [群組方塊] 內繪製每個控制項。</span><span class="sxs-lookup"><span data-stu-id="e33af-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="e33af-111">如果您有想要放在群組方塊中的現有控制項，您可以選取所有控制項、將其剪下至剪貼簿、選取 [<xref:System.Windows.Forms.GroupBox>] 控制項，然後將它們貼到 [群組] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="e33af-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="e33af-112">您也可以將它們拖曳到 [群組] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="e33af-112">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="e33af-113">將 [群組方塊] 的 [<xref:System.Windows.Forms.GroupBox.Text%2A>] 屬性設定為適當的標題。</span><span class="sxs-lookup"><span data-stu-id="e33af-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e33af-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="e33af-114">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="e33af-115">GroupBox 控制項</span><span class="sxs-lookup"><span data-stu-id="e33af-115">GroupBox Control</span></span>](groupbox-control-windows-forms.md)
