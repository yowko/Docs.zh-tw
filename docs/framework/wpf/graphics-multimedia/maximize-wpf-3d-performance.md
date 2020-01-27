---
title: 最大化3D 效能
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: 414a4677a1e05cd69c382e35194328d6ce1bddf9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744591"
---
# <a name="maximize-wpf-3d-performance"></a>最大化 WPF 3D 效能
當您使用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 來建立3D 控制項，並在應用程式中包含3D 場景時，請務必考慮效能優化。 本主題提供具有應用程式效能影響的3D 類別和屬性清單，以及使用它們時優化效能的建議。  
  
 本主題假設您已深入瞭解 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D 功能。 本檔中的建議適用于「轉譯層2」，大致定義為支援圖元著色器版本2.0 和頂點著色器2.0 版的硬體。 如需詳細資訊，請參閱[圖形轉譯層](../advanced/graphics-rendering-tiers.md)。  
  
## <a name="performance-impact-high"></a>效能影響：高  
  
|屬性|建議|  
|-|-|  
|<xref:System.Windows.Media.Brush>|筆刷速度（最快到最慢）：<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> （快取）<br /><br /> <xref:System.Windows.Media.VisualBrush> （快取）<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> （未快取）<br /><br /> <xref:System.Windows.Media.VisualBrush> （未快取）|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|當您不需要讓 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 明確地將 <xref:System.Windows.Controls.Viewport3D> 的內容裁剪至 Viewport3D's 矩形時，請將 `Viewport3D.ClipToBounds` 設定為 false。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 反鋸齒的裁剪可能非常緩慢，而且預設會在 <xref:System.Windows.Controls.Viewport3D>上啟用 `ClipToBounds` （慢）。|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|每當您在執行滑鼠點擊測試時不 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 需要考慮 <xref:System.Windows.Controls.Viewport3D> 內容時，請將 `Viewport3D.IsHitTestVisible` 設定為 false。  點擊測試3D 內容是在軟體中完成，可能會因為大型網格而變慢。 <xref:System.Windows.UIElement.IsHitTestVisible%2A> 在 <xref:System.Windows.Controls.Viewport3D>上預設為啟用（緩慢）。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|只有在需要不同的材質或轉換時，才建立不同的模型。  否則，請嘗試結合許多具有相同資料的 <xref:System.Windows.Media.Media3D.GeometryModel3D> 實例，並轉換成較大的 <xref:System.Windows.Media.Media3D.GeometryModel3D> 和 <xref:System.Windows.Media.Media3D.MeshGeometry3D> 實例。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|網格動畫：變更每個畫面格的網格個別頂點，在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]中不一定有效。  若要將每個頂點修改時變更通知的效能影響降至最低，請在執行每個頂點修改之前，先從視覺化樹狀結構卸離網格。  一旦網格已修改，請將其重新附加至視覺化樹狀結構。  此外，請嘗試將以這種方式繪製動畫的網格大小降到最低。|  
|3D 消除鋸齒|若要增加轉譯速度，請在 <xref:System.Windows.Controls.Viewport3D> 上停用取樣，方法是將附加屬性 <xref:System.Windows.Media.RenderOptions.EdgeMode%2A> 設定為 [`Aliased`]。  根據預設，Windows 上會啟用3D 消除鋸齒功能，每圖元4個樣本。|  
|文字|3D 場景中的即時文字（即時，因為它是在 <xref:System.Windows.Media.DrawingBrush> 或 <xref:System.Windows.Media.VisualBrush>中）可能會變慢。 除非文字會變更，否則請嘗試改用文字的影像（透過 <xref:System.Windows.Media.Imaging.RenderTargetBitmap>）。|  
|<xref:System.Windows.Media.TileBrush>|如果您必須使用 <xref:System.Windows.Media.VisualBrush> 或3D 場景中的 <xref:System.Windows.Media.DrawingBrush>，因為筆刷的內容不是靜態的，請嘗試快取筆刷（將附加 <xref:System.Windows.Media.RenderOptions.CachingHint%2A> 屬性設定為 `Cache`）。  設定最小和最大刻度失效閾值（使用附加屬性 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> 和 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>），如此一來，快取的筆刷就不會太頻繁地重新產生，同時仍維持您所需的品質等級。  根據預設，<xref:System.Windows.Media.DrawingBrush> 和 <xref:System.Windows.Media.VisualBrush> 不會進行快取，這表示每次與筆刷一併繪製的內容都必須重新轉譯時，筆刷的整個內容必須先重新轉譯成中繼表面。|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect> 強制轉譯所有受影響的內容，而不需要硬體加速。  為了達到最佳效能，請不要使用 <xref:System.Windows.Media.Effects.BitmapEffect>。|  
  
## <a name="performance-impact-medium"></a>效能影響：中  
  
