---
title: "點陣圖效果概觀 | Microsoft Docs"
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
  - "點陣圖效果"
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# 點陣圖效果概觀
點陣圖效果可以讓設計人員和開發人員將視覺效果套用至呈現的 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 內容。  例如，點陣圖效果可以讓您輕易地將 <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> 效果或模糊效果套用至影像或按鈕。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] \(含\) 以後版本中，<xref:System.Windows.Media.Effects.BitmapEffect> 類別已過時。  如果您嘗試使用 <xref:System.Windows.Media.Effects.BitmapEffect> 類別，則會收到過期的例外狀況。  非過時的 <xref:System.Windows.Media.Effects.BitmapEffect> 類別替代項目為 <xref:System.Windows.Media.Effects.Effect> 類別。  在大部分情況下，<xref:System.Windows.Media.Effects.Effect> 類別的速度快上許多。  
  
   
  
<a name="wpf_effects"></a>   
## WPF 點陣圖效果  
 點陣圖效果 \(<xref:System.Windows.Media.Effects.BitmapEffect> 物件\) 是一種簡單的像素處理作業。  點陣圖效果會將 <xref:System.Windows.Media.Imaging.BitmapSource> 當做輸入，並且在套用效果 \(例如模糊或下拉式陰影\) 後產生新的 <xref:System.Windows.Media.Imaging.BitmapSource>。  每個點陣圖效果都會公開屬性，這些屬性可以控制篩選屬性，例如 <xref:System.Windows.Media.Effects.BlurBitmapEffect> 的 <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A>。  
  
 有一個特殊的情況，在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，效果可以以實況 <xref:System.Windows.Media.Visual> 物件上的屬性來設定，例如 <xref:System.Windows.Controls.Button> 或 <xref:System.Windows.Controls.TextBox>。  像素處理作業會在執行階段套用和呈現。  在此情況下，呈現時 <xref:System.Windows.Media.Visual> 會自動轉換成其 <xref:System.Windows.Media.Imaging.BitmapSource> 的對等項目，並且當成輸入傳遞至 <xref:System.Windows.Media.Effects.BitmapEffect>。  輸出結果會取代 <xref:System.Windows.Media.Visual> 物件的預設呈現行為。  這就是為什麼 <xref:System.Windows.Media.Effects.BitmapEffect> 物件會強迫視覺物件只在軟體中呈現，也就是說，  套用效果時視覺物件不會使用硬體加速功能。  
  
-   <xref:System.Windows.Media.Effects.BlurBitmapEffect> 會模擬失焦的物件。  
  
-   <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> 會在物件的周圍建立色彩光暈。  
  
-   <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> 會在物件背後建立陰影。  
  
-   <xref:System.Windows.Media.Effects.BevelBitmapEffect> 會建立斜面 \(Bevel\)，這個斜面會根據指定的曲線抬高影像表面。  
  
-   <xref:System.Windows.Media.Effects.EmbossBitmapEffect> 會建立 <xref:System.Windows.Media.Visual> 的凹凸貼圖，使用人工光源給予深度和紋理的印象。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 點陣圖效果是在軟體模式中呈現。  所有套用效果的物件也會在軟體中呈現。  在大型視覺物件上使用點陣圖效果或者以點陣圖效果的屬性建立動畫時，降低的效能最多。  這並不代表您完全不能這樣使用點陣圖效果，但是應該考量周詳並且做過徹底測試，以確保使用者能得到預期的經驗。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 點陣圖效果不支援執行部分信任。  應用程式必須具有完全信任權限，才能使用點陣圖效果。  
  
<a name="applyeffects"></a>   
## 如何套用效果  
 <xref:System.Windows.Media.Effects.BitmapEffect> 是 <xref:System.Windows.Media.Visual> 上的屬性。  因此，將效果套用至視覺物件，例如 <xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.Image>、<xref:System.Windows.Media.DrawingVisual> 或 <xref:System.Windows.UIElement>，就跟設定屬性一樣簡單。  <xref:System.Windows.UIElement.BitmapEffect%2A> 可以設定為單一 <xref:System.Windows.Media.Effects.BitmapEffect> 物件，或者多種效果可以使用 <xref:System.Windows.Media.Effects.BitmapEffectGroup> 物件鏈結。  
  
 下列範例示範如何在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中套用 <xref:System.Windows.Media.Effects.BitmapEffect>。  
  
 [!code-xml[EffectsGallery_snip#BlurSimpleExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 下列範例示範如何在程式碼中套用 <xref:System.Windows.Media.Effects.BitmapEffect>。  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  當 <xref:System.Windows.Media.Effects.BitmapEffect> 套用至配置容器時，例如 <xref:System.Windows.Controls.DockPanel> 或 <xref:System.Windows.Controls.Canvas>，效果會套用至項目或視覺物件的視覺化樹狀目錄，包括其所有子項目。  
  
<a name="customeffects"></a>   
## 建立自訂效果  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 也提供 Unmanaged 的介面，以建立可以在 Unmanaged [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式中使用的自訂效果。  如需建立自訂點陣圖效果的其他參考資料，請參閱 [Unmanaged WPF 點陣圖效果](_wibe_lh)文件。  
  
## 請參閱  
 <xref:System.Windows.Media.Effects.BitmapEffectGroup>   
 <xref:System.Windows.Media.Effects.BitmapEffectInput>   
 <xref:System.Windows.Media.Effects.BitmapEffectCollection>   
 [Unmanaged WPF Bitmap Effect](_wibe_lh)   
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)   
 [安全性](../../../../docs/framework/wpf/security-wpf.md)   
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)