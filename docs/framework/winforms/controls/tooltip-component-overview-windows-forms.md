---
title: ToolTip 元件概觀
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 731f7ad0ce6670000d8c3d3e901e1506f7ef470a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741911"
---
# <a name="tooltip-component-overview-windows-forms"></a><span data-ttu-id="7c92d-102">ToolTip 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="7c92d-102">ToolTip Component Overview (Windows Forms)</span></span>
<span data-ttu-id="7c92d-103">當使用者指向控制項時，Windows Form <xref:System.Windows.Forms.ToolTip> 元件會顯示文字。</span><span class="sxs-lookup"><span data-stu-id="7c92d-103">The Windows Forms <xref:System.Windows.Forms.ToolTip> component displays text when the user points at controls.</span></span> <span data-ttu-id="7c92d-104">工具提示可以與任何控制項產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7c92d-104">A ToolTip can be associated with any control.</span></span> <span data-ttu-id="7c92d-105">使用此元件的範例：若要在表單上儲存空間，您可以在按鈕上顯示一個小圖示，並使用工具提示來說明按鈕的功能。</span><span class="sxs-lookup"><span data-stu-id="7c92d-105">An example use of this component: to save space on a form, you can display a small icon on a button and use a ToolTip to explain the button's function.</span></span>  
  
## <a name="working-with-the-tooltip-component"></a><span data-ttu-id="7c92d-106">使用工具提示元件</span><span class="sxs-lookup"><span data-stu-id="7c92d-106">Working with the ToolTip Component</span></span>  
 <span data-ttu-id="7c92d-107"><xref:System.Windows.Forms.ToolTip> 元件會提供 `ToolTip` 屬性給 Windows Form 或其他容器上的多個控制項。</span><span class="sxs-lookup"><span data-stu-id="7c92d-107">A <xref:System.Windows.Forms.ToolTip> component provides a `ToolTip` property to multiple controls on a Windows Form or other container.</span></span> <span data-ttu-id="7c92d-108">例如，如果您將一個 <xref:System.Windows.Forms.ToolTip> 元件放在表單上，您可以在 <xref:System.Windows.Forms.TextBox> 控制項中顯示「在此輸入您的名稱」，然後在 <xref:System.Windows.Forms.Button> 控制項中，針對 [按一下這裡儲存變更]。</span><span class="sxs-lookup"><span data-stu-id="7c92d-108">For example, if you place one <xref:System.Windows.Forms.ToolTip> component on a form, you can display "Type your name here" for a <xref:System.Windows.Forms.TextBox> control and "Click here to save changes" for a <xref:System.Windows.Forms.Button> control.</span></span>  
  
 <span data-ttu-id="7c92d-109"><xref:System.Windows.Forms.ToolTip> 元件的主要方法是 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 和 <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>。</span><span class="sxs-lookup"><span data-stu-id="7c92d-109">The key methods of the <xref:System.Windows.Forms.ToolTip> component are <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> and <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span></span> <span data-ttu-id="7c92d-110">您可以使用 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 方法來設定針對控制項顯示的工具提示。</span><span class="sxs-lookup"><span data-stu-id="7c92d-110">You can use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method to set the ToolTips displayed for controls.</span></span> <span data-ttu-id="7c92d-111">如需詳細資訊，請參閱[如何：在設計階段設定 Windows Form 上控制項的工具提示](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="7c92d-111">For more information, see [How to: Set ToolTips for Controls on a Windows Form at Design Time](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span></span> <span data-ttu-id="7c92d-112">索引鍵屬性是 <xref:System.Windows.Forms.ToolTip.Active%2A>的，其必須設定為 `true`，工具提示才會出現，而 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>則會設定顯示工具提示字串的時間長度、使用者必須指向控制項以顯示工具提示，以及後續工具提示視窗出現的時間長短。</span><span class="sxs-lookup"><span data-stu-id="7c92d-112">The key properties are <xref:System.Windows.Forms.ToolTip.Active%2A>, which must be set to `true` for the ToolTip to appear, and <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, which sets the length of time that the ToolTip string is shown, how long the user must point at the control for the ToolTip to appear, and how long it takes for subsequent ToolTip windows to appear.</span></span> <span data-ttu-id="7c92d-113">如需詳細資訊，請參閱[如何：變更 Windows Forms 工具提示元件的延遲](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)。</span><span class="sxs-lookup"><span data-stu-id="7c92d-113">For more information, see [How to: Change the Delay of the Windows Forms ToolTip Component](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c92d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c92d-114">See also</span></span>

- <xref:System.Windows.Forms.ToolTip>
- [<span data-ttu-id="7c92d-115">操作說明：在設計階段設定 Windows Forms 上控制項的工具提示</span><span class="sxs-lookup"><span data-stu-id="7c92d-115">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [<span data-ttu-id="7c92d-116">操作說明：變更 Windows Forms ToolTip 元件的延遲時間</span><span class="sxs-lookup"><span data-stu-id="7c92d-116">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
