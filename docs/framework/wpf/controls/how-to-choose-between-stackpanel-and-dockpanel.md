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
ms.openlocfilehash: 8338421dfb1bea856c15edf9d324cec955584f9f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206963"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>HOW TO：在 StackPanel 和 DockPanel 之間選擇
此範例示範如何使用之間選擇<xref:System.Windows.Controls.StackPanel>或是<xref:System.Windows.Controls.DockPanel>堆疊內容中的當<xref:System.Windows.Controls.Panel>。  
  
## <a name="example"></a>範例  
 雖然您可以使用<xref:System.Windows.Controls.DockPanel>或<xref:System.Windows.Controls.StackPanel>來堆疊子項目，兩個控制項不一定會產生相同的結果。 例如，您將項目子系順序可能會影響中子項目的大小<xref:System.Windows.Controls.DockPanel>但未顯示於<xref:System.Windows.Controls.StackPanel>。 不同的行為就會發生<xref:System.Windows.Controls.StackPanel>量值在堆疊的方向<xref:System.Double>。<xref:System.Double.PositiveInfinity>; 不過，<xref:System.Windows.Controls.DockPanel>量值使用的大小。  
  
 下列範例示範此之間的主要差異<xref:System.Windows.Controls.DockPanel>和<xref:System.Windows.Controls.StackPanel>。  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [面板概觀](panels-overview.md)
