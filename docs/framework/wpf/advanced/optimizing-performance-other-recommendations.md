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
ms.openlocfilehash: b6d99d90a3da232e1873ebe8433e01ceb2977de6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636428"
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
 當您使用 <xref:System.Windows.Media.Brush> 設定專案的 <xref:System.Windows.Shapes.Shape.Fill%2A> 或 <xref:System.Windows.Shapes.Shape.Stroke%2A> 時，最好設定 <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> 值，而不是設定元素的 <xref:System.Windows.UIElement.Opacity%2A> 屬性。 修改元素的 <xref:System.Windows.UIElement.Opacity%2A> 屬性可能會導致 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 建立暫存介面。  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>物件瀏覽  
 <xref:System.Windows.Navigation.NavigationWindow> 物件衍生自 <xref:System.Windows.Window>，並以內容導覽支援加以延伸，主要是藉由匯總 <xref:System.Windows.Navigation.NavigationService> 和日誌。 您可以藉由指定統一資源識別元（URI）或物件，來更新 <xref:System.Windows.Navigation.NavigationWindow> 的工作區。 下列範例將顯示這兩種方法：  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 每個 <xref:System.Windows.Navigation.NavigationWindow> 物件都有日誌，會在該視窗中記錄使用者的流覽歷程記錄。 日誌的用途之一，就是讓使用者能夠追溯其步驟。  
  
 當您使用統一資源識別元（URI）進行流覽時，日誌只會儲存統一資源識別元（URI）參考。 這表示您每次重新瀏覽頁面時，它都會動態重新建構，如果頁面相當複雜，就有可能耗費許多時間。 在此情況下，日誌儲存成本雖然較低，但重新建構頁面所需的時間則可能很長。  
  
 當您使用物件進行瀏覽時，日誌會儲存該物件的整個視覺化樹狀結構。 這表示在您每次重新瀏覽頁面時，它都會立即呈現而不需重新建構。 在此情況下，日誌儲存成本較高，但重新建構頁面所需的時間較短。  
  
 當您使用 <xref:System.Windows.Navigation.NavigationWindow> 物件時，您必須記住日誌支援會如何影響應用程式的效能。 如需詳細資訊，請參閱[覽概觀](../app-development/navigation-overview.md)。  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>大型立體表面的點擊測試  
 就 CPU 的耗用量而言，大型立體表面的點擊測試是一項很耗損效能的作業。 當立體表面為動畫形式時，更是如此。 若您不需要對這些表面進行點擊測試，請停用點擊測試。 衍生自 <xref:System.Windows.UIElement> 的物件可以藉由將 <xref:System.Windows.UIElement.IsHitTestVisible%2A> 屬性設定為 `false`來停用點擊測試。  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>CompositionTarget.Rendering 事件  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> 事件會導致 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 持續以動畫顯示。 若使用此事件，請盡可能中斷其連結。  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>避免使用 ScrollBarVisibility = Auto  
 請盡可能避免使用 `HorizontalScrollBarVisibility` 和 `VerticalScrollBarVisibility` 屬性的 <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> 值。 這些屬性是針對 <xref:System.Windows.Controls.RichTextBox>、<xref:System.Windows.Controls.ScrollViewer>和 <xref:System.Windows.Controls.TextBox> 物件，以及 <xref:System.Windows.Controls.ListBox> 物件的附加屬性所定義。 相反地，請將 <xref:System.Windows.Controls.ScrollBarVisibility> 設定為 <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>、<xref:System.Windows.Controls.ScrollBarVisibility.Hidden>或 <xref:System.Windows.Controls.ScrollBarVisibility.Visible>。  
  
 <xref:System.Windows.Controls.ScrollBarVisibility.Auto> 值適用于空間受限的情況，捲軸應該只在必要時才顯示。 例如，使用此 <xref:System.Windows.Controls.ScrollBarVisibility> 值搭配 <xref:System.Windows.Controls.ListBox> 30 個專案，而非具有數百行文字的 <xref:System.Windows.Controls.TextBox>，可能會很有用。  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>設定字型快取服務以縮短啟動時間  
 WPF 字型快取服務會在 WPF 應用程式之間共用字型資料。 您所執行的第一個 WPF 應用程式會啟動此服務（如果服務尚未執行）。 如果您使用的是 Windows Vista，可以將 "Windows Presentation Foundation （WPF） Font-size Cache 3.0.0.0" 服務從 "Manual" （預設值）設定為 [自動（延遲開始）]，以減少 WPF 應用程式的初始啟動時間。  
  
## <a name="see-also"></a>請參閱

- [應用程式效能規劃](planning-for-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [文字](optimizing-performance-text.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [動畫祕訣和訣竅](../graphics-multimedia/animation-tips-and-tricks.md)