|屬性|建議|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|當網格定義為具有共用頂點的相鄰三角形，而且這些頂點具有相同的位置、標準和材質座標時，請只定義每個共用的頂點一次，然後以 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>的索引來定義三角形。|  
|<xref:System.Windows.Media.ImageBrush>|當您明確控制大小（當您使用 <xref:System.Windows.Media.Imaging.RenderTargetBitmap> 和/或 <xref:System.Windows.Media.ImageBrush>）時，請嘗試將材質大小降至最低。  請注意，較低解析度的材質可能會降低視覺品質，因此請嘗試在品質與效能之間取得適當的平衡。|  
|不透明度|轉譯半透明的3D 內容（例如反射）時，請在筆刷或材質上使用不透明度屬性（透過 <xref:System.Windows.Media.Brush.Opacity%2A> 或 <xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>），而不是將 `Viewport3D.Opacity` 設定為小於1的值，以建立個別的半透明 <xref:System.Windows.Controls.Viewport3D>。|  
|<xref:System.Windows.Controls.Viewport3D>|將您在場景中使用的 <xref:System.Windows.Controls.Viewport3D> 物件數目降至最低。  將許多3D 模型放在同一個 Viewport3D 中，而不是為每個模型建立個別的 Viewport3D 實例。|  
|<xref:System.Windows.Freezable>|通常，重複使用 <xref:System.Windows.Media.Media3D.MeshGeometry3D>、<xref:System.Windows.Media.Media3D.GeometryModel3D>、筆刷和材質是有益的。  全都是 multiparentable，因為它們是從 `Freezable`衍生而來。|  
|<xref:System.Windows.Freezable>|當 Freezable 的屬性在您的應用程式中保持不變時，請在其上呼叫 <xref:System.Windows.Freezable.Freeze%2A> 方法。  凍結可以減少工作集並增加速度。|  
|<xref:System.Windows.Media.Brush>|當筆刷的內容不會變更時，請使用 <xref:System.Windows.Media.ImageBrush>，而不是 <xref:System.Windows.Media.VisualBrush> 或 <xref:System.Windows.Media.DrawingBrush>。  2D 內容可以透過 <xref:System.Windows.Media.Imaging.RenderTargetBitmap> 轉換成 <xref:System.Windows.Controls.Image>，然後在 <xref:System.Windows.Media.ImageBrush>中使用。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|除非您真的需要查看 <xref:System.Windows.Media.Media3D.GeometryModel3D>的背景臉部，否則請勿使用 <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>。|  
|<xref:System.Windows.Media.Media3D.Light>|輕速（最快到最慢）：<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|嘗試在下列限制之下保留網格大小：<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>： 20001 <xref:System.Windows.Media.Media3D.Point3D> 實例<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>： 60003 <xref:System.Int32> 實例|  
|<xref:System.Windows.Media.Media3D.Material>|材質速度（最快到最慢）：<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D 不會以一致的方式選擇不可見筆刷（黑色的環境筆刷、清除筆刷等）。  請考慮從場景中省略這些。|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|<xref:System.Windows.Media.Media3D.MaterialGroup> 中的每個 <xref:System.Windows.Media.Media3D.Material> 都會導致另一個轉譯行程，因此，包括許多材質，甚至是簡單的資料，都可以大幅增加 GPU 上的填滿需求。  將 <xref:System.Windows.Media.Media3D.MaterialGroup>中的材質數目降至最低。|  
  
## <a name="performance-impact-low"></a>效能影響：低  
  
|屬性|建議|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|當您不需要動畫或資料系結，而不是使用包含多個轉換的轉換群組時，請使用單一 <xref:System.Windows.Media.Media3D.MatrixTransform3D>，將其設定為不會在轉換群組中獨立存在之所有轉換的乘積。|  
|<xref:System.Windows.Media.Media3D.Light>|將場景中的燈數目降至最低。 場景中有太多光源會強制 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 切換回軟體轉譯。  限制大約是 110 <xref:System.Windows.Media.Media3D.DirectionalLight> 物件、70 <xref:System.Windows.Media.Media3D.PointLight> 物件或 40 <xref:System.Windows.Media.Media3D.SpotLight> 物件。|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|將物件放在不同的 <xref:System.Windows.Media.Media3D.ModelVisual3D> 實例中，藉以區分其與靜態物件的移動。  ModelVisual3D 比 <xref:System.Windows.Media.Media3D.GeometryModel3D> 「粗」，因為它會快取已轉換的界限。  GeometryModel3D 已優化為模型;ModelVisual3D 已優化為場景節點。  使用 ModelVisual3D 將 GeometryModel3D 的共用實例放入場景中。|  
|<xref:System.Windows.Media.Media3D.Light>|將變更場景中光源數的次數減至最少。  光線計數的每項變更都會強制執行著色器重新產生和重新編譯，除非先前已有該設定（因此已快取其著色器）。|  
|Light|黑色光源不會顯示出來，但會加入轉譯時間;請考慮將它們省略。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|若要將 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]中大型集合的結構時間最小化，例如 MeshGeometry3D's <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>、<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>、<xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>和 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>，請在值擴展之前預先調整集合的大小。 可能的話，請傳遞集合的函式預先填入資料結構（例如陣列或清單）。|  
  
## <a name="see-also"></a>請參閱

- [立體圖形概觀](3-d-graphics-overview.md)
