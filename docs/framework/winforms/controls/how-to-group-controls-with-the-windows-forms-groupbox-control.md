---
title: HOW TO：使用 Windows Forms GroupBox 控制項分組控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: d2bad0020d18cd262bc2fe3489a00209308bd7b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941319"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="c12c8-102">HOW TO：使用 Windows Forms GroupBox 控制項分組控制項</span><span class="sxs-lookup"><span data-stu-id="c12c8-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="c12c8-103">Windows Form<xref:System.Windows.Forms.GroupBox>控制項用來分組其他控制項。</span><span class="sxs-lookup"><span data-stu-id="c12c8-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="c12c8-104">有三個群組控制項的原因：</span><span class="sxs-lookup"><span data-stu-id="c12c8-104">There are three reasons to group controls:</span></span>  
  
- <span data-ttu-id="c12c8-105">若要建立明確的使用者介面的相關的表單項目的視覺化群組。</span><span class="sxs-lookup"><span data-stu-id="c12c8-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
- <span data-ttu-id="c12c8-106">若要建立以程式設計方式 （選項按鈕群組，例如）。</span><span class="sxs-lookup"><span data-stu-id="c12c8-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
- <span data-ttu-id="c12c8-107">在設計階段，做為一個單位移動控制項。</span><span class="sxs-lookup"><span data-stu-id="c12c8-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="c12c8-108">若要建立的控制項群組</span><span class="sxs-lookup"><span data-stu-id="c12c8-108">To create a group of controls</span></span>  
  
1. <span data-ttu-id="c12c8-109">繪製<xref:System.Windows.Forms.GroupBox>表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="c12c8-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="c12c8-110">加入群組方塊中，繪製群組方塊內的每個其他控制項。</span><span class="sxs-lookup"><span data-stu-id="c12c8-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="c12c8-111">如果您有想要的群組方塊括住的現有控制項，您可以選取所有的控制項，它們剪到 剪貼簿上，選取<xref:System.Windows.Forms.GroupBox>控制項，然後再將它們貼入 群組 方塊。</span><span class="sxs-lookup"><span data-stu-id="c12c8-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="c12c8-112">您也可以將它們拖曳至 [群組] 方塊。</span><span class="sxs-lookup"><span data-stu-id="c12c8-112">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="c12c8-113">設定<xref:System.Windows.Forms.GroupBox.Text%2A>群組方塊中，為適當的 caption 屬性。</span><span class="sxs-lookup"><span data-stu-id="c12c8-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c12c8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c12c8-114">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="c12c8-115">GroupBox 控制項</span><span class="sxs-lookup"><span data-stu-id="c12c8-115">GroupBox Control</span></span>](groupbox-control-windows-forms.md)
