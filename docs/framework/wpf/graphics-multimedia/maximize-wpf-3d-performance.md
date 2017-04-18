---
title: "最大化 WPF 3D 效能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "立體圖形 [WPF]"
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 最大化 WPF 3D 效能
當您使用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 建置 3D 控制項並將 3D 場景加入應用程式中時，請務必考量效能最佳化的問題。本主題列出影響應用程式效能的 3D 類別和屬性，並提供使用這些類別和屬性時的效能最佳化建議。  
  
 本主題假設您對 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D 功能有深入的了解。  本文件中的建議適用於「轉譯層 2」\-\- 其粗略定義就是支援像素著色器 2.0 版和頂點著色器 2.0 版的硬體。  如需詳細資訊，請參閱 [圖形轉譯層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)。  
  
## 效能影響：大  
  
|||  
|-|-|  
|屬性|建議|  
|<xref:System.Windows.Media.Brush>|筆刷速度 \(從最快到最慢\)：<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> \(快取的\)<br /><br /> <xref:System.Windows.Media.VisualBrush> \(快取的\)<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> \(取消快取\)<br /><br /> <xref:System.Windows.Media.VisualBrush> \(非快取的\)|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|只要您不需要 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 將 <xref:System.Windows.Controls.Viewport3D> 的內容明確裁剪為 Viewport3D 的矩形，就將 `Viewport3D.ClipToBounds` 設為 false。[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 反鋸齒裁剪可能很慢，而 <xref:System.Windows.Controls.Viewport3D> 上預設會啟用 `ClipToBounds` \(慢\)。|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|只要您在執行滑鼠點擊測試時不需要 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 考量 <xref:System.Windows.Controls.Viewport3D> 的內容，就將 `Viewport3D.IsHitTestVisible` 設為 false。3D 內容的點擊測試是在軟體中執行，萬一網狀結構很大就會變得很慢。<xref:System.Windows.Controls.Viewport3D> 上預設會啟用 <xref:System.Windows.UIElement.IsHitTestVisible%2A> \(慢\)。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|只有在不同模型需要有不同「材質」或「轉換」時，才建立不同模型。  否則，試著將具有相同「材質」和「轉換」的多個 <xref:System.Windows.Media.Media3D.GeometryModel3D> 執行個體合併到幾個較大的 <xref:System.Windows.Media.Media3D.GeometryModel3D> 和 <xref:System.Windows.Media.Media3D.MeshGeometry3D> 執行個體中。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，網狀結構動畫 \(在每一畫面格上變更網狀結構的個別頂點\) 不一定很有效率。若要減少修改各點頂點時變更通知作業對效能所造成的影響，在修改各頂點之前請先中斷網狀結構與視覺化樹狀結構的連結。在網狀結構修改完成之後，再將它重新附加至視覺化樹狀結構。此外，也請盡量縮減以這種方式建立動畫的網狀結構大小。|  
|3D Antialiasing|若要加快呈現速度，請將 <xref:System.Windows.Controls.Viewport3D> 上的附加屬性 <xref:System.Windows.Media.RenderOptions.EdgeMode%2A> 設為 `Aliased` 以停用多重取樣。  根據預設，3D 消除鋸齒功能在 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 上會停用，而在 [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] 上會啟用 \(每一像素 4 樣本\)。|  
|文字|3D 場景中的實體文字 \(因為在 <xref:System.Windows.Media.DrawingBrush> 或 <xref:System.Windows.Media.VisualBrush> 中，所以稱為實體\) 可能會很慢。  除非文字會變更，否則請盡量改用文字影像 \(利用 <xref:System.Windows.Media.Imaging.RenderTargetBitmap>\)。|  
|<xref:System.Windows.Media.TileBrush>|如果因為筆刷的內容不是靜態內容，而必須在 3D 場景中使用 <xref:System.Windows.Media.VisualBrush> 或 <xref:System.Windows.Media.DrawingBrush>，請試著快取筆刷 \(將附加屬性 <xref:System.Windows.Media.RenderOptions.CachingHint%2A> 設定為 `Cache`\)。  設定最小和最大縮放失效臨界值 \(透過附加屬性 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> 和 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>\)，使快取的筆刷不會太常重新產生，同時仍能維持您想要的品質等級。  根據預設，並不會快取 <xref:System.Windows.Media.DrawingBrush> 和 <xref:System.Windows.Media.VisualBrush>，意思是說每次需要重新呈現用筆刷繪製的效果時，都必須先在中繼表面上重新呈現筆刷的完整內容。|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect> 會在不使用硬體加速的情形下強制重新呈現所有受影響的內容。  為達到最佳效能，請不要使用 <xref:System.Windows.Media.Effects.BitmapEffect>。|  
  
## 效能影響：中  
  
|||  
|-|-|  
|屬性|建議|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|當網狀結構是定義為鄰接的三角形，這些三角形具有共用的頂點且這些頂點有相同的位置、法線和紋理座標，您只要定義各共用頂點一次，然後再用 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> 以索引鍵定義您的三角形即可。|  
|<xref:System.Windows.Media.ImageBrush>|當您對大小有明確的控制時 \(當您使用 <xref:System.Windows.Media.Imaging.RenderTargetBitmap> 和 \(或\) <xref:System.Windows.Media.ImageBrush> 時\)，請將紋理大小減至最小。  請注意，較低解析度的紋理會降低視覺品質，所以請盡量在品質和效能之間找到適當的平衡點。|  
|Opacity|在呈現半透明 3D 內容時 \(如倒影\)，可以使用筆刷或材質上的不透明屬性 \(利用 <xref:System.Windows.Media.Brush.Opacity%2A> 或 <xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>\)，而不是藉由將 `Viewport3D.Opacity` 設為低於 1 來建立另一個半透明 <xref:System.Windows.Controls.Viewport3D>。|  
|<xref:System.Windows.Controls.Viewport3D>|將您在場景中使用的 <xref:System.Windows.Controls.Viewport3D> 物件數量減至最少。  將許多 3D 模型放在相同的 Viewport3D 中，而不是為每個模型建立個別的 Viewport3D 執行個體。|  
|<xref:System.Windows.Freezable>|一般而言，重複使用 <xref:System.Windows.Media.Media3D.MeshGeometry3D>、<xref:System.Windows.Media.Media3D.GeometryModel3D>、「筆刷」和「材質」有許多好處。  因為它們都是衍生自 `Freezable`，所以它們可以有許多父系。|  
|<xref:System.Windows.Freezable>|當 Freezable 的屬性在您的應用程式中會維持不變時，請呼叫 Freezable 的 <xref:System.Windows.Freezable.Freeze%2A> 方法。  凍結可減少工作集並增加速度。|  
|<xref:System.Windows.Media.Brush>|當筆刷內容不會變更時，請使用 <xref:System.Windows.Media.ImageBrush> 而不是 <xref:System.Windows.Media.VisualBrush> 或 <xref:System.Windows.Media.DrawingBrush>。  您可以先利用 <xref:System.Windows.Media.Imaging.RenderTargetBitmap> 將 2D 內容轉換為 <xref:System.Windows.Controls.Image>，然後再於 <xref:System.Windows.Media.ImageBrush> 中使用。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|除非您真的需要看到 <xref:System.Windows.Media.Media3D.GeometryModel3D> 的背面，否則請不要使用 <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>。|  
|<xref:System.Windows.Media.Media3D.Light>|光源速度 \(從最快到最慢\)：<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|請盡量讓網狀結構大小維持在下列上限之下：<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>：20,001 個 <xref:System.Windows.Media.Media3D.Point3D> 執行個體<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>：60,003 個 <xref:System.Int32> 執行個體|  
|<xref:System.Windows.Media.Media3D.Material>|材質速度 \(從最快到最慢\)：<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D 不會使用一致的方式來排除不可見的筆刷 \(黑色環境筆刷、清除筆刷等\)。請考慮不要在您的場景中使用這些筆刷。|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|<xref:System.Windows.Media.Media3D.MaterialGroup> 中的每個 <xref:System.Windows.Media.Media3D.Material> 都會引起另一個呈現動作，因此加入許多材質，甚至是簡單的材質，都會大幅增加 GPU 的填滿要求。  請減少您 <xref:System.Windows.Media.Media3D.MaterialGroup> 中的材質數量。|  
  
## 效能影響：小  
  
|||  
|-|-|  
|屬性|建議|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|當您不需要動畫或資料繫結時，請不要使用含有多個轉換的轉換群組，而應當改用單一 <xref:System.Windows.Media.Media3D.MatrixTransform3D>，將它設定為所有轉換的乘積，這些轉換在其他情況下是個別存在轉換群組中的。|  
|<xref:System.Windows.Media.Media3D.Light>|減少您場景中的光源數。  場景中的光源過多將會強制 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 切換回軟體轉譯。光源數上限約為 110 個 <xref:System.Windows.Media.Media3D.DirectionalLight> 物件、70 個 <xref:System.Windows.Media.Media3D.PointLight> 物件或 40 個 <xref:System.Windows.Media.Media3D.SpotLight> 物件。|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|將移動物件和靜態物件分開，做法是將它們放在不同的 <xref:System.Windows.Media.Media3D.ModelVisual3D> 執行個體中，以與靜態物件分開。  ModelVisual3D 會快取轉換後的邊界，因此比 <xref:System.Windows.Media.Media3D.GeometryModel3D> 更「厚重」。  GeometryModel3D 是模型時有最佳效能；而 ModelVisual3D 是場景節點時則有最佳效能。  請使用 ModelVisual3D 將共用的 GeometryModel3D 執行個體放入場景中。|  
|<xref:System.Windows.Media.Media3D.Light>|減少您在場景中變更光源數的次數。  除非該組態之前已經存在 \(因此其著色器已快取\)，否則每次變更光源數量都會迫使著色器重新產生和重新編譯。|  
|Light|您看不見黑色光源，但它們也會增加呈現時間；請考慮別使用它們。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|若要在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中減少大型集合的建構時間，如 MeshGeometry3D 的 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>、<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>、<xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> 和 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>，請在填入值之前預先調整集合的大小。  可能的話，請傳遞已預先填入資料結構 \(如陣列或 List\) 的集合的建構函式。|  
  
## 請參閱  
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)