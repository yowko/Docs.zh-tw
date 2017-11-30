---
title: "如何：在 StackPanel 和 DockPanel 之間選擇"
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
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 40d99e090a0599c98560e4102d18d35ee7174259
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a><span data-ttu-id="7a376-102">如何：在 StackPanel 和 DockPanel 之間選擇</span><span class="sxs-lookup"><span data-stu-id="7a376-102">How to: Choose Between StackPanel and DockPanel</span></span>
<span data-ttu-id="7a376-103">這個範例示範如何使用之間選擇<xref:System.Windows.Controls.StackPanel>或<xref:System.Windows.Controls.DockPanel>您堆疊內容中的，當<xref:System.Windows.Controls.Panel>。</span><span class="sxs-lookup"><span data-stu-id="7a376-103">This example shows how to choose between using a <xref:System.Windows.Controls.StackPanel> or a <xref:System.Windows.Controls.DockPanel> when you stack content in a <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a376-104">範例</span><span class="sxs-lookup"><span data-stu-id="7a376-104">Example</span></span>  
 <span data-ttu-id="7a376-105">雖然您可以使用<xref:System.Windows.Controls.DockPanel>或<xref:System.Windows.Controls.StackPanel>來堆疊子項目，兩個控制項不一定會產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="7a376-105">Although you can use either <xref:System.Windows.Controls.DockPanel> or <xref:System.Windows.Controls.StackPanel> to stack child elements, the two controls do not always produce the same results.</span></span> <span data-ttu-id="7a376-106">例如，您將項目子系順序可能會影響中子項目的大小<xref:System.Windows.Controls.DockPanel>但無法在<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="7a376-106">For example, the order that you place child elements can affect the size of child elements in a <xref:System.Windows.Controls.DockPanel> but not in a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="7a376-107">不同的行為就會發生<xref:System.Windows.Controls.StackPanel>方向在堆疊中的量值<xref:System.Double>。<xref:System.Double.PositiveInfinity>; 不過，<xref:System.Windows.Controls.DockPanel>量值使用的大小。</span><span class="sxs-lookup"><span data-stu-id="7a376-107">This different behavior occurs because <xref:System.Windows.Controls.StackPanel> measures in the direction of stacking at <xref:System.Double>.<xref:System.Double.PositiveInfinity>; however, <xref:System.Windows.Controls.DockPanel> measures only the available size.</span></span>  
  
 <span data-ttu-id="7a376-108">下列範例會示範這個之間的主要差異<xref:System.Windows.Controls.DockPanel>和<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="7a376-108">The following example demonstrates this key difference between <xref:System.Windows.Controls.DockPanel> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7a376-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a376-109">See Also</span></span>  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.DockPanel>  
 [<span data-ttu-id="7a376-110">面板概觀</span><span class="sxs-lookup"><span data-stu-id="7a376-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
