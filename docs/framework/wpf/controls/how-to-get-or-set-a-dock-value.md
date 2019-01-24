---
title: HOW TO：取得或設定 Dock 值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
ms.openlocfilehash: 847f8732e1807ab2541d42fe720aacbecb034154
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738504"
---
# <a name="how-to-get-or-set-a-dock-value"></a><span data-ttu-id="e6346-102">HOW TO：取得或設定 Dock 值</span><span class="sxs-lookup"><span data-stu-id="e6346-102">How to: Get or Set a Dock Value</span></span>
<span data-ttu-id="e6346-103">下列範例示範如何指派<xref:System.Windows.Controls.Dock>物件的值。</span><span class="sxs-lookup"><span data-stu-id="e6346-103">The following example shows how to assign a <xref:System.Windows.Controls.Dock> value for an object.</span></span> <span data-ttu-id="e6346-104">此範例會使用<xref:System.Windows.Controls.DockPanel.GetDock%2A>並<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="e6346-104">The example uses the <xref:System.Windows.Controls.DockPanel.GetDock%2A> and <xref:System.Windows.Controls.DockPanel.SetDock%2A> methods of <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6346-105">範例</span><span class="sxs-lookup"><span data-stu-id="e6346-105">Example</span></span>  
 <span data-ttu-id="e6346-106">此範例會建立的執行個體<xref:System.Windows.Controls.TextBlock>項目， `txt1`，並指派<xref:System.Windows.Controls.Dock>的值`Top`利用<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="e6346-106">The example creates an instance of the <xref:System.Windows.Controls.TextBlock> element, `txt1`, and assigns a <xref:System.Windows.Controls.Dock> value of `Top` by using the <xref:System.Windows.Controls.DockPanel.SetDock%2A> method of <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="e6346-107">然後將附加的值<xref:System.Windows.Controls.Dock>屬性，以<xref:System.Windows.Controls.TextBlock.Text%2A>的<xref:System.Windows.Controls.TextBlock>使用的項目<xref:System.Windows.Controls.DockPanel.GetDock%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e6346-107">It then appends the value of the <xref:System.Windows.Controls.Dock> property to the <xref:System.Windows.Controls.TextBlock.Text%2A> of the <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.DockPanel.GetDock%2A> method.</span></span> <span data-ttu-id="e6346-108">最後，範例會新增<xref:System.Windows.Controls.TextBlock>父系的項目<xref:System.Windows.Controls.DockPanel>， `dp1`。</span><span class="sxs-lookup"><span data-stu-id="e6346-108">Finally, the example adds the <xref:System.Windows.Controls.TextBlock> element to the parent <xref:System.Windows.Controls.DockPanel>, `dp1`.</span></span>  
  
 [!code-csharp[DockPanelSetDock#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e6346-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6346-109">See also</span></span>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.DockPanel.GetDock%2A>
- <xref:System.Windows.Controls.DockPanel.SetDock%2A>
- [<span data-ttu-id="e6346-110">面板概觀</span><span class="sxs-lookup"><span data-stu-id="e6346-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
