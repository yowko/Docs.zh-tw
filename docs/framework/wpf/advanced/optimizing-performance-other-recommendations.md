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
ms.openlocfilehash: 727331adb41251460209f157d1804ff455bcf473
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186307"
---
# <a name="optimizing-performance-other-recommendations"></a>最佳化效能：其他建議
<a name="introduction"></a> 本主題提供[最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)一節中主題所涵蓋內容以外的效能建議。  
  
 本主題包含下列幾節：  
  
- [筆刷透明度與項目透明度的比較](#Opacity)  
  
- [物件瀏覽](#Navigation_Objects)  
  
- [大型立體表面的點擊測試](#Hit_Testing)  
  
- [CompositionTarget.Rendering 事件](#CompositionTarget_Rendering_Event)  
  
- [避免使用 ScrollBarVisibility = Auto](#Avoid_Using_ScrollBarVisibility)  
  
- [設定字型快取服務以縮短啟動時間](#FontCache)  
  
<a name="Opacity"></a>
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>筆刷透明度與項目透明度的比較  
 <xref:System.Windows.Media.Brush>使用 設置 元素<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Shape.Stroke%2A>或 時，最好設置<xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType>值，而不是設置元素的屬性。 <xref:System.Windows.UIElement.Opacity%2A> 修改元素的屬性<xref:System.Windows.UIElement.Opacity%2A>可能會導致[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]創建臨時曲面。  
  
<a name="Navigation_Objects"></a>
## <a name="navigation-to-object"></a>物件瀏覽  
 物件<xref:System.Windows.Navigation.NavigationWindow>派生自<xref:System.Windows.Window>內容導航支援並擴展它，主要通過聚合<xref:System.Windows.Navigation.NavigationService>和日誌。 可以通過指定統一的資源識別碼<xref:System.Windows.Navigation.NavigationWindow>（URI） 或物件來更新 的工作區。 下列範例將顯示這兩種方法：  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 每個<xref:System.Windows.Navigation.NavigationWindow>物件都有一個日誌，記錄使用者在該視窗中的導航歷史記錄。 日誌的用途之一，就是讓使用者能夠追溯其步驟。  
  
 使用統一的資源識別碼 （URI） 導航時，日誌僅存儲統一的資源識別碼 （URI） 引用。 這表示您每次重新瀏覽頁面時，它都會動態重新建構，如果頁面相當複雜，就有可能耗費許多時間。 在此情況下，日誌儲存成本雖然較低，但重新建構頁面所需的時間則可能很長。  
  
 當您使用物件進行瀏覽時，日誌會儲存該物件的整個視覺化樹狀結構。 這表示在您每次重新瀏覽頁面時，它都會立即呈現而不需重新建構。 在此情況下，日誌儲存成本較高，但重新建構頁面所需的時間較短。  
  
 使用 物件時<xref:System.Windows.Navigation.NavigationWindow>，需要牢記日記支援如何影響應用程式的性能。 如需詳細資訊，請參閱[覽概觀](../app-development/navigation-overview.md)。  
  
<a name="Hit_Testing"></a>
## <a name="hit-testing-on-large-3d-surfaces"></a>大型立體表面的點擊測試  
 就 CPU 的耗用量而言，大型立體表面的點擊測試是一項很耗損效能的作業。 當立體表面為動畫形式時，更是如此。 若您不需要對這些表面進行點擊測試，請停用點擊測試。 派生自<xref:System.Windows.UIElement>的物件可以通過將<xref:System.Windows.UIElement.IsHitTestVisible%2A>屬性設置為`false`來禁用點擊測試。  
  
<a name="CompositionTarget_Rendering_Event"></a>
## <a name="compositiontargetrendering-event"></a>CompositionTarget.Rendering 事件  
 該<xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType>事件導致[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]連續設置動畫。 若使用此事件，請盡可能中斷其連結。  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>
## <a name="avoid-using-scrollbarvisibilityauto"></a>避免使用 ScrollBarVisibility = Auto  
 盡可能避免使用 和<xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType>`HorizontalScrollBarVisibility``VerticalScrollBarVisibility`屬性的值。 <xref:System.Windows.Controls.RichTextBox>這些屬性為<xref:System.Windows.Controls.ScrollViewer>和<xref:System.Windows.Controls.TextBox>物件以及作為<xref:System.Windows.Controls.ListBox>物件的附加屬性定義。 <xref:System.Windows.Controls.ScrollBarVisibility>而是設置為<xref:System.Windows.Controls.ScrollBarVisibility.Disabled>，<xref:System.Windows.Controls.ScrollBarVisibility.Hidden>或<xref:System.Windows.Controls.ScrollBarVisibility.Visible>。  
  
 該<xref:System.Windows.Controls.ScrollBarVisibility.Auto>值適用于空間有限且僅在必要時顯示捲軸的情況。 例如，將此值<xref:System.Windows.Controls.ScrollBarVisibility>與 30 個<xref:System.Windows.Controls.ListBox>項（而不是包含數百行文本的項<xref:System.Windows.Controls.TextBox>）使用可能很有用。  
  
<a name="FontCache"></a>
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>設定字型快取服務以縮短啟動時間  
 WPF 字型快取服務在 WPF 應用程式之間共用字體資料。 如果服務尚未運行，則運行的第一個 WPF 應用程式將啟動此服務。 如果使用 Windows Vista，則可以將"Windows 演示基礎 （WPF） 字體緩存 3.0.0"服務從"手動"（預設值）設置為"自動（延遲啟動）"，以減少 WPF 應用程式的初始啟動時間。  
  
## <a name="see-also"></a>另請參閱

- [應用程式效能規劃](planning-for-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [文本](optimizing-performance-text.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [動畫祕訣和訣竅](../graphics-multimedia/animation-tips-and-tricks.md)
