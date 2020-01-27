---
title: 使用設計工具將按鈕指定為 [取消] 按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: 95d1139b6e339055f944ad0b0967a6d91283d49e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746047"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="ac87c-102">如何：使用設計工具將 Windows Form 按鈕指定為取消按鈕</span><span class="sxs-lookup"><span data-stu-id="ac87c-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="ac87c-103">在任何 Windows Form 上，您都可以將 <xref:System.Windows.Forms.Button> 控制項指定為 [取消] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ac87c-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="ac87c-104">每當使用者按下 ESC 鍵時，就會按一下 [取消] 按鈕，而不論表單上的其他控制項有哪些焦點。</span><span class="sxs-lookup"><span data-stu-id="ac87c-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="ac87c-105">這類按鈕通常是程式設計的，可讓使用者快速結束作業，而不需要認可任何動作。</span><span class="sxs-lookup"><span data-stu-id="ac87c-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>

## <a name="to-designate-the-cancel-button"></a><span data-ttu-id="ac87c-106">若要指定取消按鈕</span><span class="sxs-lookup"><span data-stu-id="ac87c-106">To designate the cancel button</span></span>

1. <span data-ttu-id="ac87c-107">選取按鈕所在的表單。</span><span class="sxs-lookup"><span data-stu-id="ac87c-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="ac87c-108">在 [**屬性**] 視窗中，將表單的 [<xref:System.Windows.Forms.Form.CancelButton%2A>] 屬性設定為 <xref:System.Windows.Forms.Button> 控制項的名稱。</span><span class="sxs-lookup"><span data-stu-id="ac87c-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac87c-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="ac87c-109">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="ac87c-110">Button 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="ac87c-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="ac87c-111">選取 Windows Forms Button 控制項的方法</span><span class="sxs-lookup"><span data-stu-id="ac87c-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="ac87c-112">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="ac87c-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="ac87c-113">如何：使用設計工具將 Windows Forms 按鈕指定為接受按鈕</span><span class="sxs-lookup"><span data-stu-id="ac87c-113">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [<span data-ttu-id="ac87c-114">Button 控制項</span><span class="sxs-lookup"><span data-stu-id="ac87c-114">Button Control</span></span>](button-control-windows-forms.md)
