---
title: 點陣圖效果概觀
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 4a5e73f21d4ce4988f56c139d13038dca902b5b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186997"
---
# <a name="bitmap-effects-overview"></a>點陣圖效果概觀
點陣圖效果使設計人員和開發人員能夠將視覺效果應用於渲染的 Windows 演示文稿基礎 （WPF） 內容。 例如，點陣圖效果允許您輕鬆地將<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>效果或模糊效果應用於圖像或按鈕。  
  
> [!IMPORTANT]
> 在 .NET 框架 4 或<xref:System.Windows.Media.Effects.BitmapEffect>更高版本中，類已過時。 如果嘗試使用 類，<xref:System.Windows.Media.Effects.BitmapEffect>將獲取過時的異常。 <xref:System.Windows.Media.Effects.BitmapEffect>類的非過時的替代方法是類<xref:System.Windows.Media.Effects.Effect>。 在大多數情況下，<xref:System.Windows.Media.Effects.Effect>類明顯更快。  

<a name="wpf_effects"></a>
## <a name="wpf-bitmap-effects"></a>WPF 點陣圖效果  
 點陣圖效果（<xref:System.Windows.Media.Effects.BitmapEffect>物件）是簡單的圖元處理操作。 點陣圖效果將 用作<xref:System.Windows.Media.Imaging.BitmapSource>輸入，並在應用效果後生成<xref:System.Windows.Media.Imaging.BitmapSource>新的效果，如模糊或投影。 每個點陣圖效果公開可以控制篩選屬性的屬性，例如<xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A>。 <xref:System.Windows.Media.Effects.BlurBitmapEffect>  
  
 作為特殊情況，在 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]可以將 效果設置為活動<xref:System.Windows.Media.Visual>物件的屬性，例如 或<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.TextBox>。 像素處理會在執行階段套用並進行轉譯。 在這種情況下，在渲染時，將自動<xref:System.Windows.Media.Visual>轉換為等效項<xref:System.Windows.Media.Imaging.BitmapSource>，並作為輸入饋入 。 <xref:System.Windows.Media.Effects.BitmapEffect> 輸出將替換<xref:System.Windows.Media.Visual>物件的預設呈現行為。 這就是為什麼<xref:System.Windows.Media.Effects.BitmapEffect>物件強制視覺物件僅在軟體中渲染，即應用效果時，視覺物件上沒有硬體加速。  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>類比顯示焦點外的物件。  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>在物件周長周圍創建顏色光暈。  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>在物件後面創建陰影。  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>創建一個斜面，根據指定的曲線增益圖像的表面。  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>創建 的<xref:System.Windows.Media.Visual>凹凸貼圖，以便從人工光源給人以深度和紋理的印象。  
  
> [!NOTE]
> WPF 點陣圖效果在軟體模式下呈現。 套用效果的任何物件也會在軟體中轉譯。 對大型視覺物件使用點陣圖效果或為點陣圖效果的屬性建立動畫時，效能會降低最多。 這並不是說您不應該以此種方式使用點陣圖效果，而是您應特別小心並徹底測試，以確保使用者能得到預期的體驗。  
  
> [!NOTE]
> WPF 位映射效果不支援部分信任執行。 應用程式必須有完全信任權限才能使用點陣圖效果。  
  
<a name="applyeffects"></a>
## <a name="how-to-apply-an-effect"></a>如何套用效果  
 <xref:System.Windows.Media.Effects.BitmapEffect>是 上的<xref:System.Windows.Media.Visual>屬性。 因此，將效果應用於 Visuals，如<xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Image>、、<xref:System.Windows.Media.DrawingVisual>或<xref:System.Windows.UIElement>，與設置屬性一樣簡單。 <xref:System.Windows.UIElement.BitmapEffect%2A>可以設置為單個<xref:System.Windows.Media.Effects.BitmapEffect>物件，也可以使用 該<xref:System.Windows.Media.Effects.BitmapEffectGroup>物件連結多個效果。  
  
 下面的示例演示如何<xref:System.Windows.Media.Effects.BitmapEffect>在 中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]應用 。  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 下面的示例演示如何在代碼中應用<xref:System.Windows.Media.Effects.BitmapEffect>。  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> <xref:System.Windows.Media.Effects.BitmapEffect>當 應用於佈局容器（如<xref:System.Windows.Controls.DockPanel>或<xref:System.Windows.Controls.Canvas>）時，效果將應用於元素或視覺物件（包括其所有子項目）的視覺化樹。  
  
<a name="customeffects"></a>
## <a name="creating-custom-effects"></a>建立自訂效果  
 WPF 還提供非託管介面，以創建可用於託管 WPF 應用程式的自訂效果。 如需建立自訂點陣圖效果的其他參考資料，請參閱 [Unmanaged WPF 點陣圖效果 (英文)](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh) 文件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Unmanaged WPF 點陣圖效果 (英文)](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [影像處理概觀](imaging-overview.md)
- [安全性](../security-wpf.md)
- [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
