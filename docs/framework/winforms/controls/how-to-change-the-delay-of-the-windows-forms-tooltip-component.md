---
title: 變更工具提示元件的延遲
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
ms.openlocfilehash: 8ab0b0760e8c82d752eaada19f14cae57fa63fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746584"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="abc12-102">如何：變更 Windows Form ToolTip 元件的延遲時間</span><span class="sxs-lookup"><span data-stu-id="abc12-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="abc12-103">您可以為 Windows Forms <xref:System.Windows.Forms.ToolTip> 元件設定多個延遲值。</span><span class="sxs-lookup"><span data-stu-id="abc12-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="abc12-104">所有這些屬性的測量單位為毫秒。</span><span class="sxs-lookup"><span data-stu-id="abc12-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="abc12-105">[<xref:System.Windows.Forms.ToolTip.InitialDelay%2A>] 屬性會決定使用者必須指向相關聯控制項的時間，才會出現工具提示字串。</span><span class="sxs-lookup"><span data-stu-id="abc12-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="abc12-106"><xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> 屬性會設定當滑鼠從一個工具提示相關聯的控制項移至另一個時，後續工具提示字串所需的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="abc12-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="abc12-107">[<xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A>] 屬性會決定工具提示字串的顯示時間長度。</span><span class="sxs-lookup"><span data-stu-id="abc12-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="abc12-108">您可以個別設定這些值，或藉由設定 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 屬性的值;其他延遲屬性則是根據指派給 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 屬性的值來設定。</span><span class="sxs-lookup"><span data-stu-id="abc12-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="abc12-109">例如，當 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 設定為 n 值時，<xref:System.Windows.Forms.ToolTip.InitialDelay%2A> 設定為 N，<xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> 設定為 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 除以五（或 N/5）的值，而 <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> 設定為 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 屬性（或5N）的五倍值。</span><span class="sxs-lookup"><span data-stu-id="abc12-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="abc12-110">若要設定延遲</span><span class="sxs-lookup"><span data-stu-id="abc12-110">To set the delay</span></span>  
  
1. <span data-ttu-id="abc12-111">設定下列屬性，如這個範例所示。</span><span class="sxs-lookup"><span data-stu-id="abc12-111">Set the following properties as shown in this example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="abc12-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="abc12-112">See also</span></span>

- [<span data-ttu-id="abc12-113">ToolTip 元件概觀</span><span class="sxs-lookup"><span data-stu-id="abc12-113">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="abc12-114">操作說明：在設計階段設定 Windows Forms 上控制項的工具提示</span><span class="sxs-lookup"><span data-stu-id="abc12-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [<span data-ttu-id="abc12-115">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="abc12-115">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
