---
title: HOW TO：使用設計工具將 Windows Forms 的按鈕指定為取消按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: cc352f15fb1e8b531cd0f9b298b2db4ce649d3cf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039640"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="dbc6b-102">作法：使用設計工具將 Windows Forms 的按鈕指定為取消按鈕</span><span class="sxs-lookup"><span data-stu-id="dbc6b-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="dbc6b-103">在任何 Windows Form 上, 您可以將<xref:System.Windows.Forms.Button>控制項指定為 [取消] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="dbc6b-104">每當使用者按下 ESC 鍵時, 就會按一下 [取消] 按鈕, 而不論表單上的其他控制項有哪些焦點。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="dbc6b-105">這類按鈕通常是程式設計的, 可讓使用者快速結束作業, 而不需要認可任何動作。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>

## <a name="to-designate-the-cancel-button"></a><span data-ttu-id="dbc6b-106">若要指定取消按鈕</span><span class="sxs-lookup"><span data-stu-id="dbc6b-106">To designate the cancel button</span></span>

1. <span data-ttu-id="dbc6b-107">選取按鈕所在的表單。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="dbc6b-108">在 [**屬性**] 視窗中, 將窗<xref:System.Windows.Forms.Form.CancelButton%2A>體的屬性<xref:System.Windows.Forms.Button>設為控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbc6b-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbc6b-109">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="dbc6b-110">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="dbc6b-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="dbc6b-111">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="dbc6b-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="dbc6b-112">如何：回應 Windows Forms 按鈕點擊</span><span class="sxs-lookup"><span data-stu-id="dbc6b-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- <span data-ttu-id="dbc6b-113">[如何：使用設計工具將 Windows Forms 按鈕指定為 [接受] 按鈕](designate-a-wf-button-as-the-accept-button-using-the-designer.md)</span><span class="sxs-lookup"><span data-stu-id="dbc6b-113">[How to: Designate a Windows Forms Button as the Accept Button Using the Designer](designate-a-wf-button-as-the-accept-button-using-the-designer.md)</span></span>
- [<span data-ttu-id="dbc6b-114">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="dbc6b-114">Button Control</span></span>](button-control-windows-forms.md)
