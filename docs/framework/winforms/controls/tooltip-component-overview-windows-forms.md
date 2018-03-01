---
title: "ToolTip 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fce1cb5750197e52461b4883f1238325fa10fc5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="tooltip-component-overview-windows-forms"></a><span data-ttu-id="9d750-102">ToolTip 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="9d750-102">ToolTip Component Overview (Windows Forms)</span></span>
<span data-ttu-id="9d750-103">當使用者指向控制項時，Windows Form <xref:System.Windows.Forms.ToolTip> 元件會顯示文字。</span><span class="sxs-lookup"><span data-stu-id="9d750-103">The Windows Forms <xref:System.Windows.Forms.ToolTip> component displays text when the user points at controls.</span></span> <span data-ttu-id="9d750-104">工具提示可以與任何控制項產生關聯。</span><span class="sxs-lookup"><span data-stu-id="9d750-104">A ToolTip can be associated with any control.</span></span> <span data-ttu-id="9d750-105">使用此元件的範例： 為了節省空間，在表單上，您可以在按鈕上顯示小圖示，並使用工具提示說明按鈕的功能。</span><span class="sxs-lookup"><span data-stu-id="9d750-105">An example use of this component: to save space on a form, you can display a small icon on a button and use a ToolTip to explain the button's function.</span></span>  
  
## <a name="working-with-the-tooltip-component"></a><span data-ttu-id="9d750-106">使用 ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="9d750-106">Working with the ToolTip Component</span></span>  
 <span data-ttu-id="9d750-107">A<xref:System.Windows.Forms.ToolTip>元件提供`ToolTip`Windows 表單或其他容器上的多個控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="9d750-107">A <xref:System.Windows.Forms.ToolTip> component provides a `ToolTip` property to multiple controls on a Windows Form or other container.</span></span> <span data-ttu-id="9d750-108">例如，如果您將其中一個<xref:System.Windows.Forms.ToolTip>表單上的元件，您可以顯示為 「 類型名稱 」<xref:System.Windows.Forms.TextBox>控制和"按一下這裡以儲存變更"的<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="9d750-108">For example, if you place one <xref:System.Windows.Forms.ToolTip> component on a form, you can display "Type your name here" for a <xref:System.Windows.Forms.TextBox> control and "Click here to save changes" for a <xref:System.Windows.Forms.Button> control.</span></span>  
  
 <span data-ttu-id="9d750-109">主要方法<xref:System.Windows.Forms.ToolTip>元件是<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>和<xref:System.Windows.Forms.ToolTip.GetToolTip%2A>。</span><span class="sxs-lookup"><span data-stu-id="9d750-109">The key methods of the <xref:System.Windows.Forms.ToolTip> component are <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> and <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span></span> <span data-ttu-id="9d750-110">您可以使用<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>方法，以設定控制項顯示的工具提示。</span><span class="sxs-lookup"><span data-stu-id="9d750-110">You can use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method to set the ToolTips displayed for controls.</span></span> <span data-ttu-id="9d750-111">如需詳細資訊，請參閱[How to： 在設計階段的 Windows Form 上控制項的 設定工具提示](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="9d750-111">For more information, see [How to: Set ToolTips for Controls on a Windows Form at Design Time](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span></span> <span data-ttu-id="9d750-112">索引鍵屬性是<xref:System.Windows.Forms.ToolTip.Active%2A>，且必須設為`true`才會出現，工具提示和<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>、 可設定的工具提示字串會顯示的時間長度、 多久才會出現，工具提示控制項必須指向使用者和時間的方式會針對後續工具提示視窗出現。</span><span class="sxs-lookup"><span data-stu-id="9d750-112">The key properties are <xref:System.Windows.Forms.ToolTip.Active%2A>, which must be set to `true` for the ToolTip to appear, and <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, which sets the length of time that the ToolTip string is shown, how long the user must point at the control for the ToolTip to appear, and how long it takes for subsequent ToolTip windows to appear.</span></span> <span data-ttu-id="9d750-113">如需詳細資訊，請參閱[如何： 變更 Windows Form ToolTip 元件的延遲](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)。</span><span class="sxs-lookup"><span data-stu-id="9d750-113">For more information, see [How to: Change the Delay of the Windows Forms ToolTip Component](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d750-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="9d750-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolTip>  
 [<span data-ttu-id="9d750-115">操作說明：在設計階段設定 Windows Forms 上控制項的工具提示</span><span class="sxs-lookup"><span data-stu-id="9d750-115">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [<span data-ttu-id="9d750-116">操作說明：變更 Windows Forms ToolTip 元件的延遲時間</span><span class="sxs-lookup"><span data-stu-id="9d750-116">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
