---
title: 如何：使用設計工具將 Windows Form 按鈕指定為取消按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: faffeafc0cbe67c3b40297144ec85acd94956da9
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46322404"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="f2f7a-102">如何：使用設計工具將 Windows Form 按鈕指定為取消按鈕</span><span class="sxs-lookup"><span data-stu-id="f2f7a-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="f2f7a-103">在任何 Windows 表單上，您可以指定<xref:System.Windows.Forms.Button>設為 [取消] 按鈕的控制項。</span><span class="sxs-lookup"><span data-stu-id="f2f7a-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="f2f7a-104">每當使用者按下 ESC 鍵，不論哪一個表單上的其他控制項具有焦點時，按一下 [取消] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f2f7a-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="f2f7a-105">這類按鈕通常被設計成讓使用者快速結束作業，而不需要認可至任何動作。</span><span class="sxs-lookup"><span data-stu-id="f2f7a-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2f7a-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="f2f7a-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f2f7a-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="f2f7a-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f2f7a-108">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="f2f7a-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="f2f7a-109">若要指定 [取消] 按鈕</span><span class="sxs-lookup"><span data-stu-id="f2f7a-109">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="f2f7a-110">選取的按鈕所在的表單。</span><span class="sxs-lookup"><span data-stu-id="f2f7a-110">Select the form on which the button resides.</span></span>  
  
2.  <span data-ttu-id="f2f7a-111">在 [**屬性**] 視窗中，將表單的<xref:System.Windows.Forms.Form.CancelButton%2A>屬性設<xref:System.Windows.Forms.Button>控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="f2f7a-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f7a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2f7a-112">See Also</span></span>  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [<span data-ttu-id="f2f7a-113">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="f2f7a-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="f2f7a-114">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="f2f7a-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="f2f7a-115">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="f2f7a-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="f2f7a-116">操作說明：使用設計工具將 Windows Forms 按鈕指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="f2f7a-116">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="f2f7a-117">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="f2f7a-117">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
