---
title: HOW TO：在 StackPanel 和 DockPanel 之間選擇
ms.date: 03/30/2017
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
ms.openlocfilehash: 13353212589f99c9ad735761af60ab3eff6c9ad8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357582"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a><span data-ttu-id="f593d-102">HOW TO：在 StackPanel 和 DockPanel 之間選擇</span><span class="sxs-lookup"><span data-stu-id="f593d-102">How to: Choose Between StackPanel and DockPanel</span></span>
<span data-ttu-id="f593d-103">此範例示範如何使用之間選擇<xref:System.Windows.Controls.StackPanel>或是<xref:System.Windows.Controls.DockPanel>堆疊內容中的當<xref:System.Windows.Controls.Panel>。</span><span class="sxs-lookup"><span data-stu-id="f593d-103">This example shows how to choose between using a <xref:System.Windows.Controls.StackPanel> or a <xref:System.Windows.Controls.DockPanel> when you stack content in a <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f593d-104">範例</span><span class="sxs-lookup"><span data-stu-id="f593d-104">Example</span></span>  
 <span data-ttu-id="f593d-105">雖然您可以使用<xref:System.Windows.Controls.DockPanel>或<xref:System.Windows.Controls.StackPanel>來堆疊子項目，兩個控制項不一定會產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="f593d-105">Although you can use either <xref:System.Windows.Controls.DockPanel> or <xref:System.Windows.Controls.StackPanel> to stack child elements, the two controls do not always produce the same results.</span></span> <span data-ttu-id="f593d-106">例如，您將項目子系順序可能會影響中子項目的大小<xref:System.Windows.Controls.DockPanel>但未顯示於<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="f593d-106">For example, the order that you place child elements can affect the size of child elements in a <xref:System.Windows.Controls.DockPanel> but not in a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="f593d-107">不同的行為就會發生<xref:System.Windows.Controls.StackPanel>量值在堆疊的方向<xref:System.Double>。<xref:System.Double.PositiveInfinity>; 不過，<xref:System.Windows.Controls.DockPanel>量值使用的大小。</span><span class="sxs-lookup"><span data-stu-id="f593d-107">This different behavior occurs because <xref:System.Windows.Controls.StackPanel> measures in the direction of stacking at <xref:System.Double>.<xref:System.Double.PositiveInfinity>; however, <xref:System.Windows.Controls.DockPanel> measures only the available size.</span></span>  
  
 <span data-ttu-id="f593d-108">下列範例示範此之間的主要差異<xref:System.Windows.Controls.DockPanel>和<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="f593d-108">The following example demonstrates this key difference between <xref:System.Windows.Controls.DockPanel> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f593d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f593d-109">See also</span></span>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="f593d-110">面板概觀</span><span class="sxs-lookup"><span data-stu-id="f593d-110">Panels Overview</span></span>](panels-overview.md)
