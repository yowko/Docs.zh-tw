---
title: HOW TO：將 Windows Forms 上的物件分層
ms.date: 03/30/2017
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
ms.openlocfilehash: 8d0abbf0f71ac176d17261a0ae863938c575bdaf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311646"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="3ca5f-102">HOW TO：將 Windows Forms 上的物件分層</span><span class="sxs-lookup"><span data-stu-id="3ca5f-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="3ca5f-103">當您建立複雜的使用者介面，或使用多個文件介面 (MDI) 表單時，您通常要控制項和子表單，以建立更複雜的使用者介面 (UI) 層級。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="3ca5f-104">移動和追蹤的控制項和 windows 群組的內容中，您可以使用他們的疊置順序。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="3ca5f-105">*疊置順序*是沿著表單的 z 軸 （深度） 的表單上控制項的視覺分層。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="3ca5f-106">在頂端的疊置順序的視窗重疊所有其他視窗。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="3ca5f-107">所有其他視窗重疊視窗底部的疊置順序。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-107">All other windows overlap the window at the bottom of the z-order.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ca5f-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3ca5f-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3ca5f-110">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="3ca5f-111">在設計階段的圖層控制項</span><span class="sxs-lookup"><span data-stu-id="3ca5f-111">To layer controls at design time</span></span>  
  
1. <span data-ttu-id="3ca5f-112">選取您想要圖層的控制項。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-112">Select a control that you want to layer.</span></span>  
  
2. <span data-ttu-id="3ca5f-113">上**格式**功能表上，指向**順序**，然後按一下**提到最上層**或是**移到最下層**。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-113">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>  
  
### <a name="to-layer-controls-programmatically"></a><span data-ttu-id="3ca5f-114">若要以程式設計方式配置控制項</span><span class="sxs-lookup"><span data-stu-id="3ca5f-114">To layer controls programmatically</span></span>  
  
-   <span data-ttu-id="3ca5f-115">使用<xref:System.Windows.Forms.Control.BringToFront%2A>和<xref:System.Windows.Forms.Control.SendToBack%2A>來操作控制項疊置順序的方法。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-115">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>  
  
     <span data-ttu-id="3ca5f-116">例如，如果<xref:System.Windows.Forms.TextBox>控制項， `txtFirstName`，是下面另一個控制項，而且您想要將它在最上層，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="3ca5f-116">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>  
  
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
>  <span data-ttu-id="3ca5f-117">Windows Form 支援*控制項內含項目*。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-117">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="3ca5f-118">控制項內含項目牽涉到將多個控制項內包含的控制項，例如數目<xref:System.Windows.Forms.RadioButton>控制項內<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-118">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="3ca5f-119">然後，您可以層中包含的控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-119">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="3ca5f-120">移動 [群組] 中移動了控制項，因為它們包含在其中。</span><span class="sxs-lookup"><span data-stu-id="3ca5f-120">Moving the group box moves the controls as well, because they are contained inside it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ca5f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ca5f-121">See also</span></span>

- [<span data-ttu-id="3ca5f-122">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="3ca5f-122">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="3ca5f-123">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="3ca5f-123">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="3ca5f-124">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="3ca5f-124">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="3ca5f-125">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="3ca5f-125">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="3ca5f-126">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="3ca5f-126">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
