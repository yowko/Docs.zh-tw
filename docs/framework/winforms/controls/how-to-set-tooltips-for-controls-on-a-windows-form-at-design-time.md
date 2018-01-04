---
title: "如何：在設計階段設定 Windows Form 上控制項的工具提示"
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
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b296dc6ce929733d6e076cfa676ea6ab5624f45c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="dff42-102">如何：在設計階段設定 Windows Form 上控制項的工具提示</span><span class="sxs-lookup"><span data-stu-id="dff42-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="dff42-103">您可以設定<xref:System.Windows.Forms.ToolTip>字串在程式碼中或在 Windows Form 設計工具。</span><span class="sxs-lookup"><span data-stu-id="dff42-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="dff42-104">如需有關<xref:System.Windows.Forms.ToolTip>元件，請參閱[ToolTip 元件概觀](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="dff42-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dff42-105">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="dff42-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="dff42-106">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="dff42-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="dff42-107">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="dff42-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="dff42-108">以程式設計方式設定工具提示</span><span class="sxs-lookup"><span data-stu-id="dff42-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="dff42-109">新增控制項，將會顯示工具提示。</span><span class="sxs-lookup"><span data-stu-id="dff42-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="dff42-110">使用<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>方法<xref:System.Windows.Forms.ToolTip>元件。</span><span class="sxs-lookup"><span data-stu-id="dff42-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
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
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="dff42-111">在設計工具中設定工具提示</span><span class="sxs-lookup"><span data-stu-id="dff42-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="dff42-112">新增 <xref:System.Windows.Forms.ToolTip> 元件至表單。</span><span class="sxs-lookup"><span data-stu-id="dff42-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="dff42-113">選取的控制項，會顯示工具提示中，或將它加入至表單。</span><span class="sxs-lookup"><span data-stu-id="dff42-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="dff42-114">在**屬性**視窗中，將**ToolTip1 的**適當的文字字串的值。</span><span class="sxs-lookup"><span data-stu-id="dff42-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dff42-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="dff42-115">See Also</span></span>  
 [<span data-ttu-id="dff42-116">ToolTip 元件概觀</span><span class="sxs-lookup"><span data-stu-id="dff42-116">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [<span data-ttu-id="dff42-117">操作說明：變更 Windows Forms ToolTip 元件的延遲時間</span><span class="sxs-lookup"><span data-stu-id="dff42-117">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [<span data-ttu-id="dff42-118">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="dff42-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
