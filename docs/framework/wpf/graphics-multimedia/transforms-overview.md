---
title: "轉換概觀 | Microsoft Docs"
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
  - "2D 轉換類別"
  - "類別, 2D 轉換"
  - "FrameworkElement 物件, 旋轉"
  - "FrameworkElement 物件, 縮放比例"
  - "FrameworkElement 物件, 扭曲"
  - "FrameworkElement 物件, 轉譯"
  - "轉換類別, 2D"
  - "轉換, 關於轉換"
  - "轉換, 關於轉換"
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 轉換概觀
本主題說明如何使用 [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> 類別旋轉、縮放、移動 \(轉換\) 和傾斜 <xref:System.Windows.FrameworkElement> 物件。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="whatIsATransformSection"></a>   
## 什麼是轉換  
 <xref:System.Windows.Media.Transform> 會定義如何將某個座標空間的點對應或轉換到另一個座標空間。  此對應關係會由轉換 <xref:System.Windows.Media.Matrix> 描述，這是一個由三個資料列和三個資料行的 <xref:System.Double> 值組成的集合。  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 使用以資料列為主的矩陣。  向量會以資料列向量表示，而非資料行向量。  
  
 下表顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 矩陣的結構。  
  
### 二維轉換矩陣  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> 預設：1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> 預設：0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> 預設：0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> 預設：1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> 預設：0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> 預設：0.0|1.0|  
  
 藉由操作矩陣值，您可以旋轉、縮放、傾斜和移動 \(轉換\) 物件。  例如，如果您將第三列第一行的值 \(<xref:System.Windows.Media.Matrix.OffsetX%2A> 值\) 改成 100，就可以將物件沿著 X 軸移動 100 個單位。  如果將第二列的第二行的值變更為 3，可以將物件放大成目前高度的三倍。  如果您變更這兩個值，就會將物件沿著 X 軸移動 100 個單位，且高度延伸 3 倍。  由於 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 僅支援仿射轉換，因此右欄中的值一律為 0, 0, 1。  
  
 雖然 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 可讓您直接操作矩陣值，但它也提供多個 <xref:System.Windows.Media.Transform> 類別，無須知道基礎矩陣結構的設定方式，就可以轉換物件。  例如，<xref:System.Windows.Media.ScaleTransform> 類別可讓您設定其 <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 和 <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 屬性來縮放物件，而無須操作轉換矩陣。  同樣地，只要設定 <xref:System.Windows.Media.RotateTransform> 類別的 <xref:System.Windows.Media.RotateTransform.Angle%2A> 屬性，就可以旋轉物件。  
  
<a name="transformClassesSection"></a>   
## 轉換類別  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 針對常見的轉換操作，提供下列 [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> 類別：  
  
|類別|描述|範例|示意圖|  
|--------|--------|--------|---------|  
|<xref:System.Windows.Media.RotateTransform>|以指定的 <xref:System.Windows.Media.RotateTransform.Angle%2A> 旋轉項目。|[旋轉物件](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object.md)||  
|<xref:System.Windows.Media.ScaleTransform>|以指定的 <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 和 <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 大小縮放項目。|[縮放項目](../../../../docs/framework/wpf/graphics-multimedia/how-to-scale-an-element.md)||  
|<xref:System.Windows.Media.SkewTransform>|以指定的 <xref:System.Windows.Media.SkewTransform.AngleX%2A> 和 <xref:System.Windows.Media.SkewTransform.AngleY%2A> 角度傾斜項目。|[傾斜項目](../../../../docs/framework/wpf/graphics-multimedia/how-to-skew-an-element.md)||  
|<xref:System.Windows.Media.TranslateTransform>|以指定的 <xref:System.Windows.Media.TranslateTransform.X%2A> 和 <xref:System.Windows.Media.TranslateTransform.Y%2A> 單位移動 \(轉換\) 項目。|[轉譯項目](../../../../docs/framework/wpf/graphics-multimedia/how-to-translate-an-element.md)||  
  
 如需建立更複雜的轉換，[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 則提供了下列兩個類別：  
  
|類別|描述|範例|  
|--------|--------|--------|  
|<xref:System.Windows.Media.TransformGroup>|將多個 <xref:System.Windows.Media.TransformGroup> 物件組成單一 <xref:System.Windows.Media.Transform>，然後再套用轉換屬性。|[套用多重轉換至物件](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|建立其他 <xref:System.Windows.Media.Transform> 類別沒有提供的自訂轉換。  當您使用 <xref:System.Windows.Media.MatrixTransform> 時，是直接操作矩陣。|[使用 MatrixTransform 建立自訂轉換](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 也提供[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]轉換。  如需詳細資訊，請參閱 <xref:System.Windows.Media.Media3D.Transform3D> 類別。  
  
<a name="transformationproperties"></a>   
## 常見轉換屬性  
 轉換物件的一個方法就是宣告適當的 <xref:System.Windows.Media.Transform> 型別，然後將它套用到物件的轉換屬性。  物件的型別不同，轉換屬性也不同。  下表列出幾個常用的 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 型別及其轉換屬性。  
  
|型別|轉換屬性|  
|--------|----------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## 轉換和座標系統  
 當您轉換物件時，不只轉換物件本身，同時也轉換了物件所在的座標空間。  根據預設，轉換會置於目標物件座標系統原點的中央：\(0,0\)。  唯一的例外是 <xref:System.Windows.Media.TranslateTransform>，<xref:System.Windows.Media.TranslateTransform> 沒有置中屬性可設定，因為不論位於何處的中央，轉換效果都相同。  
  
 下列範例使用 <xref:System.Windows.Media.RotateTransform>，以預設中心 \(0, 0\) 為準，旋轉 <xref:System.Windows.Shapes.Rectangle> 項目 \(<xref:System.Windows.FrameworkElement> 的一種\) 45 度角。  下圖顯示旋轉的效果。  
  
 ![對 &#40;0,0&#41; 旋轉 45 度的 FrameworkElement](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm\_FE\_rotated\_about\_upperleft\_corner")  
矩形項目以點 \(0,0\) 為準旋轉 45 度角  
  
 [!code-xml[Transforms_snip#TransformsFERotatedAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 根據預設，項目會以左上角 \(0, 0\) 為中心來旋轉。  <xref:System.Windows.Media.RotateTransform>、<xref:System.Windows.Media.ScaleTransform> 和 <xref:System.Windows.Media.SkewTransform> 類別提供 CenterX 和 CenterY 屬性，可讓您設定套用轉換的點。  
  
 下面的範例也使用 <xref:System.Windows.Media.RotateTransform> 旋轉 <xref:System.Windows.Shapes.Rectangle> 項目 45 度角，不過，這次會設定 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 和 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 屬性，讓 <xref:System.Windows.Media.RotateTransform> 的中心成為 \(25, 25\)。  下圖顯示旋轉的效果。  
  
 ![以 &#40;25, 25&#41; 為中心旋轉 45 度的幾何圖形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-center.png "graphicsmm\_FE\_rotated\_about\_center")  
矩形項目以點 \(25, 25\) 為準旋轉 45 度角  
  
 [!code-xml[Transforms_snip#TransformsFERotatedAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## 轉換 FrameworkElement  
 若要將轉換套用到 <xref:System.Windows.FrameworkElement>，請建立 <xref:System.Windows.Media.Transform> 並將它套用到 <xref:System.Windows.FrameworkElement> 類別提供的兩個屬性的其中一個：  
  
-   <xref:System.Windows.FrameworkElement.LayoutTransform%2A>：在配置傳遞前套用的轉換。  套用轉換之後，版面配置系統會處理項目的轉換後大小和位置。  
  
-   <xref:System.Windows.UIElement.RenderTransform%2A>：修改項目外觀的轉換，但會在版面配置傳遞完成後套用。  使用 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性代替 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 屬性有助於改善效能。  
  
 那麼應該使用哪個屬性？  由於具備效能優點，請盡量使用 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性，特別是使用動畫 <xref:System.Windows.Media.Transform> 物件時。  但若在縮放、旋轉或傾斜項目時，需要項目的父項調整成項目轉換後的大小，請使用 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 屬性。  請注意，與 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 屬性一起使用時，<xref:System.Windows.Media.TranslateTransform> 物件看起來似乎對項目沒有作用。  這是因為版面配置系統在處理時，會將轉換後的項目傳回原始位置。  
  
 如需 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 版面配置的詳細資訊，請參閱[配置](../../../../docs/framework/wpf/advanced/layout.md)概觀。  
  
<a name="exampleRotateAnElement45degSection"></a>   
## 範例：旋轉 FrameworkElement 45 度角  
 下列範例會使用 <xref:System.Windows.Media.RotateTransform> 順時針旋轉按鈕 45 度。  此按鈕包含在還有其他兩個按鈕的 <xref:System.Windows.Controls.StackPanel> 中。  
  
 根據預設，<xref:System.Windows.Media.RotateTransform> 會以點 \(0, 0\) 為中心旋轉。  由於範例沒有指定中心值，按鈕會以點 \(0, 0\)，也就是左上角為中心旋轉。  <xref:System.Windows.Media.RotateTransform> 會套用到 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性。  下圖顯示轉換的結果。  
  
 ![使用 RenderTransform 經過轉換的按鈕](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm\_RenderTransformWithDefaultCenter")  
從左上角順時針旋轉 45 度  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 下面範例也使用 <xref:System.Windows.Media.RotateTransform> 旋轉順時針旋轉按鈕 45 度，但同時也將按鈕的 <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 設為 \(0.5, 0.5\)。  <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 屬性的值是與按鈕的大小相對的。  因此，旋轉會套用到按鈕的中心，而非左上角。  下圖顯示轉換的結果。  
  
 ![對其中心轉換的按鈕](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm\_RenderTransformRelativeCenter")  
以中心為準順時針旋轉 45 度  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 下列範例會使用 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 屬性 \(而非 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性\) 旋轉按鈕。  這會使轉換影響按鈕的版面配置，觸發版面配置系統完全傳遞。  因此，按鈕會旋轉再重新調整位置，因為其大小已經變更。  下圖顯示轉換的結果。  
  
 ![使用 LayoutTransform 經過轉換的按鈕](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-layouttransform.png "graphicsmm\_LayoutTransform")  
用來旋轉按鈕的 LayoutTransform  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## 將轉換顯示為動畫  
 <xref:System.Windows.Media.Transform> 類別繼承自 <xref:System.Windows.Media.Animation.Animatable> 類別，因此可以顯示為動畫。  若要將 <xref:System.Windows.Media.Transform> 顯示為動畫，請將相容型別的動畫套用到要顯示為動畫的屬性。  
  
 下列範例將 <xref:System.Windows.Media.Animation.Storyboard> 和 <xref:System.Windows.Media.Animation.DoubleAnimation> 與 <xref:System.Windows.Media.RotateTransform> 一起使用，讓 <xref:System.Windows.Controls.Button> 在按一下時就地旋轉。  
  
 [!code-xml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 如需完整範例，請參閱 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252) \(英文\)。  如需動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
<a name="freezable_features"></a>   
## Freezable 功能  
 <xref:System.Windows.Media.Transform> 類別繼承自 <xref:System.Windows.Freezable> 類別，因此可以提供數項特殊功能：<xref:System.Windows.Media.Transform> 物件可以宣告為[資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)、供多個物件共用、設成唯讀以提升效能、複製以及設成安全執行緒 \(Thread\-Safe\)。  如需 <xref:System.Windows.Freezable> 物件所提供不同功能的詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.Matrix>   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)   
 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252)