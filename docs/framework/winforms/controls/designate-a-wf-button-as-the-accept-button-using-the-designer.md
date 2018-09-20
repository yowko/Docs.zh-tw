---
title: 如何：使用設計工具將 Windows Form 按鈕指定為接受按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: ca049e86ab53fbd84cb24e81b0a850050ec2823f
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492366"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="80ba3-102">如何：使用設計工具將 Windows Form 按鈕指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="80ba3-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="80ba3-103">在任何 Windows 表單上，您可以指定<xref:System.Windows.Forms.Button>設為接受按鈕，也就是預設按鈕的控制項。</span><span class="sxs-lookup"><span data-stu-id="80ba3-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="80ba3-104">每當使用者按下 ENTER 鍵，不論哪一個表單上的其他控制項具有焦點按一下預設按鈕。</span><span class="sxs-lookup"><span data-stu-id="80ba3-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="80ba3-105">例外狀況是另一個按鈕具有焦點的控制項時，會被按一下的按鈕，並將焦點放在此情況下，-多行文字方塊中或自訂控制項的設陷 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="80ba3-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80ba3-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="80ba3-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="80ba3-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="80ba3-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="80ba3-108">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="80ba3-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="80ba3-109">若要指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="80ba3-109">To designate the accept button</span></span>  
  
1.  <span data-ttu-id="80ba3-110">選取的按鈕所在的表單。</span><span class="sxs-lookup"><span data-stu-id="80ba3-110">Select the form on which the button resides.</span></span>  
  
2.  <span data-ttu-id="80ba3-111">在 [**屬性**] 視窗中，將表單的<xref:System.Windows.Forms.Form.AcceptButton%2A>屬性設<xref:System.Windows.Forms.Button>控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="80ba3-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ba3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80ba3-112">See Also</span></span>  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [<span data-ttu-id="80ba3-113">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="80ba3-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="80ba3-114">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="80ba3-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="80ba3-115">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="80ba3-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="80ba3-116">操作說明：使用設計工具將 Windows Forms 按鈕指定為取消按鈕</span><span class="sxs-lookup"><span data-stu-id="80ba3-116">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="80ba3-117">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="80ba3-117">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
