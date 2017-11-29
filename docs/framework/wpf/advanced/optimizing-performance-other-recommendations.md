---
title: "最佳化效能：其他建議"
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
- Terminal Services rendering [WPF]
- opacity [WPF]
- hit-test objects [WPF]
- ScrollBarVisibility enumeration [WPF]
- brushes [WPF], performance
ms.assetid: d028cc65-7e97-4a4f-9859-929734eaf40d
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eda112db6dd977b6ef25a1b3a9ae40349d3a045f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-other-recommendations"></a>最佳化效能：其他建議
<a name="introduction"></a> 本主題提供[最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)一節中主題所涵蓋內容以外的效能建議。  
  
 此主題包括下列章節：  
  
-   [筆刷透明度與項目透明度的比較](#Opacity)  
  
-   [物件瀏1覽](#Navigation_Objects)  
  
-   [大型立體表面的點擊測試](#Hit_Testing)  
  
-   [CompositionTarget.Rendering 事件](#CompositionTarget_Rendering_Event)  
  
-   [避免使用 ScrollBarVisibility = Auto](#Avoid_Using_ScrollBarVisibility)  
  
-   [設定字型快取服務以縮短啟動時間](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>筆刷透明度與項目透明度的比較  
 當您使用<xref:System.Windows.Media.Brush>設定<xref:System.Windows.Shapes.Shape.Fill%2A>或<xref:System.Windows.Shapes.Shape.Stroke%2A>的項目，最好是在設定<xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType>值而非設定的項目<xref:System.Windows.UIElement.Opacity%2A>屬性。 修改的項目<xref:System.Windows.UIElement.Opacity%2A>屬性可能會導致[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]建立暫存的介面。  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>物件瀏覽  
 <xref:System.Windows.Navigation.NavigationWindow>物件衍生自<xref:System.Windows.Window>，並擴充內容巡覽的支援，主要是彙總<xref:System.Windows.Navigation.NavigationService>和日誌。 您可以更新的用戶端區域<xref:System.Windows.Navigation.NavigationWindow>藉由指定[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]或物件。 下列範例將顯示這兩種方法：  
  
 [!code-csharp[Performance#PerformanceSnippet14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 每個<xref:System.Windows.Navigation.NavigationWindow>物件具有該視窗中會記錄使用者的瀏覽歷程記錄的日誌。 日誌的用途之一，就是讓使用者能夠追溯其步驟。  
  
 當您使用 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 進行巡覽時，日誌只會儲存 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 參考。 這表示您每次重新瀏覽頁面時，它都會動態重新建構，如果頁面相當複雜，就有可能耗費許多時間。 在此情況下，日誌儲存成本雖然較低，但重新建構頁面所需的時間則可能很長。  
  
 當您使用物件進行瀏覽時，日誌會儲存該物件的整個視覺化樹狀結構。 這表示在您每次重新瀏覽頁面時，它都會立即呈現而不需重新建構。 在此情況下，日誌儲存成本較高，但重新建構頁面所需的時間較短。  
  
 當您使用<xref:System.Windows.Navigation.NavigationWindow>物件，您必須謹記在心的日誌支援如何影響您的應用程式效能。 如需詳細資訊，請參閱[覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>大型立體表面的點擊測試  
 就 CPU 的耗用量而言，大型立體表面的點擊測試是一項很耗損效能的作業。 當立體表面為動畫形式時，更是如此。 若您不需要對這些表面進行點擊測試，請停用點擊測試。 物件，衍生自<xref:System.Windows.UIElement>可以停用的點擊測試設定<xref:System.Windows.UIElement.IsHitTestVisible%2A>屬性`false`。  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>CompositionTarget.Rendering 事件  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType>事件導致[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]持續動畫。 若使用此事件，請盡可能中斷其連結。  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>避免使用 ScrollBarVisibility = Auto  
 可能的話，請避免使用<xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType>值`HorizontalScrollBarVisibility`和`VerticalScrollBarVisibility`屬性。 這些屬性定義為<xref:System.Windows.Controls.RichTextBox>， <xref:System.Windows.Controls.ScrollViewer>，和<xref:System.Windows.Controls.TextBox>物件，並為附加屬性的<xref:System.Windows.Controls.ListBox>物件。 相反地，設定<xref:System.Windows.Controls.ScrollBarVisibility>至<xref:System.Windows.Controls.ScrollBarVisibility.Disabled>， <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>，或<xref:System.Windows.Controls.ScrollBarVisibility.Visible>。  
  
 <xref:System.Windows.Controls.ScrollBarVisibility.Auto>值適合的情況下，當空間被限制，並在必要時，應該只會顯示捲軸。 例如，可能很有用使用這個<xref:System.Windows.Controls.ScrollBarVisibility>值與<xref:System.Windows.Controls.ListBox>30 個項目與<xref:System.Windows.Controls.TextBox>含有上百個行文字。  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>設定字型快取服務以縮短啟動時間  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 字型快取服務可在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式之間共用字型資料。 您所執行的第一個 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式會啟動此服務 (若尚未執行)。 若您使用 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]，即可將 "[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Font Cache 3.0.0.0" 服務從「手動」(預設值) 設定為「自動 (延遲開始)」，以縮短 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式的初始啟動時間。  
  
## <a name="see-also"></a>另請參閱  
 [應用程式效能規劃](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [版面配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D 圖形和影像處理](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [動畫祕訣和訣竅](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
