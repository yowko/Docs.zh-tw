---
title: "最佳化效能：配置與設計 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "設計考量"
  - "配置傳遞"
  - "配置, 最佳化效能"
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 最佳化效能：配置與設計
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的設計會在計算配置以及驗證物件參考時產生不必要的負荷，因而影響它的效能。  而物件的建構 \(特別是在執行階段\) 則會影響應用程式的效能特性。  
  
 本主題提供這些區域的效能建議。  
  
## Layout  
 詞彙「配置傳遞」說明的處理序是用來測量和排列 <xref:System.Windows.Controls.Panel> 衍生物件的子項集合成員，然後將它們繪製在螢幕上。  配置傳遞是數學密集的處理序，即集合中的子項數目愈多，需要的計算數就愈多。  例如，每次集合中的子 <xref:System.Windows.UIElement> 物件變更它的位置時，配置系統就可能觸發新的傳遞。  因為物件特性與配置行為之間具有緊密的關聯性 \(Relationship\)，所以重要的是了解可以叫用 \(Invoke\) 配置系統的事件類型。  盡可能減少配置傳遞的任何不必要叫用，可以更妥善的執行應用程式。  
  
 配置系統會針對集合中的每個子成員完成兩個傳遞：測量傳遞和排列傳遞。  每個子物件都會提供它自己對 <xref:System.Windows.UIElement.Measure%2A> 和 <xref:System.Windows.UIElement.Arrange%2A> 方法的覆寫實作，以提供它自己特有的配置行為。  簡單來說，配置是一個遞迴系統，可以調整項目大小、定位項目以及將項目繪製在畫面上。  
  
-   子 <xref:System.Windows.UIElement> 物件開始配置處理序的第一步，是先測量它的核心屬性。  
  
-   接著評估與大小相關的物件 <xref:System.Windows.FrameworkElement> 屬性，例如 <xref:System.Windows.FrameworkElement.Width%2A>、<xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Margin%2A>。  
  
-   套用 <xref:System.Windows.Controls.Panel> 的特定邏輯，例如 <xref:System.Windows.Controls.DockPanel> 的 <xref:System.Windows.Controls.DockPanel.Dock%2A> 屬性，或 <xref:System.Windows.Controls.StackPanel> 的 <xref:System.Windows.Controls.StackPanel.Orientation%2A> 屬性。  
  
-   測量所有子物件之後，排列或定位內容。  
  
-   將子物件集合繪製至螢幕。  
  
 如果發生下列任一動作，則會再次叫用配置傳遞處理序：  
  
-   加入子物件至集合。  
  
-   套用 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 至子物件。  
  
-   針對子物件呼叫 <xref:System.Windows.UIElement.UpdateLayout%2A> 方法。  
  
-   當[相依性屬性](GTMT)的值產生變更時，而此相依性屬性標示著會影響測量或排列傳遞的中繼資料 \(Metadata\)。  
  
### 盡可能使用最有效率的面板  
 配置處理序的複雜性是直接根據所使用之 <xref:System.Windows.Controls.Panel> 衍生項目的配置行為。  例如，<xref:System.Windows.Controls.Grid> 或 <xref:System.Windows.Controls.StackPanel> 控制項提供的功能多於 <xref:System.Windows.Controls.Canvas> 控制項。  而功能增加的代價就是效能成本的增加。  然而，如果不需要 <xref:System.Windows.Controls.Grid> 控制項所提供的功能，便應該使用成本較低的替代項目，例如 <xref:System.Windows.Controls.Canvas> 或自訂面板。  
  
 如需詳細資訊，請參閱 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)。  
  
### 更新而非取代 RenderTransform  
 您可以更新 <xref:System.Windows.Media.Transform>，而不是將它取代為 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性的值。  這特別適用於包含動畫的案例。  更新現有的 <xref:System.Windows.Media.Transform>，可以避免起始不必要的配置計算。  
  
### 由上往下建置樹狀結構  
 在[邏輯樹狀結構](GTMT)中加入或移除節點時，會在節點的父項和其所有子項上引發屬性失效。  因此，應該一律遵循由上而下的建構模式，避免已驗證節點的不必要失效成本。  下表顯示建置由上到下與由下到上之樹狀結構的執行速度差異，其中樹狀結構的深度有 150 層，而且每層都有單一 <xref:System.Windows.Controls.TextBlock> 和 <xref:System.Windows.Controls.DockPanel>。  
  
|**動作**|**樹狀結構建置 \(毫秒\)**|**轉譯 \- 包括樹狀結構建置 \(毫秒\)**|  
|------------|-----------------------|-------------------------------|  
|由下到上|366|454|  
|由上到下|11|96|  
  
 下列程式碼範例示範如何建立由上到下的樹狀結構。  
  
 [!code-csharp[Performance#PerformanceSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 如需邏輯樹狀結構的詳細資訊，請參閱 [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)。  
  
## 請參閱  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [應用程式效能規劃](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)   
 [配置](../../../../docs/framework/wpf/advanced/layout.md)