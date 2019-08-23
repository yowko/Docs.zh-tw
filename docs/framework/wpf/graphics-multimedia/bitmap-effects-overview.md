---
title: 點陣圖效果概觀
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: f2fa42d5d63cad6a71efd259416dad3416bf2d72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935306"
---
# <a name="bitmap-effects-overview"></a>點陣圖效果概觀
點陣圖效果可讓設計人員和開發人員將視覺效果套用到轉譯的 Windows Presentation Foundation (WPF) 內容。 例如, 點陣圖效果可讓您輕鬆地將<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>效果或模糊效果套用到影像或按鈕。  
  
> [!IMPORTANT]
> 在 .NET Framework 4 或更新版本中, <xref:System.Windows.Media.Effects.BitmapEffect>類別已過時。 如果您嘗試使用<xref:System.Windows.Media.Effects.BitmapEffect>類別, 您會收到過時的例外狀況。 <xref:System.Windows.Media.Effects.BitmapEffect>類別的非過時替代方法<xref:System.Windows.Media.Effects.Effect>是類別。 在大多數情況下, <xref:System.Windows.Media.Effects.Effect>類別的速度會大幅提升。  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>WPF 點陣圖效果  
 點陣圖效果 (<xref:System.Windows.Media.Effects.BitmapEffect>物件) 是簡單的圖元處理作業。 點陣圖效果會接受<xref:System.Windows.Media.Imaging.BitmapSource>做為輸入, 並在套用效果之後 (例如模糊或陰影) 產生新<xref:System.Windows.Media.Imaging.BitmapSource>的。 每個點陣圖效果都會公開可控制篩選屬性的屬性, 例如<xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A>的<xref:System.Windows.Media.Effects.BlurBitmapEffect>。  
  
 在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], 您可以將效果設定為即時<xref:System.Windows.Media.Visual> <xref:System.Windows.Controls.Button>物件 (例如或<xref:System.Windows.Controls.TextBox>) 上的屬性, 這是特殊案例。 像素處理會在執行階段套用並進行轉譯。 在這種情況下, 轉譯時, <xref:System.Windows.Media.Visual>會自動轉換為其<xref:System.Windows.Media.Imaging.BitmapSource>對等的, 並以輸入的<xref:System.Windows.Media.Effects.BitmapEffect>形式送出。 輸出會取代<xref:System.Windows.Media.Visual>物件的預設呈現行為。 這就是<xref:System.Windows.Media.Effects.BitmapEffect>為什麼物件會強制視覺效果只在軟體中轉譯, 也就是在套用效果時, 不會對視覺效果進行硬體加速。  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>模擬出現在焦點之外的物件。  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>在物件的周邊周圍建立色彩光暈。  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>在物件後方建立陰影。  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>建立斜面, 根據指定的曲線來引發影像的表面。  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>建立的凹凸對應<xref:System.Windows.Media.Visual> , 以提供來自人工光源的深度和材質印象。  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 點陣圖效果是在軟體模式中轉譯。 套用效果的任何物件也會在軟體中轉譯。 對大型視覺物件使用點陣圖效果或為點陣圖效果的屬性建立動畫時，效能會降低最多。 這並不是說您不應該以此種方式使用點陣圖效果，而是您應特別小心並徹底測試，以確保使用者能得到預期的體驗。  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 點陣圖效果不支援部分信任執行。 應用程式必須有完全信任權限才能使用點陣圖效果。  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>如何套用效果  
 <xref:System.Windows.Media.Effects.BitmapEffect>是上<xref:System.Windows.Media.Visual>的屬性。 因此<xref:System.Windows.Controls.Button>, 將效果套用到視覺效果 (例如<xref:System.Windows.Controls.Image>、 <xref:System.Windows.Media.DrawingVisual>、或<xref:System.Windows.UIElement>) 就像設定屬性一樣簡單。 <xref:System.Windows.UIElement.BitmapEffect%2A>可以設定為單一<xref:System.Windows.Media.Effects.BitmapEffect>物件, 或<xref:System.Windows.Media.Effects.BitmapEffectGroup>使用物件來連結多個效果。  
  
 下列範例示範如何<xref:System.Windows.Media.Effects.BitmapEffect>在中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]套用。  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 下列範例示範如何<xref:System.Windows.Media.Effects.BitmapEffect>在程式碼中套用。  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> 當套用至版面配置容器 ( <xref:System.Windows.Controls.DockPanel>例如或<xref:System.Windows.Controls.Canvas>) 時, 效果會套用至元素或視覺物件的視覺化樹狀結構, 包括其所有的子專案。 <xref:System.Windows.Media.Effects.BitmapEffect>  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>建立自訂效果  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 也提供 Unmanaged 介面以建立可在 Managed [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式中使用的自訂效果。 如需建立自訂點陣圖效果的其他參考資料，請參閱 [Unmanaged WPF 點陣圖效果 (英文)](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) 文件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [非受控 WPF 點陣圖效果](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [影像處理概觀](imaging-overview.md)
- [Security](../security-wpf.md)
- [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
