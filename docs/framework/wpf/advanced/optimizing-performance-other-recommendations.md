---
title: "最佳化效能：其他建議 | Microsoft Docs"
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
  - "筆刷, 效能"
  - "點擊測試物件 [WPF]"
  - "不透明度"
  - "ScrollBarVisibility 列舉類型"
  - "終端機服務呈現"
ms.assetid: d028cc65-7e97-4a4f-9859-929734eaf40d
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 最佳化效能：其他建議
<a name="introduction"></a> 本主題提供[最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)一節中主題所涵蓋內容以外的效能建議。  
  
 此主題包括下列章節：  
  
-   [筆刷透明度與項目透明度的比較](#Opacity)  
  
-   [物件巡覽](#Navigation_Objects)  
  
-   [大型立體表面的點擊測試](#Hit_Testing)  
  
-   [CompositionTarget.Rendering 事件](#CompositionTarget_Rendering_Event)  
  
-   [避免使用 ScrollBarVisibility\=Auto](#Avoid_Using_ScrollBarVisibility)  
  
-   [設定字型快取服務以縮短啟動時間](#FontCache)  
  
<a name="Opacity"></a>   
## 筆刷透明度與項目透明度的比較  
 當您使用 <xref:System.Windows.Media.Brush> 設定項目的 <xref:System.Windows.Shapes.Shape.Fill%2A> 或 <xref:System.Windows.Shapes.Shape.Stroke%2A> 時，您應設定 <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=fullName> 值，而非設定項目的 <xref:System.Windows.UIElement.Opacity%2A> 屬性。  修改項目的 <xref:System.Windows.UIElement.Opacity%2A> 屬性可能會使 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 建立暫時介面。  
  
<a name="Navigation_Objects"></a>   
## 物件巡覽  
 <xref:System.Windows.Navigation.NavigationWindow> 物件是衍生自 <xref:System.Windows.Window>，並使用內容巡覽支援加以擴充，這主要是藉由彙總 \(Aggregate\) <xref:System.Windows.Navigation.NavigationService> 與日誌來進行。  您可以指定[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 或物件，來更新 <xref:System.Windows.Navigation.NavigationWindow> 的用戶端區域。  下列範例顯示這兩種方法：  
  
 [!code-csharp[Performance#PerformanceSnippet14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 每個 <xref:System.Windows.Navigation.NavigationWindow> 物件各有一份日誌，其中記載使用者在該視窗中的巡覽記錄。  日誌的用途之一，就是讓使用者能夠追溯其步驟。  
  
 當您使用[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 進行巡覽時，日誌只會儲存[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 參考。  這表示您每次重新造訪頁面時，它都會動態重新建構，如果頁面相當複雜，就有可能耗費許多時間。  在此情況下，日誌儲存成本雖然較低，但重新建構頁面所需的時間則可能很長。  
  
 當您使用物件進行巡覽時，日誌會儲存該物件的整個視覺化樹狀結構。  這表示在您每次重新造訪頁面時，它都會立即呈現而不需重新建構。  在此情況下，日誌儲存成本較高，但重新建構頁面所需的時間較短。  
  
 當您使用 <xref:System.Windows.Navigation.NavigationWindow> 物件時，必須留意日誌支援對您的應用程式效能所造成的影響。  如需詳細資訊，請參閱 [巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
<a name="Hit_Testing"></a>   
## 大型立體表面的點擊測試  
 就 CPU 的耗用量而言，大型立體表面的點擊測試 \(Hit Testing\) 是一項很耗損效能的作業。  當立體表面為動畫形式時，更是如此。  若您不需要對這些表面進行點擊測試，請停用點擊測試。  衍生自 <xref:System.Windows.UIElement> 的物件可透過將 <xref:System.Windows.UIElement.IsHitTestVisible%2A> 屬性設為 `false`，以停用點擊測試。  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## CompositionTarget.Rendering 事件  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=fullName> 事件會造成 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 連續執行動畫。  若使用此事件，請盡可能中斷其連結。  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## 避免使用 ScrollBarVisibility\=Auto  
 若情況允許，請避免對 `HorizontalScrollBarVisibility` 與 `VerticalScrollBarVisibility` 屬性使用 <xref:System.Windows.Controls.ScrollBarVisibility?displayProperty=fullName> 值。  這些屬性是針對 <xref:System.Windows.Controls.RichTextBox>、<xref:System.Windows.Controls.ScrollViewer> 與 <xref:System.Windows.Controls.TextBox> 物件而定義的，並且屬於 <xref:System.Windows.Controls.ListBox> 物件的附加屬性。  您應該將 <xref:System.Windows.Controls.ScrollBarVisibility> 設定為 <xref:System.Windows.Controls.ScrollBarVisibility>、<xref:System.Windows.Controls.ScrollBarVisibility> 或 <xref:System.Windows.Controls.ScrollBarVisibility>。  
  
 <xref:System.Windows.Controls.ScrollBarVisibility> 值適用於空間有限且捲軸僅在必要時才顯示的情況。  例如，相對於含有數百行文字的 <xref:System.Windows.Controls.TextBox>，使用此 <xref:System.Windows.Controls.ScrollBarVisibility> 值搭配 30 個項目的 <xref:System.Windows.Controls.ListBox> 就會比較適合。  
  
<a name="FontCache"></a>   
## 設定字型快取服務以縮短啟動時間  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 字型快取服務可在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式間共用字型資料。  您所執行的第一個 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式會啟動此服務 \(若尚未執行\)。  若您使用 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]，您可將 "[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Font Cache 3.0.0.0" 服務從「手動」\(預設值\) 設定為「自動 \(延遲開始\)」，以縮短 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式的初始啟動時間。  
  
## 請參閱  
 [應用程式效能規劃](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [動畫秘訣和訣竅](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)