---
title: 最大化 WPF 3D 效能
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: 6677ee3a6d17ea38636d49327d7af22b53bc900e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565434"
---
# <a name="maximize-wpf-3d-performance"></a>最大化 WPF 3D 效能
當您使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]建置 3D 控制項，並包含在應用程式中的 3D 場景，它是很重要考量效能最佳化。 本主題提供 3D 類別和應用程式，以及當您使用這些最佳化效能的建議事項會影響效能的屬性的清單。  
  
 本主題假設進階的瞭解[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3D 功能。 這份文件中的建議套用至 「 轉譯層 2 」，大致上定義為支援像素著色器 2.0 版和頂點著色器 2.0 版的硬體。 如需詳細資訊，請參閱[圖形呈現層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)。  
  
## <a name="performance-impact-high"></a>效能的影響： 高  
  
|屬性|建議|  
|-|-|  
|<xref:System.Windows.Media.Brush>|筆刷速度 （最快到最慢）：<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> （快取）<br /><br /> <xref:System.Windows.Media.VisualBrush> （快取）<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> （未快取）<br /><br /> <xref:System.Windows.Media.VisualBrush> （未快取）|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|設定`Viewport3D.ClipToBounds`為 false 時不需要有[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]明確裁剪內容<xref:System.Windows.Controls.Viewport3D>Viewport3D 的矩形。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 反鋸齒補償裁剪可能會非常慢，和`ClipToBounds`預設為啟用 （慢） 上<xref:System.Windows.Controls.Viewport3D>。|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|設定`Viewport3D.IsHitTestVisible`為 false 時不需要[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]要考慮的內容<xref:System.Windows.Controls.Viewport3D>執行滑鼠點擊測試。  點擊測試的 3D 內容會在軟體中完成，而且可以是大型網狀結構慢。 <xref:System.Windows.UIElement.IsHitTestVisible%2A> 預設為啟用 （慢） 上<xref:System.Windows.Controls.Viewport3D>。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|它們需要不同的資料或轉換時，才建立不同的模型。  否則，嘗試聯合許多<xref:System.Windows.Media.Media3D.GeometryModel3D>成一些較大的執行個體具有相同的資料和轉換<xref:System.Windows.Media.Media3D.GeometryModel3D>和<xref:System.Windows.Media.Media3D.MeshGeometry3D>執行個體。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Mesh 動畫 — 變更個別畫面格為基礎的 mesh 的個別端點 — 不一定有效率[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  若要修改每個頂點時降低變更通知的效能影響，卸離執行每個頂點修改之前的視覺化樹狀結構從網狀結構。  一旦網狀結構已被修改，重新附加它的視覺化樹狀結構。  此外，請嘗試以這種方式建立動畫的網狀結構的大小降到最低。|  
|3D 反鋸齒功能|若要增加呈現的速度，停用多重採樣<xref:System.Windows.Controls.Viewport3D>藉由設定附加的屬性<xref:System.Windows.Media.RenderOptions.EdgeMode%2A>至`Aliased`。  根據預設，3D 的消除鋸齒會停用[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]並在上啟用[!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)]4 的範例，每個像素。|  
|Text|Live 3D 場景中的文字 (live 因為它處於<xref:System.Windows.Media.DrawingBrush>或<xref:System.Windows.Media.VisualBrush>) 可能會很慢。 請嘗試改為使用映像的文字 (透過<xref:System.Windows.Media.Imaging.RenderTargetBitmap>) 除非的文字會改變。|  
|<xref:System.Windows.Media.TileBrush>|如果您必須使用<xref:System.Windows.Media.VisualBrush>或<xref:System.Windows.Media.DrawingBrush>3D 場景中因為筆刷的內容不是靜態的再試一次快取的筆刷 (設定附加的屬性<xref:System.Windows.Media.RenderOptions.CachingHint%2A>至`Cache`)。  設定最小和最大刻度失效的臨界值 (與附加的屬性<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A>和<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>)，以便快取的筆刷不會重新產生頻率太高，同時仍維持您所需的層級的品質。  根據預設，<xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>不會快取，這表示，每次使用筆刷繪製的項目必須為重新轉譯，筆刷的整個內容必須先重新轉譯為中繼的介面。|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect> 強制所有受影響的內容，但不限於硬體加速呈現。  為了達到最佳效能，請勿使用<xref:System.Windows.Media.Effects.BitmapEffect>。|  
  
## <a name="performance-impact-medium"></a>效能的影響： 中  
  
|屬性|建議|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|當網狀結構定義為鄰接三角形有共用的頂點，這些端點擁有相同的位置、 normal 和材質座標，定義每個共用的頂點僅一次，而且然後使用索引來定義您三角形<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>。|  
|<xref:System.Windows.Media.ImageBrush>|嘗試減少紋理大小時您可以明確控制大小 (當您使用<xref:System.Windows.Media.Imaging.RenderTargetBitmap>及/或<xref:System.Windows.Media.ImageBrush>)。  請注意，較低解析度的紋理可以減少視覺品質，因此嘗試尋找品質與效能之間的正確平衡。|  
|不透明度|當半透明的 3D 轉譯內容 （例如反射） 時，使用的不透明度屬性上筆刷或資料 (透過<xref:System.Windows.Media.Brush.Opacity%2A>或<xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>) 而不是建立另一個半透明<xref:System.Windows.Controls.Viewport3D>藉由設定`Viewport3D.Opacity`小於 1 的值。|  
|<xref:System.Windows.Controls.Viewport3D>|減少數目<xref:System.Windows.Controls.Viewport3D>場景中使用的物件。  將許多 3D 模型放在相同的 Viewport3D，而不會建立每個模型的個別 Viewport3D 執行個體。|  
|<xref:System.Windows.Freezable>|通常很有幫助重複使用<xref:System.Windows.Media.Media3D.MeshGeometry3D>， <xref:System.Windows.Media.Media3D.GeometryModel3D>，筆刷和資料。  所有都 multiparentable，因為它們衍生自`Freezable`。|  
|<xref:System.Windows.Freezable>|呼叫<xref:System.Windows.Freezable.Freeze%2A>Freezable 時將會保留其屬性上的方法不變更您的應用程式中。  凍結可以降低工作集，並加快速度。|  
|<xref:System.Windows.Media.Brush>|使用<xref:System.Windows.Media.ImageBrush>而不是<xref:System.Windows.Media.VisualBrush>或<xref:System.Windows.Media.DrawingBrush>時不會變更筆刷的內容。  2D 內容可以轉換成<xref:System.Windows.Controls.Image>透過<xref:System.Windows.Media.Imaging.RenderTargetBitmap>並接著用於<xref:System.Windows.Media.ImageBrush>。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|請勿使用<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>除非您確實需要查看背景表面您<xref:System.Windows.Media.Media3D.GeometryModel3D>。|  
|<xref:System.Windows.Media.Media3D.Light>|淺色速度 （最快到最慢）：<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|嘗試保留在這些限制的網狀結構大小：<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>: 20,001<xref:System.Windows.Media.Media3D.Point3D>執行個體<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>: 60,003<xref:System.Int32>執行個體|  
|<xref:System.Windows.Media.Media3D.Material>|材質的速度 （最快到最慢）：<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D 不退出一致的方式不可見的筆刷 （黑色的環境筆刷、 清除的筆刷等）。  請考慮從場景省略。|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|每個<xref:System.Windows.Media.Media3D.Material>中<xref:System.Windows.Media.Media3D.MaterialGroup>導致另一個轉譯階段，因此包含許多資料，即使是簡單的資料，可以大幅提升您的 GPU 的填滿需求。  中材質數目最小化您<xref:System.Windows.Media.Media3D.MaterialGroup>。|  
  
## <a name="performance-impact-low"></a>效能的影響： 低  
  
|屬性|建議|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|當您不需要動畫，或資料繫結，而不使用此轉換群組中包含多個轉換，使用單一<xref:System.Windows.Media.Media3D.MatrixTransform3D>，它會存在，則為獨立轉換群組中的所有轉換的產品設定。|  
|<xref:System.Windows.Media.Media3D.Light>|場景中的光源數目降到最低。 場景中太多的燈號會強制[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]来改為使用軟體呈現。  限制大致上是 110<xref:System.Windows.Media.Media3D.DirectionalLight>物件，70<xref:System.Windows.Media.Media3D.PointLight>物件或 40<xref:System.Windows.Media.Media3D.SpotLight>物件。|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|從靜態物件移動物件，方法是將它們放置在不同的分隔<xref:System.Windows.Media.Media3D.ModelVisual3D>執行個體。  ModelVisual3D 是 「 高 」 比<xref:System.Windows.Media.Media3D.GeometryModel3D>因為它會快取已轉換的範圍。  GeometryModel3D 經過最佳化能夠模型;ModelVisual3D，已完成最佳化場景節點。  使用 ModelVisual3D GeometryModel3D 的共用執行個體放在場景。|  
|<xref:System.Windows.Media.Media3D.Light>|您變更場景中的燈號的數字的次數降到最低。  淺色計數在每次變更強制的著色器重新產生金鑰和重新編譯，除非該組態之前已經存在 （並因此有其著色器快取）。|  
|亮色調|黑色燈號不會顯示，但是這些物件會加入要呈現的時間;請考慮省略它們。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|最小化的大型集合，在建構階段[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]，例如 MeshGeometry3D <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>， <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>， <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>，和<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>，預先調整大小的集合值的母體擴展之前。 可能的話，請傳遞的集合的建構函式已預先填入的資料結構，例如陣列或清單。|  
  
## <a name="see-also"></a>另請參閱  
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
