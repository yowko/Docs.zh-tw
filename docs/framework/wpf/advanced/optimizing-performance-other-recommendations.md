---
title: 最佳化效能：其他建議
ms.date: 03/30/2017
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
ms.openlocfilehash: 56d3e3cad09b46090a11b884f3ac590e8d4ba23a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773096"
---
# <a name="optimizing-performance-other-recommendations"></a>最佳化效能：其他建議
<a name="introduction"></a> 本主題提供[最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)一節中主題所涵蓋內容以外的效能建議。  
  
 此主題包括下列章節：  
  
- [筆刷透明度與項目透明度的比較](#Opacity)  
  
- [物件瀏1覽](#Navigation_Objects)  
  
- [大型立體表面的點擊測試](#Hit_Testing)  
  
- [CompositionTarget.Rendering 事件](#CompositionTarget_Rendering_Event)  
  
- [避免使用 ScrollBarVisibility = Auto](#Avoid_Using_ScrollBarVisibility)  
  
- [設定字型快取服務以縮短啟動時間](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>筆刷透明度與項目透明度的比較  
 當您使用<xref:System.Windows.Media.Brush>來設定<xref:System.Windows.Shapes.Shape.Fill%2A>或<xref:System.Windows.Shapes.Shape.Stroke%2A>項目，最好設定<xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType>而非設定值的項目<xref:System.Windows.UIElement.Opacity%2A>屬性。 修改項目的<xref:System.Windows.UIElement.Opacity%2A>屬性可能會使[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]建立暫時介面。  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>物件瀏覽  
 <xref:System.Windows.Navigation.NavigationWindow>物件衍生自<xref:System.Windows.Window>並使用內容瀏覽支援加以擴充，主要是由彙總<xref:System.Windows.Navigation.NavigationService>和日誌。 您可以更新的工作區<xref:System.Windows.Navigation.NavigationWindow>由指定[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]或物件。 下列範例將顯示這兩種方法：  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 每個<xref:System.Windows.Navigation.NavigationWindow>物件有一份日誌，在該視窗中會記錄使用者的瀏覽歷程記錄。 日誌的用途之一，就是讓使用者能夠追溯其步驟。  
  
 當您使用 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 進行巡覽時，日誌只會儲存 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 參考。 這表示您每次重新瀏覽頁面時，它都會動態重新建構，如果頁面相當複雜，就有可能耗費許多時間。 在此情況下，日誌儲存成本雖然較低，但重新建構頁面所需的時間則可能很長。  
  
 當您使用物件進行瀏覽時，日誌會儲存該物件的整個視覺化樹狀結構。 這表示在您每次重新瀏覽頁面時，它都會立即呈現而不需重新建構。 在此情況下，日誌儲存成本較高，但重新建構頁面所需的時間較短。  
  
 當您使用<xref:System.Windows.Navigation.NavigationWindow>物件時，您必須謹記在心的日誌支援對您的應用程式效能的影響。 如需詳細資訊，請參閱[覽概觀](../app-development/navigation-overview.md)。  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>大型立體表面的點擊測試  
 就 CPU 的耗用量而言，大型立體表面的點擊測試是一項很耗損效能的作業。 當立體表面為動畫形式時，更是如此。 若您不需要對這些表面進行點擊測試，請停用點擊測試。 物件衍生自<xref:System.Windows.UIElement>可以停用點擊測試 splittunneling<xref:System.Windows.UIElement.IsHitTestVisible%2A>屬性設`false`。  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>CompositionTarget.Rendering 事件  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType>事件會致使[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]持續執行動畫。 若使用此事件，請盡可能中斷其連結。  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>避免使用 ScrollBarVisibility = Auto  
 可能的話，請避免使用<xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType>值`HorizontalScrollBarVisibility`和`VerticalScrollBarVisibility`屬性。 這些屬性會定義<xref:System.Windows.Controls.RichTextBox>， <xref:System.Windows.Controls.ScrollViewer>，並<xref:System.Windows.Controls.TextBox>物件，並為附加屬性的<xref:System.Windows.Controls.ListBox>物件。 相反地，設定<xref:System.Windows.Controls.ScrollBarVisibility>要<xref:System.Windows.Controls.ScrollBarVisibility.Disabled>， <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>，或<xref:System.Windows.Controls.ScrollBarVisibility.Visible>。  
  
 <xref:System.Windows.Controls.ScrollBarVisibility.Auto>值適合的情況下，名額有限，並在必要時，應該只顯示捲軸時。 比方說，它可能會使用這<xref:System.Windows.Controls.ScrollBarVisibility>具有值<xref:System.Windows.Controls.ListBox>30 個項目相對於<xref:System.Windows.Controls.TextBox>含有數百行文字。  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>設定字型快取服務以縮短啟動時間  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 字型快取服務可在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式之間共用字型資料。 您所執行的第一個 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式會啟動此服務 (若尚未執行)。 如果您使用[!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]，您可以從 「 手動 」 （預設值） 設定 「 Windows Presentation Foundation (WPF) Font Cache 3.0.0.0"服務，為 [自動 （延遲開始）]，以減少初始啟動時間[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式。  
  
## <a name="see-also"></a>另請參閱

- [應用程式效能規劃](planning-for-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [動畫祕訣和訣竅](../graphics-multimedia/animation-tips-and-tricks.md)
