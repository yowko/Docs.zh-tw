---
title: "最佳化效能：配置與設計"
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
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df87170b05f830916ef2f77fd4cb5a4abab42faa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-performance-layout-and-design"></a>最佳化效能：配置與設計
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的設計可能會因為在計算版面配置和驗證物件參考而產生不必要的額外負荷，進而影響其效能。 物件的建構，特別是在執行階段，可能會影響應用程式的效能特性。  
  
 本主題提供這些區域的效能建議。  
  
## <a name="layout"></a>配置  
 詞彙 「 配置傳遞 」 描述的程序的測量和排列的成員<xref:System.Windows.Controls.Panel>-衍生的子系，然後將它們在螢幕上繪製物件的集合。 配置傳遞是數學密集的程序，在集合中的子系數目愈大，需要的計算數目愈大。 例如，每次子系<xref:System.Windows.UIElement>集合中的物件變更它的位置，就有可能會觸發新的行程由配置系統。 由於物件特性與版面配置行為之間的密切關係，了解可以叫用版面配置系統的事件類型便很重要。 藉由盡可能減少版面配置傳遞中任何不必要的引動過程，您的應用程式效能會比較好。  
  
 版面配置系統會為集合中每個子成員完成兩個階段︰測量階段和排列階段。 每一個子物件會提供自己的覆寫的實作<xref:System.Windows.UIElement.Measure%2A>和<xref:System.Windows.UIElement.Arrange%2A>方法，才能提供它自己的特定配置行為。 簡單來說，版面配置是導致項目調整大小、定位並在螢幕上繪製的遞迴系統。  
  
-   子系<xref:System.Windows.UIElement>物件開始版面配置處理序的第一個具有測量其核心屬性。  
  
-   物件的<xref:System.Windows.FrameworkElement>屬性與相關的大小，例如<xref:System.Windows.FrameworkElement.Width%2A>， <xref:System.Windows.FrameworkElement.Height%2A>，和<xref:System.Windows.FrameworkElement.Margin%2A>，會進行評估。  
  
-   <xref:System.Windows.Controls.Panel>-套用的特定邏輯，例如<xref:System.Windows.Controls.DockPanel.Dock%2A>屬性<xref:System.Windows.Controls.DockPanel>，或<xref:System.Windows.Controls.StackPanel.Orientation%2A>屬性<xref:System.Windows.Controls.StackPanel>。  
  
-   在測量所有子物件之後，會排列 (或定位) 內容。  
  
-   子物件的集合會繪製到螢幕。  
  
 如果發生任何下列動作，會再次叫用配置傳遞流程︰  
  
-   子物件新增至集合。  
  
-   A<xref:System.Windows.FrameworkElement.LayoutTransform%2A>套用到子物件。  
  
-   <xref:System.Windows.UIElement.UpdateLayout%2A>方法呼叫的子物件。  
  
-   當發生在以中繼資料標示的相依性屬性值的變更會影響測量或排列階段時。  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>請盡可能使用最有效率的面板  
 版面配置處理序的複雜度直接根據配置行為<xref:System.Windows.Controls.Panel>-衍生您使用的項目。 例如，<xref:System.Windows.Controls.Grid>或<xref:System.Windows.Controls.StackPanel>控制項提供更多的功能比<xref:System.Windows.Controls.Canvas>控制項。 這種功能增加的代價是較高的效能成本。 不過，如果您不需要的功能，<xref:System.Windows.Controls.Grid>提供控制項，您應該使用成本較低的替代項目，例如<xref:System.Windows.Controls.Canvas>或自訂的面板。  
  
 如需詳細資訊，請參閱[面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)。  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>更新，而不是取代 RenderTransform  
 您可以更新<xref:System.Windows.Media.Transform>而不是取代的值為<xref:System.Windows.UIElement.RenderTransform%2A>屬性。 特別是在包含動畫的案例。 藉由更新現有<xref:System.Windows.Media.Transform>，避免 起始不必要的版面配置計算。  
  
### <a name="build-your-tree-top-down"></a>由上而下建置您的樹狀結構  
 在邏輯樹狀結構節點新增或移除節點時，會對節點之父代及其所有子系引發屬性失效。 因此，應該一律遵循由上而下的建構模式，以避免在已驗證的節點上發生不必要的失效成本。 下表顯示在之間建立樹狀結構由上而下和由下往上，其中的樹狀結構是 150 層與單一的執行速度<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Controls.DockPanel>每個層級。  
  
|**動作**|**樹狀結構建置 (毫秒)**|**轉譯 — 包括樹狀結構建置 (毫秒)**|  
|----------------|---------------------------------|-------------------------------------------------|  
|由下而上|366|454|  
|由上而下|11|96|  
  
 下列程式碼範例示範如何由上而下建立樹狀結構。  
  
 [!code-csharp[Performance#PerformanceSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 如需有關邏輯樹狀結構的詳細資訊，請參閱 [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)。  
  
## <a name="see-also"></a>請參閱  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [應用程式效能規劃](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [2D 圖形和影像處理](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [版面配置](../../../../docs/framework/wpf/advanced/layout.md)
