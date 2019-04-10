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
ms.openlocfilehash: fb6c8a7d62aa09a6e1d82cb4079d1425a7f39f8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160729"
---
# <a name="how-to-get-or-set-a-dock-value"></a><span data-ttu-id="2e5f0-102">HOW TO：取得或設定 Dock 值</span><span class="sxs-lookup"><span data-stu-id="2e5f0-102">How to: Get or Set a Dock Value</span></span>
<span data-ttu-id="2e5f0-103">下列範例示範如何指派<xref:System.Windows.Controls.Dock>物件的值。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-103">The following example shows how to assign a <xref:System.Windows.Controls.Dock> value for an object.</span></span> <span data-ttu-id="2e5f0-104">此範例會使用<xref:System.Windows.Controls.DockPanel.GetDock%2A>並<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-104">The example uses the <xref:System.Windows.Controls.DockPanel.GetDock%2A> and <xref:System.Windows.Controls.DockPanel.SetDock%2A> methods of <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e5f0-105">範例</span><span class="sxs-lookup"><span data-stu-id="2e5f0-105">Example</span></span>  
 <span data-ttu-id="2e5f0-106">此範例會建立的執行個體<xref:System.Windows.Controls.TextBlock>項目， `txt1`，並指派<xref:System.Windows.Controls.Dock>的值`Top`利用<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-106">The example creates an instance of the <xref:System.Windows.Controls.TextBlock> element, `txt1`, and assigns a <xref:System.Windows.Controls.Dock> value of `Top` by using the <xref:System.Windows.Controls.DockPanel.SetDock%2A> method of <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="2e5f0-107">然後將附加的值<xref:System.Windows.Controls.Dock>屬性，以<xref:System.Windows.Controls.TextBlock.Text%2A>的<xref:System.Windows.Controls.TextBlock>使用的項目<xref:System.Windows.Controls.DockPanel.GetDock%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-107">It then appends the value of the <xref:System.Windows.Controls.Dock> property to the <xref:System.Windows.Controls.TextBlock.Text%2A> of the <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.DockPanel.GetDock%2A> method.</span></span> <span data-ttu-id="2e5f0-108">最後，範例會新增<xref:System.Windows.Controls.TextBlock>父系的項目<xref:System.Windows.Controls.DockPanel>， `dp1`。</span><span class="sxs-lookup"><span data-stu-id="2e5f0-108">Finally, the example adds the <xref:System.Windows.Controls.TextBlock> element to the parent <xref:System.Windows.Controls.DockPanel>, `dp1`.</span></span>  
  
 [!code-csharp[DockPanelSetDock#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2e5f0-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e5f0-109">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.DockPanel.GetDock%2A>
- <xref:System.Windows.Controls.DockPanel.SetDock%2A>
- [<span data-ttu-id="2e5f0-110">面板概觀</span><span class="sxs-lookup"><span data-stu-id="2e5f0-110">Panels Overview</span></span>](panels-overview.md)
