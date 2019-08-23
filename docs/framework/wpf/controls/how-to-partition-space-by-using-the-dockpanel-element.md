---
title: 作法：使用 DockPanel 元素分割空間
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
ms.openlocfilehash: d22a808ce3ab95e3b351408bf4cc372a335da553
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960191"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>作法：使用 DockPanel 元素分割空間
下列範例會<xref:System.Windows.Controls.DockPanel>使用元素來[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]建立簡單的架構。 分割<xref:System.Windows.Controls.DockPanel>區的可用空間可供其子項目使用。  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Windows.Controls.DockPanel.Dock%2A>屬性 (也就是附加屬性), 將兩個<xref:System.Windows.Controls.Border>完全相同的<xref:System.Windows.Controls.Dock.Top>元素固定在分割空間的上。 第三<xref:System.Windows.Controls.Border>個元素停駐<xref:System.Windows.Controls.Dock.Left>于, 其寬度設定為200圖元。 第四<xref:System.Windows.Controls.Border>個<xref:System.Windows.Controls.Dock.Bottom>停駐在螢幕的上。 最後一個<xref:System.Windows.Controls.Border>元素會自動填滿剩餘的空間。  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
> 根據預設, <xref:System.Windows.Controls.DockPanel>元素的最後一個子系會填滿剩餘的未配置空間。 如果您不想要有此行為，請設定 `LastChildFill="False"`。  
  
 編譯後的應用程式會產生一個看起來如下的新 UI。  
  
 ![典型的 DockPanel 案例。](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.DockPanel>
- [面板概觀](panels-overview.md)
