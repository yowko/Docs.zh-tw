---
title: "如何：取得或設定 Dock 值"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7d663acf446ee2f7a36fc2d0c8605c31a0f2a84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-or-set-a-dock-value"></a><span data-ttu-id="e8fb9-102">如何：取得或設定 Dock 值</span><span class="sxs-lookup"><span data-stu-id="e8fb9-102">How to: Get or Set a Dock Value</span></span>
<span data-ttu-id="e8fb9-103">下列範例示範如何指派<xref:System.Windows.Controls.Dock>物件的值。</span><span class="sxs-lookup"><span data-stu-id="e8fb9-103">The following example shows how to assign a <xref:System.Windows.Controls.Dock> value for an object.</span></span> <span data-ttu-id="e8fb9-104">此範例會使用<xref:System.Windows.Controls.DockPanel.GetDock%2A>和<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="e8fb9-104">The example uses the <xref:System.Windows.Controls.DockPanel.GetDock%2A> and <xref:System.Windows.Controls.DockPanel.SetDock%2A> methods of <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8fb9-105">範例</span><span class="sxs-lookup"><span data-stu-id="e8fb9-105">Example</span></span>  
 <span data-ttu-id="e8fb9-106">此範例會建立的執行個體<xref:System.Windows.Controls.TextBlock>項目， `txt1`，並將指派<xref:System.Windows.Controls.Dock>值`Top`使用<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="e8fb9-106">The example creates an instance of the <xref:System.Windows.Controls.TextBlock> element, `txt1`, and assigns a <xref:System.Windows.Controls.Dock> value of `Top` by using the <xref:System.Windows.Controls.DockPanel.SetDock%2A> method of <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="e8fb9-107">然後將附加的值<xref:System.Windows.Controls.Dock>屬性<xref:System.Windows.Controls.TextBlock.Text%2A>的<xref:System.Windows.Controls.TextBlock>所使用的項目<xref:System.Windows.Controls.DockPanel.GetDock%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e8fb9-107">It then appends the value of the <xref:System.Windows.Controls.Dock> property to the <xref:System.Windows.Controls.TextBlock.Text%2A> of the <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.DockPanel.GetDock%2A> method.</span></span> <span data-ttu-id="e8fb9-108">最後，範例會加入<xref:System.Windows.Controls.TextBlock>父代的項目<xref:System.Windows.Controls.DockPanel>， `dp1`。</span><span class="sxs-lookup"><span data-stu-id="e8fb9-108">Finally, the example adds the <xref:System.Windows.Controls.TextBlock> element to the parent <xref:System.Windows.Controls.DockPanel>, `dp1`.</span></span>  
  
 [!code-csharp[DockPanelSetDock#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e8fb9-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="e8fb9-109">See Also</span></span>  
 <xref:System.Windows.Controls.DockPanel>  
 <xref:System.Windows.Controls.DockPanel.GetDock%2A>  
 <xref:System.Windows.Controls.DockPanel.SetDock%2A>  
 [<span data-ttu-id="e8fb9-110">面板概觀</span><span class="sxs-lookup"><span data-stu-id="e8fb9-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
