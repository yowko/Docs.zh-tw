---
title: 作法：使用設計工具將 Windows Forms 的按鈕指定為接受按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27ecb26c493232bcfb996d012f9760b7ef91e5b2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039663"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="35780-102">作法：使用設計工具將 Windows Forms 的按鈕指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="35780-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="35780-103">在任何 Windows Form 上, 您可以將<xref:System.Windows.Forms.Button>控制項指定為 [接受] 按鈕, 也稱為 [預設值] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="35780-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="35780-104">每當使用者按下 ENTER 鍵時, 不論表單上的其他控制項有焦點, 都會按一下 [預設] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="35780-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="35780-105">這種情況的例外狀況是當具有焦點的控制項是另一個按鈕時, 在此情況下, 將會按一下具有焦點的按鈕 (或多行文字方塊), 或陷印 ENTER 鍵的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="35780-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>

## <a name="to-designate-the-accept-button"></a><span data-ttu-id="35780-106">若要指定接受按鈕</span><span class="sxs-lookup"><span data-stu-id="35780-106">To designate the accept button</span></span>

1. <span data-ttu-id="35780-107">選取按鈕所在的表單。</span><span class="sxs-lookup"><span data-stu-id="35780-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="35780-108">在 [**屬性**] 視窗中, 將窗<xref:System.Windows.Forms.Form.AcceptButton%2A>體的屬性<xref:System.Windows.Forms.Button>設為控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="35780-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="35780-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35780-109">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="35780-110">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="35780-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="35780-111">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="35780-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="35780-112">如何：回應 Windows Forms 按鈕點擊</span><span class="sxs-lookup"><span data-stu-id="35780-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- <span data-ttu-id="35780-113">[如何：使用設計工具將 Windows Forms 按鈕指定為 [取消] 按鈕](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)</span><span class="sxs-lookup"><span data-stu-id="35780-113">[How to: Designate a Windows Forms Button as the Cancel Button Using the Designer](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)</span></span>
- [<span data-ttu-id="35780-114">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="35780-114">Button Control</span></span>](button-control-windows-forms.md)
