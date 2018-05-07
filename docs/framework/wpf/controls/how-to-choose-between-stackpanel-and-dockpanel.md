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
ms.openlocfilehash: c9bfb8d29051a9cfa61d3fcb93b8bb9a68d14e00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>如何：在 StackPanel 和 DockPanel 之間選擇
這個範例示範如何使用之間選擇<xref:System.Windows.Controls.StackPanel>或<xref:System.Windows.Controls.DockPanel>您堆疊內容中的，當<xref:System.Windows.Controls.Panel>。  
  
## <a name="example"></a>範例  
 雖然您可以使用<xref:System.Windows.Controls.DockPanel>或<xref:System.Windows.Controls.StackPanel>來堆疊子項目，兩個控制項不一定會產生相同的結果。 例如，您將項目子系順序可能會影響中子項目的大小<xref:System.Windows.Controls.DockPanel>但無法在<xref:System.Windows.Controls.StackPanel>。 不同的行為就會發生<xref:System.Windows.Controls.StackPanel>方向在堆疊中的量值<xref:System.Double>。<xref:System.Double.PositiveInfinity>; 不過，<xref:System.Windows.Controls.DockPanel>量值使用的大小。  
  
 下列範例會示範這個之間的主要差異<xref:System.Windows.Controls.DockPanel>和<xref:System.Windows.Controls.StackPanel>。  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.DockPanel>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)
