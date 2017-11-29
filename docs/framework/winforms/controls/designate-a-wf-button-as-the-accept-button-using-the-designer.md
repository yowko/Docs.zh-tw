---
title: "如何：使用設計工具將 Windows Form 按鈕指定為接受按鈕"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 044fa4ab2e9a37038e9db9a2784fad4190713806
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="61e1a-102">如何：使用設計工具將 Windows Form 按鈕指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="61e1a-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="61e1a-103">您可以在任何 Windows 表單上，指定<xref:System.Windows.Forms.Button>控制項為接受按鈕，也稱為預設按鈕。</span><span class="sxs-lookup"><span data-stu-id="61e1a-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="61e1a-104">每當使用者按下 ENTER 鍵，是按下無論哪個表單上的其他控制項具有焦點的預設按鈕。</span><span class="sxs-lookup"><span data-stu-id="61e1a-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="61e1a-105">例外狀況是另一個按鈕具有焦點的控制項時，會在此情況下，按一下具有焦點按鈕，或多行文字方塊中或自訂控制項的 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="61e1a-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61e1a-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="61e1a-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="61e1a-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="61e1a-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="61e1a-108">如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。</span><span class="sxs-lookup"><span data-stu-id="61e1a-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="61e1a-109">若要指定接受按鈕</span><span class="sxs-lookup"><span data-stu-id="61e1a-109">To designate the accept button</span></span>  
  
1.  <span data-ttu-id="61e1a-110">選取按鈕所在的表單。</span><span class="sxs-lookup"><span data-stu-id="61e1a-110">Select the form on which the button resides.</span></span>  
  
2.  <span data-ttu-id="61e1a-111">在**屬性**視窗中，將表單的<xref:System.Windows.Forms.Form.AcceptButton%2A>屬性<xref:System.Windows.Forms.Button>控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="61e1a-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e1a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61e1a-112">See Also</span></span>  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [<span data-ttu-id="61e1a-113">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="61e1a-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="61e1a-114">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="61e1a-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="61e1a-115">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="61e1a-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="61e1a-116">操作說明：使用設計工具將 Windows Forms 按鈕指定為取消按鈕</span><span class="sxs-lookup"><span data-stu-id="61e1a-116">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="61e1a-117">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="61e1a-117">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
