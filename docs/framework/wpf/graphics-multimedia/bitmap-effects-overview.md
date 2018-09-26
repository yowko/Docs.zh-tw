---
title: 點陣圖效果概觀
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 97b878621d5aa1860cd955755d9bbc344b95b993
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171721"
---
# <a name="bitmap-effects-overview"></a>點陣圖效果概觀
點陣圖效果可讓設計人員和開發人員来套用至視覺效果呈現 Windows Presentation Foundation (WPF) 內容。 例如，點陣圖效果可讓您輕鬆地套用<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>效果或模糊效果影像或按鈕。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]或更新版本，<xref:System.Windows.Media.Effects.BitmapEffect>類別已過時。 如果您嘗試使用<xref:System.Windows.Media.Effects.BitmapEffect>類別，您會收到已淘汰的例外狀況。 非過時的替代方式，來<xref:System.Windows.Media.Effects.BitmapEffect>類別是<xref:System.Windows.Media.Effects.Effect>類別。 在大部分情況下，<xref:System.Windows.Media.Effects.Effect>類別速度獲得大幅提升。  
  
  
  
<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>WPF 點陣圖效果  
 點陣圖效果 (<xref:System.Windows.Media.Effects.BitmapEffect>物件) 是簡單的像素處理作業。 點陣圖效果會採用<xref:System.Windows.Media.Imaging.BitmapSource>作為輸入，並產生新<xref:System.Windows.Media.Imaging.BitmapSource>之後套用效果，例如模糊或陰影。 每個點陣圖效果會公開可控制篩選的屬性，這類<xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A>的<xref:System.Windows.Media.Effects.BlurBitmapEffect>。  
  
 特殊案例，在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，效果可以為屬性上設定即時<xref:System.Windows.Media.Visual>物件，例如<xref:System.Windows.Controls.Button>或<xref:System.Windows.Controls.TextBox>。 像素處理會在執行階段套用並進行轉譯。 在此情況下，在轉譯時<xref:System.Windows.Media.Visual>會自動轉換為其<xref:System.Windows.Media.Imaging.BitmapSource>對等和做為輸入<xref:System.Windows.Media.Effects.BitmapEffect>。 輸出會取代<xref:System.Windows.Media.Visual>物件的預設轉譯行為。 這就是為什麼<xref:System.Windows.Media.Effects.BitmapEffect>物件會強制在軟體中轉譯只也就是沒有視覺效果上的硬體加速時套用效果的視覺效果。  
  
-   <xref:System.Windows.Media.Effects.BlurBitmapEffect> 模擬物件出現失焦。  
  
-   <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> 建立物件周圍的色彩的光暈。  
  
-   <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> 建立物件後方的陰影。  
  
-   <xref:System.Windows.Media.Effects.BevelBitmapEffect> 建立根據指定的曲線影像表面的斜面。  
  
-   <xref:System.Windows.Media.Effects.EmbossBitmapEffect> 建立的凹凸貼圖<xref:System.Windows.Media.Visual>以便從人工光源創造深度和紋理的印象。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 點陣圖效果是在軟體模式中轉譯。 套用效果的任何物件也會在軟體中轉譯。 對大型視覺物件使用點陣圖效果或為點陣圖效果的屬性建立動畫時，效能會降低最多。 這並不是說您不應該以此種方式使用點陣圖效果，而是您應特別小心並徹底測試，以確保使用者能得到預期的體驗。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 點陣圖效果不支援部分信任執行。 應用程式必須有完全信任權限才能使用點陣圖效果。  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>如何套用效果  
 <xref:System.Windows.Media.Effects.BitmapEffect> 是一個屬性上<xref:System.Windows.Media.Visual>。 因此這類將效果套用至視覺效果<xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.Image>， <xref:System.Windows.Media.DrawingVisual>，或<xref:System.Windows.UIElement>，非常簡單，只要設定屬性。 <xref:System.Windows.UIElement.BitmapEffect%2A> 可以設定為單一<xref:System.Windows.Media.Effects.BitmapEffect>物件或多個效果可以鏈結在使用<xref:System.Windows.Media.Effects.BitmapEffectGroup>物件。  
  
 下列範例示範如何套用<xref:System.Windows.Media.Effects.BitmapEffect>在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 下列範例示範如何套用<xref:System.Windows.Media.Effects.BitmapEffect>在程式碼中。  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  當<xref:System.Windows.Media.Effects.BitmapEffect>套用至版面配置容器，例如<xref:System.Windows.Controls.DockPanel>或<xref:System.Windows.Controls.Canvas>，效果會套用至元素或視覺效果，包括其所有子元素的視覺化樹狀結構。  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>建立自訂效果  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 也提供 Unmanaged 介面以建立可在 Managed [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式中使用的自訂效果。 如需建立自訂點陣圖效果的其他參考資料，請參閱 [Unmanaged WPF 點陣圖效果 (英文)](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) 文件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Effects.BitmapEffectGroup>  
 <xref:System.Windows.Media.Effects.BitmapEffectInput>  
 <xref:System.Windows.Media.Effects.BitmapEffectCollection>  
 [Unmanaged 的 WPF 點陣圖效果](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)  
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [安全性](../../../../docs/framework/wpf/security-wpf.md)  
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [2D 圖形和影像處理](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
