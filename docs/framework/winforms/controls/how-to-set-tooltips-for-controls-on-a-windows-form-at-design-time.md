---
title: HOW TO：在設計階段設定 Windows Forms 的控制項工具提示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: d2bca517e98a8258d4f510c64593de2ad9646e13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157595"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="8501d-102">HOW TO：在設計階段設定 Windows Forms 的控制項工具提示</span><span class="sxs-lookup"><span data-stu-id="8501d-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="8501d-103">您可以設定<xref:System.Windows.Forms.ToolTip>在程式碼，或在 Windows Form 設計工具中的字串。</span><span class="sxs-lookup"><span data-stu-id="8501d-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="8501d-104">如需詳細資訊<xref:System.Windows.Forms.ToolTip>元件，請參閱 < [ToolTip 元件概觀](tooltip-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="8501d-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8501d-105">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="8501d-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8501d-106">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="8501d-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8501d-107">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="8501d-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="8501d-108">以程式設計方式設定工具提示</span><span class="sxs-lookup"><span data-stu-id="8501d-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="8501d-109">新增控制項，將會顯示工具提示。</span><span class="sxs-lookup"><span data-stu-id="8501d-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="8501d-110">使用<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>方法的<xref:System.Windows.Forms.ToolTip>元件。</span><span class="sxs-lookup"><span data-stu-id="8501d-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="8501d-111">若要在設計師中設定工具提示</span><span class="sxs-lookup"><span data-stu-id="8501d-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="8501d-112">新增 <xref:System.Windows.Forms.ToolTip> 元件至表單。</span><span class="sxs-lookup"><span data-stu-id="8501d-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="8501d-113">選取的控制項，將會顯示工具提示，或將它新增至表單。</span><span class="sxs-lookup"><span data-stu-id="8501d-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="8501d-114">在 **屬性**視窗中，將**ToolTip1 的**適當的文字字串的值。</span><span class="sxs-lookup"><span data-stu-id="8501d-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="8501d-115">若要以程式設計方式移除工具提示</span><span class="sxs-lookup"><span data-stu-id="8501d-115">To remove a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="8501d-116">使用<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>方法的<xref:System.Windows.Forms.ToolTip>元件。</span><span class="sxs-lookup"><span data-stu-id="8501d-116">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
    ```vb  
    ' In this example, Button1 is the control displaying the ToolTip.  
    ToolTip1.SetToolTip(Button1, Nothing)  
    ```  
  
    ```csharp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1.SetToolTip(button1, null);  
    ```  
  
    ```cpp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1->SetToolTip(button1, NULL);  
    ```  
  
### <a name="to-remove-a-tooltip-in-the-designer"></a><span data-ttu-id="8501d-117">若要在設計工具中移除的工具提示</span><span class="sxs-lookup"><span data-stu-id="8501d-117">To remove a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="8501d-118">選取顯示工具提示控制項。</span><span class="sxs-lookup"><span data-stu-id="8501d-118">Select the control that is displaying the ToolTip.</span></span>  
  
2.  <span data-ttu-id="8501d-119">在 [**屬性**] 視窗中，刪除中的文字**ToolTip1 的**。</span><span class="sxs-lookup"><span data-stu-id="8501d-119">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="8501d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8501d-120">See also</span></span>

- [<span data-ttu-id="8501d-121">ToolTip 元件概觀</span><span class="sxs-lookup"><span data-stu-id="8501d-121">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="8501d-122">HOW TO：變更 Windows Forms ToolTip 元件的延遲時間</span><span class="sxs-lookup"><span data-stu-id="8501d-122">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="8501d-123">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="8501d-123">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
