---
title: 最大化 WPF 3D 效能
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: 8629748c37aae8e35bb928c5a8d5a9caa7046942
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785680"
---
# <a name="maximize-wpf-3d-performance"></a>最大化 WPF 3D 效能
當您使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]建置 3D 的控制項，並納入您的應用程式的 3D 場景，務必考慮效能最佳化。 本主題提供 3D 類別和應用程式，以及最佳化效能，當您使用它們時的建議會影響效能的屬性的清單。  
  
 本主題假設有進階了解[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3D 功能。 這份文件中的建議套用到 「 轉譯層 2 」，大致上定義為支援的像素著色器版本 2.0 和頂點著色器 2.0 版的硬體。 如需詳細資訊，請參閱 <<c0> [ 圖形轉譯層](../advanced/graphics-rendering-tiers.md)。  
  
## <a name="performance-impact-high"></a>對效能的影響：High  
  
|屬性|建議|  
|-|-|  
|<xref:System.Windows.Media.Brush>|筆刷速度 （最快到最慢）：<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> （快取）<br /><br /> <xref:System.Windows.Media.VisualBrush> （快取）<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> （未快取）<br /><br /> <xref:System.Windows.Media.VisualBrush> （未快取）|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|設定`Viewport3D.ClipToBounds`為 false 時不需要有[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]明確裁剪的內容， <xref:System.Windows.Controls.Viewport3D> Viewport3D 的矩形。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 反鋸齒補償裁剪可能會很慢，以及`ClipToBounds`預設為啟用 （慢） 上<xref:System.Windows.Controls.Viewport3D>。|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|設定`Viewport3D.IsHitTestVisible`為 false，只要您不需要[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]要考慮的內容<xref:System.Windows.Controls.Viewport3D>執行滑鼠點擊測試。  點擊測試的 3D 內容在軟體中完成，而且可以是使用大型的網格變慢。 <xref:System.Windows.UIElement.IsHitTestVisible%2A> 預設為啟用 （慢） 上<xref:System.Windows.Controls.Viewport3D>。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|前提是它們需要不同的資料或轉換，請建立不同的模型。  否則，嘗試許多聯合<xref:System.Windows.Media.Media3D.GeometryModel3D>具有相同的資料和轉換的執行個體，加入一些較大<xref:System.Windows.Media.Media3D.GeometryModel3D>和<xref:System.Windows.Media.Media3D.MeshGeometry3D>執行個體。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Mesh 動畫 — 變更個別以每個畫面格為基礎的網格的頂點，並不一定有效率[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  效能的影響降到變更通知的每個頂點遭到修改時，中斷連結執行每個頂點修改之前，從視覺化樹狀結構網狀結構。  之後已修改網格，請將它重新附加至視覺化樹狀結構。  此外，請嘗試以這種方式建立動畫的網狀結構的大小降到最低。|  
|3D 消除鋸齒功能|若要提高轉譯速度，停用多重取樣<xref:System.Windows.Controls.Viewport3D>藉由設定附加的屬性<xref:System.Windows.Media.RenderOptions.EdgeMode%2A>至`Aliased`。  根據預設，3D 消除鋸齒功能會停用[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]並在上啟用[!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)]4 的範例，每像素。|  
|文字|Live 3D 場景中的文字 (live，因為它處於<xref:System.Windows.Media.DrawingBrush>或<xref:System.Windows.Media.VisualBrush>) 可能會很慢。 請嘗試改為使用映像的文字 (透過<xref:System.Windows.Media.Imaging.RenderTargetBitmap>) 除非文字會變更。|  
|<xref:System.Windows.Media.TileBrush>|如果您必須使用<xref:System.Windows.Media.VisualBrush>或是<xref:System.Windows.Media.DrawingBrush>3D 場景中的筆刷的內容不是靜態的因為嘗試快取的筆刷 (設定附加的屬性<xref:System.Windows.Media.RenderOptions.CachingHint%2A>至`Cache`)。  設定最小和最大刻度失效臨界值 (以附加屬性<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A>和<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>)，讓快取的筆刷不會重新產生頻率太高，同時仍可保有您所需的層級的品質。  根據預設，<xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>不會快取，這表示，每次使用筆刷繪製的項目必須為重新轉譯，筆刷的整個內容必須先重新呈現到中繼的介面。|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect> 強制所有受影響的內容，而不需要硬體加速呈現。  為了達到最佳效能，請勿使用<xref:System.Windows.Media.Effects.BitmapEffect>。|  
  
## <a name="performance-impact-medium"></a>對效能的影響：Medium  
  
|屬性|建議|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|當網狀結構定義為鄰接的三角形使用共用的頂點，且這些頂點會具有相同的位置、 normal 和紋理座標時，一次定義每個共用的頂點，然後定義您的三角形索引<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>。|  
|<xref:System.Windows.Media.ImageBrush>|嘗試時您可以明確控制大小相較之下，將紋理大小降至最低 (當您使用<xref:System.Windows.Media.Imaging.RenderTargetBitmap>及/或<xref:System.Windows.Media.ImageBrush>)。  請注意，較低的解析度紋理可以減少視覺品質，因此試著找出品質與效能之間的平衡點。|  
|不透明度|當呈現半透明的 3D 內容 （例如反映），使用不透明度屬性筆刷或資料 (透過<xref:System.Windows.Media.Brush.Opacity%2A>或<xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>) 而不是建立個別的半透明<xref:System.Windows.Controls.Viewport3D>藉由設定`Viewport3D.Opacity`小於 1 的值。|  
|<xref:System.Windows.Controls.Viewport3D>|減少數量<xref:System.Windows.Controls.Viewport3D>物件在場景中使用。  將許多的 3D 模型放在同一個 Viewport3D，而不是建立每個模型的個別 Viewport3D 執行個體。|  
|<xref:System.Windows.Freezable>|通常很有幫助重複使用<xref:System.Windows.Media.Media3D.MeshGeometry3D>， <xref:System.Windows.Media.Media3D.GeometryModel3D>，筆刷和材料。  所有都是 multiparentable，因為它們衍生自`Freezable`。|  
|<xref:System.Windows.Freezable>|呼叫<xref:System.Windows.Freezable.Freeze%2A>Freezable 時其屬性會保留上的方法不會變更應用程式中。  凍結可以降低工作集，並加快速度。|  
|<xref:System.Windows.Media.Brush>|使用<xref:System.Windows.Media.ImageBrush>而非<xref:System.Windows.Media.VisualBrush>或<xref:System.Windows.Media.DrawingBrush>時不會變更到筆刷的內容。  2D 內容可以轉換成<xref:System.Windows.Controls.Image>經由<xref:System.Windows.Media.Imaging.RenderTargetBitmap>並接著用於<xref:System.Windows.Media.ImageBrush>。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|不用<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>除非您真的需要查看後的臉部您<xref:System.Windows.Media.Media3D.GeometryModel3D>。|  
|<xref:System.Windows.Media.Media3D.Light>|淺的速度 （最快到最慢）：<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|嘗試保留在這些限制的網格大小：<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>：20001<xref:System.Windows.Media.Media3D.Point3D>執行個體<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>：60,003<xref:System.Int32>執行個體|  
|<xref:System.Windows.Media.Media3D.Material>|材質的速度 （最快到最慢）：<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D 並未退出一致的方式不可見的筆刷 （黑色的環境筆刷、 清楚的筆刷等）。  請考慮從場景省略。|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|每個<xref:System.Windows.Media.Media3D.Material>在<xref:System.Windows.Media.Media3D.MaterialGroup>會導致另一個轉譯階段，因此包含許多資料，甚至是簡單的資料，可能會大幅增加您的 GPU 的填滿需求。  中的資料數目降到最低您<xref:System.Windows.Media.Media3D.MaterialGroup>。|  
  
## <a name="performance-impact-low"></a>對效能的影響：低  
  
|屬性|建議|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|當您不需要動畫或資料繫結，而不使用此轉換群組中包含多個轉換，使用單一<xref:System.Windows.Media.Media3D.MatrixTransform3D>，設定為，否則會轉換群組中獨立存在的所有轉換的乘積。|  
|<xref:System.Windows.Media.Media3D.Light>|場景中的燈號數目降至最低。 在場景中的太多燈號會強制[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]回到軟體轉譯。  這些限制大致上是 110<xref:System.Windows.Media.Media3D.DirectionalLight>物件，70<xref:System.Windows.Media.Media3D.PointLight>物件或 40<xref:System.Windows.Media.Media3D.SpotLight>物件。|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|不同的靜態物件移動物件，請將它們放在不同<xref:System.Windows.Media.Media3D.ModelVisual3D>執行個體。  ModelVisual3D 是 「 比更繁重"<xref:System.Windows.Media.Media3D.GeometryModel3D>因為它會快取已轉換的範圍。  GeometryModel3D 最佳化模型;ModelVisual3D 已最佳化，是場景節點。  您可以使用 ModelVisual3D，放在場景的 GeometryModel3D 的共用執行個體。|  
|<xref:System.Windows.Media.Media3D.Light>|您變更在場景中的號誌的數字的次數降到最低。  淺計數在每次變更強制的著色器重新產生和重新編譯，除非該組態之前已經存在 （且因此有其著色器快取）。|  
|亮色調|黑色燈號不可見，但它們也會增加轉譯時間;請考慮省略它們。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|若要將大型集合中的建構時間降至最低[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]，例如 MeshGeometry3D <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>， <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>， <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>，和<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>，預先調整大小的集合值的母體擴展之前。 可能的話，請傳遞集合的建構函式預先填入的資料結構，例如陣列或清單。|  
  
## <a name="see-also"></a>另請參閱

- [立體圖形概觀](3-d-graphics-overview.md)
