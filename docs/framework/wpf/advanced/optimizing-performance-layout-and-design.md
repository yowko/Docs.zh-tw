---
title: 最佳化效能：版面配置與設計
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
ms.openlocfilehash: 8a76dd5de9f374d77345eeab3d259624546fed7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107064"
---
# <a name="optimizing-performance-layout-and-design"></a>最佳化效能：版面配置與設計
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的設計可能會因為在計算版面配置和驗證物件參考而產生不必要的額外負荷，進而影響其效能。 物件的建構，特別是在執行階段，可能會影響應用程式的效能特性。  
  
 本主題提供這些區域的效能建議。  
  
## <a name="layout"></a>配置  
 「 版面配置傳遞 」 一詞描述測量和排列成員的程序<xref:System.Windows.Controls.Panel>-衍生的子系，且然後螢幕上繪製它們的物件的集合。 配置傳遞是數學密集的程序，在集合中的子系數目愈大，需要的計算數目愈大。 例如，每次子系<xref:System.Windows.UIElement>集合中的物件變更位置時，它有可能觸發配置系統的新階段。 由於物件特性與版面配置行為之間的密切關係，了解可以叫用版面配置系統的事件類型便很重要。 藉由盡可能減少版面配置傳遞中任何不必要的引動過程，您的應用程式效能會比較好。  
  
 版面配置系統會為集合中每個子成員完成兩個階段︰測量階段和排列階段。 每個子物件會提供它自己的覆寫實的作<xref:System.Windows.UIElement.Measure%2A>和<xref:System.Windows.UIElement.Arrange%2A>方法，以便提供它自己的特定版面配置行為。 簡單來說，版面配置是導致項目調整大小、定位並在螢幕上繪製的遞迴系統。  
  
-   子系<xref:System.Windows.UIElement>物件開始版面配置程序會先測量其核心屬性。  
  
-   物件的<xref:System.Windows.FrameworkElement>大小，例如相關的屬性<xref:System.Windows.FrameworkElement.Width%2A>， <xref:System.Windows.FrameworkElement.Height%2A>，和<xref:System.Windows.FrameworkElement.Margin%2A>，會進行評估。  
  
-   <xref:System.Windows.Controls.Panel>-套用的特定邏輯，例如<xref:System.Windows.Controls.DockPanel.Dock%2A>的屬性<xref:System.Windows.Controls.DockPanel>，或有<xref:System.Windows.Controls.StackPanel.Orientation%2A>屬性<xref:System.Windows.Controls.StackPanel>。  
  
-   在測量所有子物件之後，會排列 (或定位) 內容。  
  
-   子物件的集合會繪製到螢幕。  
  
 如果發生任何下列動作，會再次叫用配置傳遞流程︰  
  
-   子物件新增至集合。  
  
-   A<xref:System.Windows.FrameworkElement.LayoutTransform%2A>套用至子物件。  
  
-   <xref:System.Windows.UIElement.UpdateLayout%2A>子物件呼叫方法。  
  
-   當發生在以中繼資料標示的相依性屬性值的變更會影響測量或排列階段時。  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>請盡可能使用最有效率的面板  
 版面配置程序的複雜性直接根據版面配置行為<xref:System.Windows.Controls.Panel>-衍生您所使用的項目。 例如，<xref:System.Windows.Controls.Grid>或是<xref:System.Windows.Controls.StackPanel>控制項提供更多的功能比<xref:System.Windows.Controls.Canvas>控制項。 這種功能增加的代價是較高的效能成本。 不過，如果您不需要的功能，<xref:System.Windows.Controls.Grid>控制項提供，您應該使用成本更低的替代項目，例如<xref:System.Windows.Controls.Canvas>或自訂的面板。  
  
 如需詳細資訊，請參閱[面板概觀](../controls/panels-overview.md)。  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>更新，而不是取代 RenderTransform  
 您可以更新<xref:System.Windows.Media.Transform>而不是取代的值為<xref:System.Windows.UIElement.RenderTransform%2A>屬性。 特別是在包含動畫的案例。 藉由更新現有<xref:System.Windows.Media.Transform>，您可避免起始不必要的版面配置計算。  
  
### <a name="build-your-tree-top-down"></a>由上而下建置您的樹狀結構  
 在邏輯樹狀結構節點新增或移除節點時，會對節點之父代及其所有子系引發屬性失效。 因此，應該一律遵循由上而下的建構模式，以避免在已驗證的節點上發生不必要的失效成本。 下表顯示之間建立由上而下和由下而上，其中樹狀結構有 150 層深一樹狀結構的執行速度差異<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Controls.DockPanel>每個層級。  
  
|**動作**|**樹狀結構建置 （毫秒）**|**轉譯 — 包括樹狀結構建置 （以毫秒為單位）**|  
|----------------|---------------------------------|-------------------------------------------------|  
|由下而上|366|454|  
|由上而下|11|96|  
  
 下列程式碼範例示範如何由上而下建立樹狀結構。  
  
 [!code-csharp[Performance#PerformanceSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 如需有關邏輯樹狀結構的詳細資訊，請參閱 [WPF 中的樹狀結構](trees-in-wpf.md)。  
  
## <a name="see-also"></a>另請參閱

- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [應用程式效能規劃](planning-for-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [文字](optimizing-performance-text.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
- [配置](layout.md)
