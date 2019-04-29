---
title: HOW TO：變更 Windows Forms ToolTip 元件的延遲時間
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: cf257cccd272c16c3d7c3d403456265444fc8ac8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781234"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="11858-102">HOW TO：變更 Windows Forms ToolTip 元件的延遲時間</span><span class="sxs-lookup"><span data-stu-id="11858-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="11858-103">有多個您可以設定 Windows Form 的延遲值<xref:System.Windows.Forms.ToolTip>元件。</span><span class="sxs-lookup"><span data-stu-id="11858-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="11858-104">所有這些屬性的測量單位為毫秒。</span><span class="sxs-lookup"><span data-stu-id="11858-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="11858-105"><xref:System.Windows.Forms.ToolTip.InitialDelay%2A>屬性會決定使用者必須指向相關聯的控制項才會出現工具提示字串的時間長度。</span><span class="sxs-lookup"><span data-stu-id="11858-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="11858-106"><xref:System.Windows.Forms.ToolTip.ReshowDelay%2A>屬性會設定後續的工具提示字串，以顯示當滑鼠移動到另一個工具提示相關聯的控制項中所花費的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="11858-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="11858-107"><xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A>屬性會決定的工具提示字串會顯示的時間長度。</span><span class="sxs-lookup"><span data-stu-id="11858-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="11858-108">您可以個別或藉由設定的值來設定這些值<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>屬性; 屬性會根據設定的值指派給其他延遲<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="11858-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="11858-109">例如，當<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>設為值 N，<xref:System.Windows.Forms.ToolTip.InitialDelay%2A>設定為 N，<xref:System.Windows.Forms.ToolTip.ReshowDelay%2A>設定的值為<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>除以五個 （或 N/5），並<xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A>值是五倍的值，這個值會設<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>屬性 （或 5N）。</span><span class="sxs-lookup"><span data-stu-id="11858-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="11858-110">若要設定的延遲</span><span class="sxs-lookup"><span data-stu-id="11858-110">To set the delay</span></span>  
  
1. <span data-ttu-id="11858-111">在此範例中所示，請設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="11858-111">Set the following properties as shown in this example.</span></span>  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="11858-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11858-112">See also</span></span>

- [<span data-ttu-id="11858-113">ToolTip 元件概觀</span><span class="sxs-lookup"><span data-stu-id="11858-113">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="11858-114">如何：在設計階段設定 Windows Form 上控制項的工具提示</span><span class="sxs-lookup"><span data-stu-id="11858-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [<span data-ttu-id="11858-115">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="11858-115">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
