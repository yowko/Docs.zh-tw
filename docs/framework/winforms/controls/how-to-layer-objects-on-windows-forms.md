---
title: "如何：將 Windows Form 上的物件分層"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f042816b912a0de643dd1d0f66ddba6d5eff7df2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="4eec8-102">如何：將 Windows Form 上的物件分層</span><span class="sxs-lookup"><span data-stu-id="4eec8-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="4eec8-103">當您建立複雜的使用者介面，或使用多個文件介面 (MDI) 表單時，您通常要控制項和子表單，以建立更複雜的使用者介面 (UI) 層級。</span><span class="sxs-lookup"><span data-stu-id="4eec8-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="4eec8-104">若要移動並追蹤的控制項和 windows 群組的內容中，您管理他們的疊置順序。</span><span class="sxs-lookup"><span data-stu-id="4eec8-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="4eec8-105">*疊置順序*會沿著表單 z （深度） 的表單上控制項的視覺化圖層。</span><span class="sxs-lookup"><span data-stu-id="4eec8-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="4eec8-106">視窗頂端的疊置順序，與所有其他 windows 重疊。</span><span class="sxs-lookup"><span data-stu-id="4eec8-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="4eec8-107">所有其他視窗重疊視窗底部的疊置順序。</span><span class="sxs-lookup"><span data-stu-id="4eec8-107">All other windows overlap the window at the bottom of the z-order.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4eec8-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="4eec8-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4eec8-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="4eec8-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4eec8-110">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="4eec8-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="4eec8-111">在設計階段的圖層控制項</span><span class="sxs-lookup"><span data-stu-id="4eec8-111">To layer controls at design time</span></span>  
  
1.  <span data-ttu-id="4eec8-112">選取您想要在圖層的控制項。</span><span class="sxs-lookup"><span data-stu-id="4eec8-112">Select a control that you want to layer.</span></span>  
  
2.  <span data-ttu-id="4eec8-113">在**格式**功能表上，指向**順序**，然後按一下 **提到最上層**或**下層**。</span><span class="sxs-lookup"><span data-stu-id="4eec8-113">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>  
  
### <a name="to-layer-controls-programmatically"></a><span data-ttu-id="4eec8-114">以程式設計方式將層級控制</span><span class="sxs-lookup"><span data-stu-id="4eec8-114">To layer controls programmatically</span></span>  
  
-   <span data-ttu-id="4eec8-115">使用<xref:System.Windows.Forms.Control.BringToFront%2A>和<xref:System.Windows.Forms.Control.SendToBack%2A>管理控制項疊置順序的方法。</span><span class="sxs-lookup"><span data-stu-id="4eec8-115">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>  
  
     <span data-ttu-id="4eec8-116">例如，如果<xref:System.Windows.Forms.TextBox>控制項， `txtFirstName`，是下面另一個控制項，而且您想要有在最上層，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4eec8-116">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="4eec8-117">Windows Form 支援*控制項內含項目*。</span><span class="sxs-lookup"><span data-stu-id="4eec8-117">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="4eec8-118">控制項內含項目都放多個控制項中包含的控制項，例如數目<xref:System.Windows.Forms.RadioButton>內控制<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="4eec8-118">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="4eec8-119">您可以再圖層內包含的控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="4eec8-119">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="4eec8-120">移動群組方塊移動了控制項，因為它們包含在它之內。</span><span class="sxs-lookup"><span data-stu-id="4eec8-120">Moving the group box moves the controls as well, because they are contained inside it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eec8-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="4eec8-121">See Also</span></span>  
 [<span data-ttu-id="4eec8-122">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="4eec8-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="4eec8-123">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="4eec8-123">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="4eec8-124">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="4eec8-124">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="4eec8-125">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="4eec8-125">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="4eec8-126">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="4eec8-126">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
