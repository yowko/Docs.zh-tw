---
title: HOW TO：在 ToolStrip 控制項使用工具提示
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 3f383b6cccba7825637ea65a0e13280b91b406c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939737"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="7cd7d-102">HOW TO：在 ToolStrip 控制項使用工具提示</span><span class="sxs-lookup"><span data-stu-id="7cd7d-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="7cd7d-103">您可以藉由<xref:System.Windows.Forms.ToolTip>將控制項<xref:System.Windows.Forms.ToolStrip>的<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>屬性設定為`true`, 為您想要的控制項顯示。</span><span class="sxs-lookup"><span data-stu-id="7cd7d-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="7cd7d-104">若要顯示工具提示</span><span class="sxs-lookup"><span data-stu-id="7cd7d-104">To display a ToolTip</span></span>  
  
- <span data-ttu-id="7cd7d-105">將控制項<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>的屬性設為。 `true`</span><span class="sxs-lookup"><span data-stu-id="7cd7d-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="7cd7d-106">的<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType>預設值`false`為`true`, 且<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType>和<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType>的預設值為。</span><span class="sxs-lookup"><span data-stu-id="7cd7d-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="7cd7d-107">若要針對 ToolStripButton 的工具提示文字使用 ToolTipText 屬性</span><span class="sxs-lookup"><span data-stu-id="7cd7d-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1. <span data-ttu-id="7cd7d-108">將按鈕的`true` <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="7cd7d-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2. <span data-ttu-id="7cd7d-109">將按鈕的`false` <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType>屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="7cd7d-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="7cd7d-110">`AutoToolTip`屬性預設為<xref:System.Windows.Forms.ToolStripButton> 、<xref:System.Windows.Forms.ToolStripSplitButton>和。 `true` <xref:System.Windows.Forms.ToolStripDropDownButton></span><span class="sxs-lookup"><span data-stu-id="7cd7d-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="7cd7d-111">預設會針對`Text` <xref:System.Windows.Forms.ToolStripButton> 文字<xref:System.Windows.Forms.ToolTip>使用其屬性。</span><span class="sxs-lookup"><span data-stu-id="7cd7d-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="7cd7d-112">使用此程式可在中<xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>顯示自訂文字。</span><span class="sxs-lookup"><span data-stu-id="7cd7d-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7cd7d-113">如果您將<xref:System.Windows.Forms.ToolStripItemDisplayStyle>設定<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>為<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>或, 按鈕上不會出現任何文字, 但是工具提示仍然會出現。</span><span class="sxs-lookup"><span data-stu-id="7cd7d-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cd7d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cd7d-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [<span data-ttu-id="7cd7d-115">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="7cd7d-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
