---
title: 如何：在 StackPanel 和 DockPanel 之間選擇
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
ms.openlocfilehash: bdf4b38e67a7856136224368e86609c135e5ad6f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976433"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a><span data-ttu-id="b8d83-102">如何：在 StackPanel 和 DockPanel 之間選擇</span><span class="sxs-lookup"><span data-stu-id="b8d83-102">How to: Choose Between StackPanel and DockPanel</span></span>
<span data-ttu-id="b8d83-103">這個範例示範當您在 <xref:System.Windows.Controls.Panel>中堆疊內容時，如何選擇使用 <xref:System.Windows.Controls.StackPanel> 或 <xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="b8d83-103">This example shows how to choose between using a <xref:System.Windows.Controls.StackPanel> or a <xref:System.Windows.Controls.DockPanel> when you stack content in a <xref:System.Windows.Controls.Panel>.</span></span>

## <a name="example"></a><span data-ttu-id="b8d83-104">範例</span><span class="sxs-lookup"><span data-stu-id="b8d83-104">Example</span></span>
 <span data-ttu-id="b8d83-105">雖然您可以使用 <xref:System.Windows.Controls.DockPanel> 或 <xref:System.Windows.Controls.StackPanel> 來堆疊子項目，但這兩個控制項不一定會產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="b8d83-105">Although you can use either <xref:System.Windows.Controls.DockPanel> or <xref:System.Windows.Controls.StackPanel> to stack child elements, the two controls do not always produce the same results.</span></span> <span data-ttu-id="b8d83-106">例如，您放置子專案的順序可能會影響 <xref:System.Windows.Controls.DockPanel> 中子專案的大小，但無法在 <xref:System.Windows.Controls.StackPanel>中。</span><span class="sxs-lookup"><span data-stu-id="b8d83-106">For example, the order that you place child elements can affect the size of child elements in a <xref:System.Windows.Controls.DockPanel> but not in a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="b8d83-107">之所以會發生這種不同的行為，是因為 <xref:System.Windows.Controls.StackPanel> 在[PositiveInfinity](xref:System.Double.PositiveInfinity)的堆疊方向測量。不過，<xref:System.Windows.Controls.DockPanel> 只會測量可用的大小。</span><span class="sxs-lookup"><span data-stu-id="b8d83-107">This different behavior occurs because <xref:System.Windows.Controls.StackPanel> measures in the direction of stacking at [Double.PositiveInfinity](xref:System.Double.PositiveInfinity); however, <xref:System.Windows.Controls.DockPanel> measures only the available size.</span></span>

 <span data-ttu-id="b8d83-108">下列範例示範 <xref:System.Windows.Controls.DockPanel> 和 <xref:System.Windows.Controls.StackPanel>之間的主要差異。</span><span class="sxs-lookup"><span data-stu-id="b8d83-108">The following example demonstrates this key difference between <xref:System.Windows.Controls.DockPanel> and <xref:System.Windows.Controls.StackPanel>.</span></span>

 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="b8d83-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="b8d83-109">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="b8d83-110">面板概觀</span><span class="sxs-lookup"><span data-stu-id="b8d83-110">Panels Overview</span></span>](panels-overview.md)
