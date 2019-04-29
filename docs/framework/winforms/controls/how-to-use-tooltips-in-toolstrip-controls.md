---
title: HOW TO：在 ToolStrip 控制項使用工具提示
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: ffaf859fafc87131de525f7bf2f52db421a208c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785745"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="d3ced-102">HOW TO：在 ToolStrip 控制項使用工具提示</span><span class="sxs-lookup"><span data-stu-id="d3ced-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="d3ced-103">您可以顯示<xref:System.Windows.Forms.ToolTip>for<xref:System.Windows.Forms.ToolStrip>您想要藉由設定控制項的控制項<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="d3ced-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="d3ced-104">若要顯示工具提示</span><span class="sxs-lookup"><span data-stu-id="d3ced-104">To display a ToolTip</span></span>  
  
- <span data-ttu-id="d3ced-105">設定<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>屬性來控制`true`。</span><span class="sxs-lookup"><span data-stu-id="d3ced-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="d3ced-106">預設值<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType>已`true`，和預設值<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType>並<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType>是`false`。</span><span class="sxs-lookup"><span data-stu-id="d3ced-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="d3ced-107">要用於工具提示文字的 prvek ToolStripButton ToolTipText 屬性</span><span class="sxs-lookup"><span data-stu-id="d3ced-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1. <span data-ttu-id="d3ced-108">設定<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>屬性的按鈕`true`。</span><span class="sxs-lookup"><span data-stu-id="d3ced-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2. <span data-ttu-id="d3ced-109">設定<xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType>屬性的按鈕`false`。</span><span class="sxs-lookup"><span data-stu-id="d3ced-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="d3ced-110">`AutoToolTip`屬性是`true`的預設<xref:System.Windows.Forms.ToolStripButton>， <xref:System.Windows.Forms.ToolStripDropDownButton>，和<xref:System.Windows.Forms.ToolStripSplitButton>。</span><span class="sxs-lookup"><span data-stu-id="d3ced-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="d3ced-111">A<xref:System.Windows.Forms.ToolStripButton>會使用其`Text`屬性<xref:System.Windows.Forms.ToolTip>預設的文字。</span><span class="sxs-lookup"><span data-stu-id="d3ced-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="d3ced-112">使用此程序顯示自訂的文字<xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>。</span><span class="sxs-lookup"><span data-stu-id="d3ced-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3ced-113">如果您設定<xref:System.Windows.Forms.ToolStripItemDisplayStyle>要<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>或<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>，沒有文字會出現在 [] 按鈕，但仍會顯示工具提示。</span><span class="sxs-lookup"><span data-stu-id="d3ced-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ced-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3ced-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [<span data-ttu-id="d3ced-115">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="d3ced-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
