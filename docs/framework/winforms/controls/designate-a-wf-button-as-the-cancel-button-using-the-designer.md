---
title: "如何：使用設計工具將 Windows Form 按鈕指定為取消按鈕"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 50289e090618d75576eecf2db87f85bd51159fb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="3c8c2-102">如何：使用設計工具將 Windows Form 按鈕指定為取消按鈕</span><span class="sxs-lookup"><span data-stu-id="3c8c2-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="3c8c2-103">您可以在任何 Windows 表單上，指定<xref:System.Windows.Forms.Button>控制項為取消按鈕。</span><span class="sxs-lookup"><span data-stu-id="3c8c2-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="3c8c2-104">每當使用者按下 ESC 鍵，不論哪表單上的其他控制項具有焦點時，請按一下 [取消] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3c8c2-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="3c8c2-105">這類按鈕通常被設計成可讓使用者快速結束作業，而不需認可任何動作。</span><span class="sxs-lookup"><span data-stu-id="3c8c2-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c8c2-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="3c8c2-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3c8c2-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="3c8c2-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3c8c2-108">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="3c8c2-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="3c8c2-109">若要指定 [取消] 按鈕</span><span class="sxs-lookup"><span data-stu-id="3c8c2-109">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="3c8c2-110">選取按鈕所在的表單。</span><span class="sxs-lookup"><span data-stu-id="3c8c2-110">Select the form on which the button resides.</span></span>  
  
2.  <span data-ttu-id="3c8c2-111">在**屬性**視窗中，將表單的<xref:System.Windows.Forms.Form.CancelButton%2A>屬性<xref:System.Windows.Forms.Button>控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="3c8c2-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c8c2-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c8c2-112">See Also</span></span>  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [<span data-ttu-id="3c8c2-113">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="3c8c2-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="3c8c2-114">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="3c8c2-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="3c8c2-115">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="3c8c2-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="3c8c2-116">操作說明：使用設計工具將 Windows Forms 按鈕指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="3c8c2-116">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="3c8c2-117">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="3c8c2-117">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
