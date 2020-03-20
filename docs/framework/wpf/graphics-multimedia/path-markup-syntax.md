---
title: 路徑標記語法
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: adcedcea6c8d6d988021cbbccf87bd25a042fd16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181853"
---
# <a name="path-markup-syntax"></a>路徑標記語法
路徑在[WPF 概述和幾何概述中討論形狀和基本圖形](shapes-and-basic-drawing-in-wpf-overview.md)，但是，本主題詳細介紹了可以使用 更緊湊地指定路徑幾何體的強大而複雜的微型語言。 [Geometry Overview](geometry-overview.md) [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 要理解本主題，應熟悉<xref:System.Windows.Media.Geometry>物件的基本特徵。 有關詳細資訊，請參閱[幾何概述](geometry-overview.md)。  
  
<a name="abouthisdocument"></a>
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry 和 PathFigureCollection 迷你語言  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供了兩個類，提供用於描述幾何路徑的微型語言<xref:System.Windows.Media.StreamGeometry>：<xref:System.Windows.Media.PathFigureCollection>和 。  
  
- 設置類型屬性<xref:System.Windows.Media.StreamGeometry><xref:System.Windows.Media.Geometry>（如<xref:System.Windows.UIElement.Clip%2A><xref:System.Windows.UIElement><xref:System.Windows.Shapes.Path.Data%2A><xref:System.Windows.Shapes.Path>元素的屬性或元素的屬性）時，可以使用 mini 語言。 下面的示例使用屬性語法創建 。 <xref:System.Windows.Media.StreamGeometry>  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
- 設置<xref:System.Windows.Media.PathFigureCollection><xref:System.Windows.Media.PathGeometry.Figures%2A>的屬性時，可以使用 迷你語言<xref:System.Windows.Media.PathGeometry>。 下面的示例使用屬性語法為 創建 。 <xref:System.Windows.Media.PathFigureCollection> <xref:System.Windows.Media.PathGeometry>  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 在上述範例中，您可以發現這兩個迷你語言非常相似。 <xref:System.Windows.Media.PathGeometry>在可以使用<xref:System.Windows.Media.StreamGeometry>的 和那你應該用哪一個？ <xref:System.Windows.Media.StreamGeometry>創建路徑後不需要修改路徑時，請使用如果需要修改<xref:System.Windows.Media.PathGeometry>路徑，請使用 。  
  
 有關和<xref:System.Windows.Media.PathGeometry><xref:System.Windows.Media.StreamGeometry>物件之間的差異的詳細資訊，請參閱[幾何概述](geometry-overview.md)。  
  
### <a name="a-note-about-white-space"></a>關於空白字元  
 為了簡潔起見，會在後續的語法區段中會顯示單一空格，但是在顯示單一空格的位置也接受多個空格。  
  
 兩個數字實際上不必用逗號或空格分隔，但只有在生成的字串是明確的時才能這樣做。 例如，`2..3`實際上是兩個數字："2"。 和 ".3"。 同樣，`2-3`是"2"和"-3"。 命令之前或之後也一樣不需要空格。  
  
### <a name="syntax"></a>語法  
 屬性[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]使用語法<xref:System.Windows.Media.StreamGeometry>由可選<xref:System.Windows.Media.FillRule>值和一個或多個圖形描述組成。  
  
|StreamGeometry XAML 屬性使用方式|  
|-----------------------------------------|  
|`<`*物件**屬性*`="` `fillRule`[ `figureDescription` `figureDescription`] |`" ... />`|  
  
 屬性[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]使用語法<xref:System.Windows.Media.PathFigureCollection>由一個或多個圖形描述組成。  
  
|PathFigureCollection XAML 屬性使用方式|  
|-----------------------------------------------|  
|`<`*物件**property*`="`屬性`figureDescription` `figureDescription`[ ]`" ... />`|  
  
|詞彙|描述|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> 指定 是否<xref:System.Windows.Media.StreamGeometry>使用<xref:System.Windows.Media.FillRule.EvenOdd>。 <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A><br /><br /> -   `F0`指定<xref:System.Windows.Media.FillRule.EvenOdd>填充規則。<br />-   `F1`指定<xref:System.Windows.Media.FillRule.Nonzero>填充規則。<br /><br /> 如果省略此命令，子路徑將使用預設行為，即<xref:System.Windows.Media.FillRule.EvenOdd>。 如果您指定此命令，您必須先放置它。|  
|*figureDescription*|由移動命令、繪製命令以及選擇性的關閉命令所組成的圖表。<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|指定圖表起點的移動命令。 請參閱[移動命令](#themovecommand)部分。|  
|*drawCommands*|說明圖表內容的一或多個繪製命令。 請參閱["繪製命令"](#drawcommands)部分。|  
|*closeCommand*|關閉圖表的選擇性關閉命令。 請參閱[關閉命令](#closecommand)部分。|  
  
<a name="themovecommand"></a>
## <a name="move-command"></a>移動命令  
 指定新圖表的起點。  
  
|語法|  
|------------|  
|`M`*起始點*<br /><br /> - 或 -<br /><br /> `m`*起始點*|  
  
|詞彙|描述|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 新圖表的起點。|  
  
 大寫表示`M``startPoint`為絕對值;大寫大寫表示為絕對值。小寫表示`m`該`startPoint`小寫是與前一個點的偏移量，如果不存在，則 （0，0）。 如果您在移動命令之後列出多個點，則會如您指定線條命令一般，在這些點之間繪製線條。  
  
<a name="drawcommands"></a>
## <a name="draw-commands"></a>繪製命令  
 繪製命令可以由數個圖形命令組成。 有下列圖形命令可使用：線條、水平線、垂直線、三次方貝茲曲線、二次方貝茲曲線、平滑三次方貝茲曲線、平滑二次方貝茲曲線，以及橢圓形弧線。  
  
 透過使用大寫或小寫字母來輸入每個命令：大寫字母表示絕對值，而小寫字母表示相對值：該區段的控制點相對於先前範例的結束點。 當按順序輸入同一類型的多個命令時，可以省略重複的命令條目;例如，可以省略重複的命令條目。例如，`L 100,200 300,400`等效于`L 100,200 L 300,400`。 下表描述了**移動**和**繪製**命令。  
  
### <a name="line-command"></a>線條命令  
 在目前的點和指定的點之間建立直線。 `l 20 30`是`L 20,30`有效**行**命令的示例。  
  
|語法|  
|------------|  
|`L`*端點*<br /><br /> - 或 -<br /><br /> `l`*端點*|  
  
|詞彙|描述|  
|----------|-----------------|  
|*端點*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 行的結束點。|  

大寫表示`L``endPoint`為絕對值;大寫大寫表示為絕對值。小寫表示`l`該`endPoint`小寫是與前一個點的偏移量，如果不存在，則 （0，0）。

### <a name="horizontal-line-command"></a>水平線命令  
 在目前的點和指定的 X 座標之間建立水平線。 `H 90` 為有效水平線命令的範例。

|語法|  
|------------|  
|`H`  *Ⅹ*<br /><br /> - 或 -<br /><br /> `h`  *Ⅹ*|  
  
|詞彙|描述|  
|----------|-----------------|  
|*Ⅹ*|<xref:System.Double?displayProperty=nameWithType><br /><br /> 線條結束點的 X 座標。|  
  
大寫表示`H``x`為絕對值;大寫大寫表示為絕對值。小寫表示`h`該`x`小寫是與前一個點的偏移量，如果不存在，則 （0，0）。
  
### <a name="vertical-line-command"></a>垂直線命令  
 在目前的點和指定的 Y 座標之間建立垂直線。 `v 90` 為有效垂直線命令的範例。

|語法|  
|------------|  
|`V`  *Y*<br /><br /> - 或 -<br /><br /> `v`  *Y*|  
  
|詞彙|描述|  
|----------|-----------------|  
|*Y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> 線條結束點的 Y 座標。|  

大寫表示`V``y`為絕對值;大寫大寫表示為絕對值。小寫表示`v`該`y`小寫是與前一個點的偏移量，如果不存在，則 （0，0）。  

### <a name="cubic-bezier-curve-command"></a>三次方貝茲曲線命令  
 使用兩個指定的控制點（1`controlPoint`和`controlPoint`2）在當前點和指定端點之間創建立方貝茲曲線。 `C 100,200 200,400 300,200` 為有效曲線命令的範例。  
  
|語法|  
|------------|  
|`C``controlPoint`1`controlPoint`2`endPoint`<br /><br /> - 或 -<br /><br /> `c``controlPoint`1`controlPoint`2`endPoint`|  
  
|詞彙|描述|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線的第一個控制點，它能決定曲線的起始正切函數。|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線的第二個控制點，它能決定曲線的結束正切函數。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線要繪製到的點。|  
  
### <a name="quadratic-bezier-curve-command"></a>二次方貝茲曲線命令  
 使用指定的控制點 （）`controlPoint`在當前點和指定端點之間創建二次方貝茲曲線。 `q 100,200 300,200` 為有效二次方貝茲曲線命令的範例。  
  
|語法|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - 或 -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|詞彙|描述|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線的控制點，它能決定曲線的起始正切函數和結束正切函數。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線要繪製到的點。|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>平滑三次方貝茲曲線命令  
 在目前的點和指定的結束點之間建立三次方貝茲曲線。 第一個控制點會假設為 (相對於目前的點) 上一個命令之第二個控制點的反映。 如果沒有上一個命令，或者上一個命令不是三次方貝茲曲線命令或平滑三次方貝茲曲線命令，則會假設第一個控制點和目前的點一致。 第二個控制點（曲線末端的控制點）由`controlPoint`2 指定。 例如，`S 100,200 200,300`是一個有效的平滑立方貝茲曲線命令。  
  
|語法|  
|------------|  
|`S``controlPoint`2`endPoint`<br /><br /> - 或 -<br /><br /> `s``controlPoint`2`endPoint`|  
  
|詞彙|描述|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線的控制點，它能決定曲線的結束正切函數。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線要繪製到的點。|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>平滑二次方貝茲曲線命令  
 在目前的點和指定的結束點之間建立二次方貝茲曲線。 控制點會假設為 (相對於目前的點) 上一個命令之控制點的反映。 如果沒有上一個命令，或者上一個命令不是二次方貝茲曲線命令或平滑二次方貝茲曲線命令，則控制點和目前的點一致。  
  
|語法|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - 或 -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|詞彙|描述|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線的控制點，它能決定曲線的起始正切函數。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲線要繪製到的點。|  
  
### <a name="elliptical-arc-command"></a>橢圓形弧線命令  
 在目前的點和指定的結束點之間建立橢圓形弧線。  
  
|語法|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - 或 -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|詞彙|描述|  
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
|`Z`<br /><br /> - 或 -<br /><br /> `z`|  

<a name="pointsyntax"></a>
## <a name="point-syntax"></a>點語法  
 描述 （0，0） 是左上角的點的 x 和 y 座標。
  
|語法|  
|------------|  
|`x` `,` `y`<br /><br /> - 或 -<br /><br /> `x` `y`|  
  
|詞彙|描述|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 點的 X 座標。|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 點的 Y 座標。|  
  
<a name="specialvalues"></a>
## <a name="special-values"></a>特殊值  
 除了標準數值，您也可以使用下列特殊值。 這些值會區分大小寫。  
  
 Infinity  
 表示<xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.  
  
 -Infinity  
 表示<xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.  
  
 NaN  
 表示<xref:System.Double.NaN?displayProperty=nameWithType>.  
  
 您也可以使用科學記號標記法。 例如，`+1.e17` 是有效的值。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.PathFigureCollection>
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
- [幾何概觀](geometry-overview.md)
- [如何使用主題](geometries-how-to-topics.md)
