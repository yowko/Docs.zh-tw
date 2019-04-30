---
title: 不透明度遮罩概觀
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 84525e58487ce9b0bc26f77ff8dbced734bc90a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008425"
---
# <a name="opacity-masks-overview"></a>不透明度遮罩概觀
不透明度遮罩可讓您將元素或視覺物件的一部分設定成透明或半透明。 若要建立不透明度遮罩，套用<xref:System.Windows.Media.Brush>要<xref:System.Windows.UIElement.OpacityMask%2A>元素的屬性或<xref:System.Windows.Media.Visual>。  筆刷會對應到元素或視覺物件，且每個筆刷像素的不透明度值會用來決定元素或視覺物件每個對應像素最終的不透明度。  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>必要條件  
 此概觀假設您已熟悉<xref:System.Windows.Media.Brush>物件。 如需筆刷的概觀，請參閱[使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)。 如需<xref:System.Windows.Media.ImageBrush>並<xref:System.Windows.Media.DrawingBrush>，請參閱[使用影像、 繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>使用不透明度遮罩建立視覺效果  
 不透明度遮罩的運作方式是將其內容對應到元素或視覺物件。 然後筆刷每個像素的 Alpha 色板會用來決定元素或視覺物件所對應像素的最終不透明度 (會忽略筆刷的實際色彩)。 如果筆刷的某一部分是透明的，則元素或視覺物件相對應的部分會變成透明。 如果筆刷的某一部分是不透明的，則元素或視覺物件相對應的部分不會改變。 由不透明度遮罩所指定的不透明度會和元素或視覺物件中現有的任何不透明度設定結合。 例如，如果元素是百分之 25 不透明，並套用從完全不透明轉換成完全透明的不透明度遮罩，結果元素會從百分之 25 不透明度轉換成完全透明。  
  
> [!NOTE]
>  雖然此概觀中的範例示範如何使用影像項目上的不透明度遮罩，但不透明度遮罩可套用至任何項目或<xref:System.Windows.Media.Visual>，包括面板和控制項。  
  
 不透明度遮罩可以用來建立有趣的視覺效果，例如，建立從檢視淡出的影像或按鈕、為元素添加紋理，或結合漸層來產生玻璃般的表面。 下圖示範不透明度遮罩的使用方式。 會使用棋盤背景來表示遮罩的透明部分。  
  
 ![具有 LinearGradientBrush 不透明度遮罩的物件](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
不透明度遮罩範例  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>建立不透明度遮罩  
 若要建立不透明度遮罩，建立<xref:System.Windows.Media.Brush>套用至<xref:System.Windows.UIElement.OpacityMask%2A>元素或視覺效果的屬性。 您可以使用任何一種<xref:System.Windows.Media.Brush>作為不透明度遮罩。  
  
- <xref:System.Windows.Media.LinearGradientBrush>、<xref:System.Windows.Media.RadialGradientBrush>：用來使元素或從檢視的視覺淡出。  
  
     下圖顯示<xref:System.Windows.Media.LinearGradientBrush>作為不透明度遮罩。  
  
     ![具有 LinearGradientBrush 不透明度遮罩的物件](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
LinearGradientBrush 不透明度遮罩範例  
  
- <xref:System.Windows.Media.ImageBrush>：用來建立紋理及柔邊或撕裂邊效果。  
  
     下圖顯示<xref:System.Windows.Media.ImageBrush>作為不透明度遮罩。  
  
     ![具有 ImageBrush 不透明度遮罩的物件](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
LinearGradientBrush 不透明度遮罩範例  
  
- <xref:System.Windows.Media.DrawingBrush>：用來建立複雜不透明度遮罩的圖形、 影像和漸層的模式。  
  
     下圖顯示<xref:System.Windows.Media.DrawingBrush>作為不透明度遮罩。  
  
     ![具有 DrawingBrush 不透明度遮罩的物件](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
DrawingBrush 不透明度遮罩範例  
  
 漸層筆刷 (<xref:System.Windows.Media.LinearGradientBrush>和<xref:System.Windows.Media.RadialGradientBrush>) 是特別適用於作為不透明度遮罩。 因為<xref:System.Windows.Media.SolidColorBrush>填滿的區域，以統一的色彩，使不佳的不透明度遮罩; 使用<xref:System.Windows.Media.SolidColorBrush>相當於設定元素或視覺效果的<xref:System.Windows.UIElement.OpacityMask%2A>屬性。  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>使用漸層作為不透明度遮罩  
 若要建立漸層填滿，您必須指定兩個或多個漸層停駐點。 每個漸層停駐點都包含色彩和位置的描述 (如需建立及使用漸層的詳細資訊，請參閱[使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md))。 使用漸層作為不透明度遮罩的程序也相同，不同之處在於，不透明度遮罩漸層是以 Alpha 色板進行混色，而不是以色彩。 所以漸層內容的實際色彩並不重要，重要的是每個色彩的 Alpha 色板 (或稱不透明度)。 下列為範例。  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>指定不透明度遮罩的漸層停駐點  
 在上一個範例中，系統定義的色彩<xref:System.Windows.Media.Colors.Black%2A>做為漸層開始色彩。 因為所有色彩<xref:System.Windows.Media.Colors>類別，除了<xref:System.Windows.Media.Colors.Transparent%2A>，是完全不透明，它們可以用來直接定義漸層停駐的不透明度遮罩的起始色彩。  
  
 其他控制時定義為不透明遮罩的 alpha 值的詳細資訊，您可以指定使用的色彩的 alpha 色板[!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)]標記，或使用十六進位標記法<xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType>方法。  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>在 "XAML" 中指定色彩不透明度  
 在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，您會使用 [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] 十六進位標記法來指定個別色彩的不透明度。 [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] 十六進位標記法使用下列語法：  
  
 `#` **aa** *rrggbb*  
  
 上一行中的 *aa* 代表用來指定色彩不透明度的兩位數十六進位值。 *rr*、*gg* 和 *bb* 分別代表用來指定色彩中紅色、綠色及藍色量的兩位數十六進位值。 每個十六進位位數的值可以是 0-9 或 A-F。 0 是最小的值，F 是最大的值。 Alpha 值為 00 時會指定完全透明的色彩，而 Alpha 值為 FF 時則會建立完全不透明的色彩。  在下列範例中，會使用十六進位 [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] 標記法指定兩個色彩。 第一個是完全不透明，而第二個是完全透明。  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>使用影像作為不透明度遮罩  
 影像也可用來作為不透明度遮罩。 下列影像顯示一個範例。 會使用棋盤背景來表示遮罩的透明部分。  
  
 ![具有 ImageBrush 不透明度遮罩的物件](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
不透明度遮罩範例  
  
 若要使用的影像作為不透明度遮罩，使用<xref:System.Windows.Media.ImageBrush>來包含該影像。 在建立作為不透明度遮罩使用的影像時，請將影像儲存為支援多透明度層級的格式，例如 [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]。 下列範例顯示用來建立上述圖例的程式碼。  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>使用並排影像作為不透明度遮罩  
 會在下列範例中，與另一個使用相同的映像<xref:System.Windows.Media.ImageBrush>，但用來產生的映像 50 平方像素的並排顯示筆刷的並排顯示功能。  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>從繪圖建立不透明度遮罩  
 繪圖可以用於建立不透明度遮罩。 繪圖本身包含的圖形也能以漸層、純色、影像或甚至其他繪圖來填滿。 下列影像為使用繪圖作為不透明度遮罩的範例。 會使用棋盤背景來表示遮罩的透明部分。  
  
 ![具有 DrawingBrush 不透明度遮罩的物件](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
DrawingBrush 不透明度遮罩範例  
  
 若要使用繪圖作為不透明度遮罩，<xref:System.Windows.Media.DrawingBrush>來包含該繪圖。 下列範例顯示用來建立上述圖例的程式碼：  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>使用並排繪圖作為不透明度遮罩  
 像是<xref:System.Windows.Media.ImageBrush>，則<xref:System.Windows.Media.DrawingBrush>可並排顯示其繪圖。 在下列範例中，會使用繪圖筆刷來建立並排不透明度遮罩。  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>另請參閱

- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
