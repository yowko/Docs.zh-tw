---
title: "如何：使用 ToolStrip 控制項中的工具提示"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bc52dd1b629829564532fd93650737f51e5d7f24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="678d5-102">如何：使用 ToolStrip 控制項中的工具提示</span><span class="sxs-lookup"><span data-stu-id="678d5-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="678d5-103">您可以顯示<xref:System.Windows.Forms.ToolTip>如<xref:System.Windows.Forms.ToolStrip>您想要藉由設定控制項的控制項<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="678d5-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="678d5-104">若要顯示的工具提示</span><span class="sxs-lookup"><span data-stu-id="678d5-104">To display a ToolTip</span></span>  
  
-   <span data-ttu-id="678d5-105">設定<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>控制項的屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="678d5-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="678d5-106">預設值<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType>是`true`的預設值和<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType>和<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType>是`false`。</span><span class="sxs-lookup"><span data-stu-id="678d5-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="678d5-107">若要使用工具提示文字的 ToolStripButton ToolTipText 屬性</span><span class="sxs-lookup"><span data-stu-id="678d5-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1.  <span data-ttu-id="678d5-108">設定<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>按鈕的屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="678d5-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2.  <span data-ttu-id="678d5-109">設定<xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType>按鈕的屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="678d5-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="678d5-110">`AutoToolTip`屬性是`true`預設<xref:System.Windows.Forms.ToolStripButton>， <xref:System.Windows.Forms.ToolStripDropDownButton>，和<xref:System.Windows.Forms.ToolStripSplitButton>。</span><span class="sxs-lookup"><span data-stu-id="678d5-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="678d5-111">A<xref:System.Windows.Forms.ToolStripButton>會使用其`Text`屬性<xref:System.Windows.Forms.ToolTip>預設文字。</span><span class="sxs-lookup"><span data-stu-id="678d5-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="678d5-112">使用此程序來顯示中的自訂文字<xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>。</span><span class="sxs-lookup"><span data-stu-id="678d5-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="678d5-113">如果您設定<xref:System.Windows.Forms.ToolStripItemDisplayStyle>至<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>或<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>，任何文字會出現在按鈕上，但仍會顯示工具提示。</span><span class="sxs-lookup"><span data-stu-id="678d5-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="678d5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="678d5-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
 <xref:System.Windows.Forms.ToolStripButton>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 <xref:System.Windows.Forms.ToolStripSplitButton>  
 [<span data-ttu-id="678d5-115">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="678d5-115">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
