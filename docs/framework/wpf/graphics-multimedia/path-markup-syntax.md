---
title: "路徑標記語法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f2b04dfa51f578ba80e2b766f455719afbb86b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="path-markup-syntax"></a>路徑標記語法
路徑中會討論[圖案和基本繪圖概觀 WPF 中](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)和[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)，不過，本主題說明的詳細資料指定路徑，您可以使用功能強大且複雜的迷你語言使用更簡潔的幾何[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該熟悉基本功能的<xref:System.Windows.Media.Geometry>物件。 如需詳細資訊，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry 和 PathFigureCollection 迷你語言  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供兩種類別可描述幾何路徑提供迷你語言：<xref:System.Windows.Media.StreamGeometry>和<xref:System.Windows.Media.PathFigureCollection>。  
  
-   您使用<xref:System.Windows.Media.StreamGeometry>迷你設定類型的屬性時的語言<xref:System.Windows.Media.Geometry>，例如<xref:System.Windows.UIElement.Clip%2A>屬性<xref:System.Windows.UIElement>或<xref:System.Windows.Shapes.Path.Data%2A>屬性<xref:System.Windows.Shapes.Path>項目。 下列範例會使用屬性語法建立<xref:System.Windows.Media.StreamGeometry>。  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   您使用<xref:System.Windows.Media.PathFigureCollection>迷你語言設定時<xref:System.Windows.Media.PathGeometry.Figures%2A>屬性<xref:System.Windows.Media.PathGeometry>。 下列範例會使用屬性語法建立<xref:System.Windows.Media.PathFigureCollection>如<xref:System.Windows.Media.PathGeometry>。  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 在上述範例中，您可以發現這兩個迷你語言非常相似。 就一定能夠使用<xref:System.Windows.Media.PathGeometry>在任何情況下，您無法使用<xref:System.Windows.Media.StreamGeometry>; 因此您應該使用哪一項？ 使用<xref:System.Windows.Media.StreamGeometry>時建立; 後修改的路徑，您不需要使用<xref:System.Windows.Media.PathGeometry>如果您需要修改路徑。  
  
 如需有關差異<xref:System.Windows.Media.PathGeometry>和<xref:System.Windows.Media.StreamGeometry>物件，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
### <a name="a-note-about-white-space"></a>關於空白字元  
 為了簡潔起見，會在後續的語法區段中會顯示單一空格，但是在顯示單一空格的位置也接受多個空格。  
  
 兩個數字不一定要以逗號或空格分隔，但是這只適用於產生的字串為明確字串的情況。 比方說，`2..3`是兩個數字:"2"。 和 ".3"。 同樣地，`2-3`是"2"和"-3"。 命令之前或之後也一樣不需要空格。  
  
### <a name="syntax"></a>語法  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]屬性使用方式語法<xref:System.Windows.Media.StreamGeometry>是由選擇性<xref:System.Windows.Media.FillRule>值和一或多個圖描述。  
  
|StreamGeometry XAML 屬性使用方式|  
|-----------------------------------------|  
|`<`*物件**屬性* `="`[ `fillRule`] `figureDescription`[ `figureDescription`] *`" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]屬性使用方式語法<xref:System.Windows.Media.PathFigureCollection>是一或多個圖說明所組成。  
  
|PathFigureCollection XAML 屬性使用方式|  
|-----------------------------------------------|  
|`<`*物件**屬性* `="` `figureDescription`[ `figureDescription`] *`" ... />`|  
  
|詞彙|描述|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> 指定是否<xref:System.Windows.Media.StreamGeometry>使用<xref:System.Windows.Media.FillRule.EvenOdd>或<xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A>。<br /><br /> -   `F0`指定<xref:System.Windows.Media.FillRule.EvenOdd>填滿規則。<br />-   `F1`指定<xref:System.Windows.Media.FillRule.Nonzero>填滿規則。<br /><br /> 如果您省略此命令時，子路徑會使用預設行為，也就是<xref:System.Windows.Media.FillRule.EvenOdd>。 如果您指定此命令，您必須先放置它。|  
|*figureDescription*|由移動命令、繪製命令以及選擇性的關閉命令所組成的圖表。<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|指定圖表起點的移動命令。 請參閱[移動命令](#themovecommand)> 一節。|  
|*drawCommands*|說明圖表內容的一或多個繪製命令。 請參閱[繪製命令](#drawcommands)> 一節。|  
|*closeCommand*|關閉圖表的選擇性關閉命令。 請參閱[Close 命令](#closecommand)> 一節。|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a>移動命令  
 指定新圖表的起點。  
  
|語法|  
|------------|  
|`M` *startPoint*<br /><br /> -或-<br /><br /> `m` *startPoint*|  
  
|詞彙|說明|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 新圖表的起點。|  
  
 以大寫`M`表示`startPoint`絕對值; 小寫`m`表示`startPoint`位移至上一個點，或 (0，0) 如果不存在。 如果您在移動命令之後列出多個點，則會如您指定線條命令一般，在這些點之間繪製線條。  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a>繪製命令  
 繪製命令可以由數個圖形命令組成。 有下列圖形命令可使用：線條、水平線、垂直線、三次方貝茲曲線、二次方貝茲曲線、平滑三次方貝茲曲線、平滑二次方貝茲曲線，以及橢圓形弧線。  
  
 透過使用大寫或小寫字母來輸入每個命令：大寫字母表示絕對值，而小寫字母表示相對值：該區段的控制點相對於先前範例的結束點。 依序輸入時的相同類型的多個命令，您可以省略的重複項目;例如，`L 100,200 300,400`相當於`L 100,200 L 300,400`。 下表描述**移動**和**繪製**命令。  
  
### <a name="line-command"></a>線條命令  
 在目前的點和指定的點之間建立直線。 `l 20 30`和`L 20,30`是有效的範例**列**命令。  
  
|語法|  
|------------|  
|`L` *endPoint*<br /><br /> -或-<br /><br /> `l` *endPoint*|  
  
|詞彙|描述|  
|----------|-----------------|  
|*endPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 行的結束點。|  

以大寫`L`表示`endPoint`絕對值; 小寫`l`表示`endPoint`位移至上一個點，或 (0，0) 如果不存在。

### <a name="horizontal-line-command"></a>水平線命令  
 在目前的點和指定的 X 座標之間建立水平線。 `H 90` 為有效水平線命令的範例。

  
|語法|  
|------------|  
|`H`  *x*<br /><br /> -或-<br /><br /> `h`  *x*|  
  
|詞彙|描述|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> 線條結束點的 X 座標。|  
  
以大寫`H`表示`x`絕對值; 小寫`h`表示`x`位移至上一個點，或 (0，0) 如果不存在。
  
### <a name="vertical-line-command"></a>垂直線命令  
 在目前的點和指定的 Y 座標之間建立垂直線。 `v 90` 為有效垂直線命令的範例。

  
|語法|  
|------------|  
|`V`  *y*<br /><br /> -或-<br /><br /> `v`  *y*|  
  
|詞彙|描述|  
|----------|-----------------|  
|*y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> 線條結束點的 Y 座標。|  

以大寫`V`表示`y`絕對值; 小寫`v`表示`y`位移至上一個點，或 (0，0) 如果不存在。  
    
### <a name="cubic-bezier-curve-command"></a>三次方貝茲曲線命令  
 使用兩個指定的控制點，建立在目前點和指定的結束點之間的三次方貝茲曲線 (`controlPoint`1 和`controlPoint`2)。 `C 100,200 200,400 300,200` 為有效曲線命令的範例。  
  
|語法|  
|------------|  
|`C` `controlPoint`1`controlPoint`2`endPoint`<br /><br /> -或-<br /><br /> `c` `controlPoint`1`controlPoint`2`endPoint`|  
  
|詞彙|描述|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線的第一個控制點，它能決定曲線的起始正切函數。|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線的第二個控制點，它能決定曲線的結束正切函數。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線要繪製到的點。|  
  
### <a name="quadratic-bezier-curve-command"></a>二次方貝茲曲線命令  
 使用指定的控制點，建立在目前點和指定的結束點之間的二次方貝茲曲線 (`controlPoint`)。 `q 100,200 300,200` 為有效二次方貝茲曲線命令的範例。  
  
|語法|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> -或-<br /><br /> `q` `controlPoint` `endPoint`|  
  
|詞彙|說明|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線的控制點，它能決定曲線的起始正切函數和結束正切函數。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線要繪製到的點。|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>平滑三次方貝茲曲線命令  
 在目前的點和指定的結束點之間建立三次方貝茲曲線。 第一個控制點會假設為 (相對於目前的點) 上一個命令之第二個控制點的反映。 如果沒有上一個命令，或者上一個命令不是三次方貝茲曲線命令或平滑三次方貝茲曲線命令，則會假設第一個控制點和目前的點一致。 第二個控制點，控制項的曲線，結尾所指定的點`controlPoint`2。 例如，`S 100,200 200,300`是有效 smooth 三次方貝茲曲線的命令。  
  
|語法|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> -或-<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|詞彙|描述|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線的控制點，它能決定曲線的結束正切函數。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線要繪製到的點。|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>平滑二次方貝茲曲線命令  
 在目前的點和指定的結束點之間建立二次方貝茲曲線。 控制點會假設為 (相對於目前的點) 上一個命令之控制點的反映。 如果沒有上一個命令，或者上一個命令不是二次方貝茲曲線命令或平滑二次方貝茲曲線命令，則控制點和目前的點一致。  
  
|語法|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> -或-<br /><br /> `t` `controlPoint` `endPoint`|  
  
|詞彙|說明|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線的控制點，它能決定曲線的起始正切函數。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線要繪製到的點。|  
  
### <a name="elliptical-arc-command"></a>橢圓形弧線命令  
 在目前的點和指定的結束點之間建立橢圓形弧線。  
  
|語法|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> -或-<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|詞彙|說明|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> 弧線的半徑 X 和 Y。|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 橢圓形的旋轉 (以角度為單位)。|  
|`isLargeArcFlag`|如果弧線的角度應該為 180 度或大於 180 度，則設定為 1；否則，請設定為 0。|  
|`sweepDirectionFlag`|如果弧線是以正值角度的方向繪製，則設定為 1；否則，請設定為 0。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 弧線要繪製到的點。|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a>關閉命令  
 結束目前的圖表，並建立連接目前的點和圖表起點的線條。 此命令會在圖表的最後一個區段和第一個區段之間建立線條聯結 (邊角)。  
  
|語法|  
|------------|  
|`Z`<br /><br /> -或-<br /><br /> `z`|  

<a name="pointsyntax"></a>   
## <a name="point-syntax"></a>點語法  
 描述 x 和 y 座標點的位置 (0，0) 是左上的角。
  
|語法|  
|------------|  
|`x` `,` `y`<br /><br /> -或-<br /><br /> `x` `y`|  
  
|詞彙|說明|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 點的 X 座標。|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 點的 Y 座標。|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a>特殊值  
 除了標準數值，您也可以使用下列特殊值。 這些值會區分大小寫。  
  
 Infinity  
 代表<xref:System.Double.PositiveInfinity?displayProperty=nameWithType>。  
  
 -Infinity  
 代表<xref:System.Double.NegativeInfinity?displayProperty=nameWithType>。  
  
 NaN  
 代表<xref:System.Double.NaN?displayProperty=nameWithType>。  
  
 您也可以使用科學記號標記法。 例如，`+1.e17`是有效的值。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.PathFigureCollection>  
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)
