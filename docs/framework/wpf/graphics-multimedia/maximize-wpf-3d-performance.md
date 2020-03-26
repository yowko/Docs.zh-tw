---
title: 最大化 3D 性能
ms.date: 03/30/2017
helpviewer_keywords:
- 3D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: 3825ea8e57c6863e2ee654072efda623db21c2a8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111994"
---
# <a name="maximize-wpf-3d-performance"></a>最大化 WPF 3D 效能
當您使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]生成 3D 控制項並在應用程式中包含 3D 場景時，考慮性能優化非常重要。 本主題提供了對應用程式具有性能影響的 3D 類和屬性的清單，以及用於在使用時優化性能的建議。  
  
 本主題假定對 3D[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]功能的高級理解。 本文檔中的建議適用于"呈現第 2 層"-大致定義為支援圖元底影版本 2.0 和頂點底影版 2.0 的硬體。 有關詳細資訊，請參閱[圖形呈現層](../advanced/graphics-rendering-tiers.md)。  
  
## <a name="performance-impact-high"></a>性能影響：高  
  
|屬性|建議|  
|-|-|  
|<xref:System.Windows.Media.Brush>|畫筆速度（最快到最慢）：<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>（緩存）<br /><br /> <xref:System.Windows.Media.VisualBrush>（緩存）<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>（未緩存）<br /><br /> <xref:System.Windows.Media.VisualBrush>（未緩存）|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|只要`Viewport3D.ClipToBounds`不需要[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]顯式剪輯 到 Viewport3D 矩形的內容<xref:System.Windows.Controls.Viewport3D>，則設置為 false。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]防鋸齒裁剪可能非常慢，並且`ClipToBounds`預設在 上<xref:System.Windows.Controls.Viewport3D>啟用（慢速）。|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|每當`Viewport3D.IsHitTestVisible`執行滑鼠點擊測試時，只要[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]不考慮 的內容<xref:System.Windows.Controls.Viewport3D>，則設置為 false。  點擊測試 3D 內容在軟體中完成，並且使用大型網中速度很慢。 <xref:System.Windows.UIElement.IsHitTestVisible%2A>預設情況下啟用（慢速）在<xref:System.Windows.Controls.Viewport3D>。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|僅當不同模型需要不同的材質或變換時，才創建不同的模型。  否則，請嘗試將多個<xref:System.Windows.Media.Media3D.GeometryModel3D>實例與相同的材質合併，並將轉換為幾個較大的<xref:System.Windows.Media.Media3D.GeometryModel3D>實例。 <xref:System.Windows.Media.Media3D.MeshGeometry3D>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|網格動畫 （按幀更改網格的各個頂點） 並不總是有效[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  為了在修改每個頂點時將更改通知的性能影響降至最低，請先從可視樹中分離網格，然後再執行每個頂點修改。  修改網格後，將其重新附加到視覺化樹。  此外，嘗試最小化以這種方式進行動畫處理的網數的大小。|  
|3D 抗鋸齒|要提高渲染速度，<xref:System.Windows.Controls.Viewport3D>請通過將附加屬性<xref:System.Windows.Media.RenderOptions.EdgeMode%2A>設置為 禁用 上的多`Aliased`採樣。  預設情況下，在 Windows 上啟用 3D 防鋸齒，每圖元有 4 個樣本。|  
|Text|3D 場景中的即時文本（即時，因為它位於<xref:System.Windows.Media.DrawingBrush>或<xref:System.Windows.Media.VisualBrush>） 中，速度可能很慢。 請嘗試使用文本的圖像（通過<xref:System.Windows.Media.Imaging.RenderTargetBitmap>），除非文本將更改。|  
|<xref:System.Windows.Media.TileBrush>|如果由於畫筆的內容不是<xref:System.Windows.Media.VisualBrush>靜態的<xref:System.Windows.Media.DrawingBrush>，必須在 3D 場景中使用 或 ， 請嘗試緩存畫筆（將附加屬性<xref:System.Windows.Media.RenderOptions.CachingHint%2A>設置為 。 `Cache`  設置最小和最大比例失效閾值（具有附加屬性<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A>和<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>），以便緩存的畫筆不會過於頻繁地重新生成，同時仍保持所需的品質級別。  預設情況下，<xref:System.Windows.Media.DrawingBrush>並且<xref:System.Windows.Media.VisualBrush>不會緩存，這意味著每次必須重新渲染使用畫筆繪製的內容時，必須首先將畫筆的整個內容重新渲染到中間曲面。|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect>強制呈現所有受影響的內容，而不進行硬體加速。  為獲得最佳性能，請勿使用<xref:System.Windows.Media.Effects.BitmapEffect>。|  
  
## <a name="performance-impact-medium"></a>性能影響：中等  
  
|屬性|建議|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|當網格定義為具有共用頂點的頂點的靠邊三角形，並且這些頂點具有相同的位置、法線和紋理座標時，僅定義每個共用頂點一次，然後使用 索引定義三角形<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>。|  
|<xref:System.Windows.Media.ImageBrush>|當您對大小具有顯式控制時（當您使用<xref:System.Windows.Media.Imaging.RenderTargetBitmap>和/或 時），嘗試最小化紋理大小。 <xref:System.Windows.Media.ImageBrush>  請注意，較低的解析度紋理可能會降低視覺品質，因此請嘗試在品質和性能之間找到適當的平衡。|  
|不透明度|渲染半透明 3D 內容（如反射）時，請使用畫筆或材質上的不透明屬性（<xref:System.Windows.Media.Brush.Opacity%2A>通過或<xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>），而不是通過設置為<xref:System.Windows.Controls.Viewport3D>`Viewport3D.Opacity`小於 1 的值來創建單獨的半透明。|  
|<xref:System.Windows.Controls.Viewport3D>|最小化場景中使用的物件<xref:System.Windows.Controls.Viewport3D>數。  將許多 3D 模型放在相同的 Viewport3D 中，而不是為每個模型創建單獨的 Viewport3D 實例。|  
|<xref:System.Windows.Freezable>|通常，重複使用<xref:System.Windows.Media.Media3D.MeshGeometry3D>、、<xref:System.Windows.Media.Media3D.GeometryModel3D>畫筆和材質是有好處的。  它們都是多父級的，因為它們派生自`Freezable`。|  
|<xref:System.Windows.Freezable>|在應用程式中<xref:System.Windows.Freezable.Freeze%2A>，當其屬性保持不變時，在"可凍結"上調用該方法。  凍結可以減少工作集和提高速度。|  
|<xref:System.Windows.Media.Brush>|使用<xref:System.Windows.Media.ImageBrush>而不是<xref:System.Windows.Media.VisualBrush>或<xref:System.Windows.Media.DrawingBrush>當畫筆的內容不會更改時。  2D 內容可以轉換為通通<xref:System.Windows.Controls.Image>，<xref:System.Windows.Media.Imaging.RenderTargetBitmap>然後在 中使用<xref:System.Windows.Media.ImageBrush>。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|不要使用<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>，除非你確實需要看到你的<xref:System.Windows.Media.Media3D.GeometryModel3D>背面。|  
|<xref:System.Windows.Media.Media3D.Light>|光速（最快到最慢）：<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|嘗試將網格大小保持在以下限制下：<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>： 20，001<xref:System.Windows.Media.Media3D.Point3D>個實例<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>： 60，003<xref:System.Int32>個實例|  
|<xref:System.Windows.Media.Media3D.Material>|材料速度（最快到最慢）：<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3D 不會以一致的方式退出宣告不可見的畫筆（黑色環境畫筆、透明畫筆等）。  請考慮從場景中省略這些。|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|每個<xref:System.Windows.Media.Media3D.Material>渲染<xref:System.Windows.Media.Media3D.MaterialGroup>通道都會導致另一個渲染通道，因此包括許多材質，甚至簡單的材料，可以顯著提高 GPU 的填充需求。  最小化 中的材料數量<xref:System.Windows.Media.Media3D.MaterialGroup>。|  
  
## <a name="performance-impact-low"></a>性能影響：低  
  
|屬性|建議|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|當不需要動畫或資料繫結時，不使用包含多個轉換的轉換組，而是使用單個<xref:System.Windows.Media.Media3D.MatrixTransform3D>，將其設置為轉換組中獨立存在的所有轉換的組成。|  
|<xref:System.Windows.Media.Media3D.Light>|最小化場景中的燈光數。 場景中的燈光過多將迫使[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]其回退到軟體渲染。  限制大約 110<xref:System.Windows.Media.Media3D.DirectionalLight>個物件、70<xref:System.Windows.Media.Media3D.PointLight>個物件或<xref:System.Windows.Media.Media3D.SpotLight>40 個物件。|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|通過將移動物件放在單獨的實例中，將移動物件<xref:System.Windows.Media.Media3D.ModelVisual3D>與靜態物件分開。  ModelVisual3D 比緩存轉換的邊界<xref:System.Windows.Media.Media3D.GeometryModel3D>"更重"。  幾何模型3D被優化為模型;ModelVisual3D 已優化為場景節點。  使用 ModelVisual3D 將幾何模型 3D 的共用實例放入場景中。|  
|<xref:System.Windows.Media.Media3D.Light>|最小化更改場景中燈光數的次數。  光計數的每個更改都會強制進行底帶再生和重新編譯，除非該配置以前存在（因此緩存了其底帶）。|  
|淡|黑光不可見，但它們會增加渲染時間;考慮省略它們。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|為了最小化 在 中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]的大型集合的構造時間，例如 MeshGeometry3D<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>的<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>、和<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>，在值填充之前預調整集合的大小。 如果可能，傳遞集合的建構函式預填充的資料結構，如陣列或清單。|  
  
## <a name="see-also"></a>另請參閱

- [3D 圖形概述](3-d-graphics-overview.md)
