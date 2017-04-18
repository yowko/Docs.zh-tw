---
title: "路徑標記語法 | Microsoft Docs"
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
  - "PathGeometry 類別"
  - "XAML 的屬性使用方式"
  - "XAML 屬性使用方式"
  - "PathGeometry 類別"
  - "PathGeometry 類別的圖形"
  - "XAML 物件項目用法"
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# 路徑標記語法
路徑中會討論[圖案和基本繪圖概觀 WPF 中](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)和[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)，不過，本主題詳細說明您可用來指定路徑幾何更簡潔地使用功能強大且複雜的迷你語言[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
 此主題包括下列各節。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該熟悉基本功能的<xref:System.Windows.Media.Geometry>物件。 如需詳細資訊，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry 和 PathFigureCollection 迷你語言  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供兩個類別，可描述幾何路徑時，提供迷你語言︰ <xref:System.Windows.Media.StreamGeometry>和<xref:System.Windows.Media.PathFigureCollection>。  
  
-   您使用<xref:System.Windows.Media.StreamGeometry>迷你語言設定屬性的型別時<xref:System.Windows.Media.Geometry>，例如<xref:System.Windows.UIElement.Clip%2A>屬性<xref:System.Windows.UIElement>或<xref:System.Windows.Shapes.Path.Data%2A>屬性<xref:System.Windows.Shapes.Path>項目。 下列範例會使用屬性語法來建立<xref:System.Windows.Media.StreamGeometry>。  
  
     [!code-xml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   您使用<xref:System.Windows.Media.PathFigureCollection>迷你語言設定時<xref:System.Windows.Media.PathGeometry.Figures%2A>屬性<xref:System.Windows.Media.PathGeometry>。 下列範例會使用屬性語法來建立<xref:System.Windows.Media.PathFigureCollection>的<xref:System.Windows.Media.PathGeometry>。  
  
     [!code-xml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 您可以看到上述範例中，兩個迷你語言都很相似。 我們仍然可以使用<xref:System.Windows.Media.PathGeometry>在任何情況下，您可以使用<xref:System.Windows.Media.StreamGeometry>; 因此您應該使用哪一個？ 使用<xref:System.Windows.Media.StreamGeometry>時建立; 之後可以修改該路徑時，您不需要使用<xref:System.Windows.Media.PathGeometry>如果您需要修改的路徑。  
  
 如需有關之間的差異<xref:System.Windows.Media.PathGeometry>和<xref:System.Windows.Media.StreamGeometry>物件，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
### <a name="a-note-about-white-space"></a>泛空白字元相關附註  
 為了簡潔起見，語法 」 一節，顯示一個空格，但是只要單一空格，還有可接受多個空格。  
  
 兩個數字不一定要分隔逗號或空格，但這只能進行時產生的字串模稜兩可。 比方說，`2..3`是兩個數字: 「&2; 」。 和 「。&3; 」。 同樣地，`2-3`是"2"和"-3"。 空白是不必要之前或之後的命令，或是。  
  
### <a name="syntax"></a>語法  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]屬性使用方式語法<xref:System.Windows.Media.StreamGeometry>是由選擇性<xref:System.Windows.Media.FillRule>值和一或多個圖描述。  
  
|StreamGeometry XAML 屬性使用方式|  
|-----------------------------------------|  
|`<`*object* *property* `="`[                                         `fillRule`]                                          `figureDescription`[                                         `figureDescription`]*`" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]屬性使用方式語法<xref:System.Windows.Media.PathFigureCollection>是由一或多個圖描述。  
  
|PathFigureCollection XAML 屬性使用方式|  
|-----------------------------------------------|  
|`<`*object* *property* `="` `figureDescription`[                                         `figureDescription`]*`" ... />`|  
  
|詞彙|說明|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=fullName><br /><br /> 指定是否<xref:System.Windows.Media.StreamGeometry>使用<xref:System.Windows.Media.FillRule>或<xref:System.Windows.Media.FillRule><xref:System.Windows.Media.PathGeometry.FillRule%2A>。<br /><br /> -   `F0`指定<xref:System.Windows.Media.FillRule>填滿規則。<br />-   `F1`指定<xref:System.Windows.Media.FillRule>填滿規則。<br /><br /> 如果您省略此命令時，子路徑會使用預設的行為，也就是<xref:System.Windows.Media.FillRule>。 如果您指定此命令時，您必須先放置。|  
|*figureDescription*|組成移動命令、 圖繪製命令，以及選擇性的關閉命令。<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|移動命令，指定圖形的開始點。 請參閱[移動命令](#themovecommand)一節。|  
|*drawCommands*|一或多個繪製命令的說明圖中的內容。 請參閱[繪製命令](#drawcommands)一節。|  
|*closeCommand*|選擇性的關閉命令來關閉圖。 請參閱[關閉命令](#closecommand)一節。|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a>移動命令  
 指定新圖形的起始點。  
  
|語法|  
|------------|  
|`M`*圓弧*<br /><br /> -或-<br /><br /> `m`*圓弧*|  
  
|詞彙|說明|  
|----------|-----------------|  
|*圓弧*|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 新圖形的開始點。|  
  
 以大寫`M`表示`startPoint`是絕對值，小寫`m`表示`startPoint`位移至先前的點，或 (0，0) 如果不存在。 如果您在移動命令之後列出多個點，但指定線條命令繪製線條到這些點。  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a>繪製命令  
 繪製命令可以包含數個圖案命令。 圖形使用下列命令︰ 列、 水平、 垂直線條、 三次方貝茲曲線、 二次方貝茲曲線、 平滑三次方貝茲曲線、 平滑二次方貝茲曲線和橢圓弧形。  
  
 您可以使用大寫或小寫字母輸入每個命令︰ 大寫字母表示絕對值，小寫字母表示相對值︰ 該區段的控點是相對於先前範例的結束點。 依序輸入時的相同類型的多個命令，您可以省略的重複項目;例如，`L 100,200 300,400`相當於`L 100,200 L 300,400`。 下表描述**移動**和**繪製**命令。  
  
### <a name="line-command"></a>命令列  
 建立目前點和指定的結束點之間的直線。                           `l 20 30`和`L 20,30`是有效的範例**列**命令。  
  
|語法|  
|------------|  
|`L`*端點*<br /><br /> -或-<br /><br /> `l`*端點*|  
  
|詞彙|說明|  
|----------|-----------------|  
|*端點*|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 行的結束點。|  
  
### <a name="horizontal-line-command"></a>水平列命令  
 建立目前點和指定的 x 座標之間的水平列。                          `H 90`是有效的水平列命令的範例。  
  
|語法|  
|------------|  
|`H`  *x*<br /><br /> -或-<br /><br /> `h`  *x*|  
  
|詞彙|說明|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=fullName><br /><br /> 線條的終點 x 座標。|  
  
### <a name="vertical-line-command"></a>垂直線命令  
 建立一條垂直線之間目前點和指定的 y 座標。                          `v 90`是有效的垂直列命令的範例。  
  
|語法|  
|------------|  
|`V`  *y*<br /><br /> -或-<br /><br /> `v`  *y*|  
  
|詞彙|描述|  
|----------|-----------------|  
|*y*|<xref:System.Double?displayProperty=fullName><br /><br /> 線條終點的 y 座標。|  
  
### <a name="cubic-bezier-curve-command"></a>三次方貝茲曲線命令  
 會使用兩個指定的控制點建立在目前點和指定的結束點之間的三次方貝茲曲線 ( `controlPoint`1 和`controlPoint`2)。                          `C 100,200 200,400 300,200`是有效的曲線命令的範例。  
  
|語法|  
|------------|  
|`C` `controlPoint`1`controlPoint`2`endPoint`<br /><br /> -或-<br /><br /> `c` `controlPoint`1`controlPoint`2`endPoint`|  
  
|詞彙|描述|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 第一個控制點的曲線，決定曲線的起始正切函數。|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 第二個控制點的曲線，決定曲線的結束的正切函數。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 曲線要繪製到的點。|  
  
### <a name="quadratic-bezier-curve-command"></a>二次方貝茲曲線命令  
 使用指定的控制項控點會建立在目前點和指定的結束點之間的二次方貝茲曲線 ( `controlPoint`)。                          `q 100,200 300,200`是有效的二次方貝茲曲線命令的範例。  
  
|語法|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> -或-<br /><br /> `q` `controlPoint` `endPoint`|  
  
|詞彙|說明|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 開始和結束的曲線的正切函數會決定曲線的控制點。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 曲線要繪製到的點。|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>平滑三次方貝茲曲線命令  
 建立目前點和指定的結束點之間的三次方貝茲曲線。 第一個控制點假設前一個命令在目前點的第二個控制點的反映。 如果沒有上一個命令，或前一個命令不是三次方貝茲曲線命令或平滑三次方貝茲曲線命令，假設第一個控制點是同一與目前的點。 第二個控制點，曲線，結尾的控制項控點由指定`controlPoint`2。 例如，`S 100,200 200,300`是有效平滑三次方貝茲曲線的命令。  
  
|語法|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> -或-<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|詞彙|說明|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 曲線，決定曲線的結束的正切函數的控制項控點。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 曲線要繪製到的點。|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>平滑二次方貝茲曲線命令  
 建立目前點和指定的結束點之間的二次方貝茲曲線。 控制項控點被假設為前一個命令在目前點的控制點的反映。 如果沒有上一個命令，或前一個命令不是二次方貝茲曲線命令或平滑二次方貝茲曲線命令，控制項控點是同一與目前的點。  
  
|語法|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> -或-<br /><br /> `t` `controlPoint` `endPoint`|  
  
|詞彙|描述|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 開始和曲線的正切函數會決定曲線的控制點。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 曲線要繪製到的點。|  
  
### <a name="elliptical-arc-command"></a>橢圓弧形命令  
 建立在目前點和指定的結束點之間的橢圓弧形。  
  
|語法|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> -或-<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|詞彙|描述|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=fullName><br /><br /> 弧線的半徑 X 和 Y。|  
|`rotationAngle`|<xref:System.Double?displayProperty=fullName><br /><br /> 橢圓形，以度為單位的旋轉角度。|  
|`isLargeArcFlag`|如果弧形的角度，應該是 180 度設定為 1 或更高。否則，設定為 0。|  
|`sweepDirectionFlag`|繪製弧形的角度為正值方向; 如果設為 1否則，設定為 0。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> 弧線要繪製到的點。|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a>關閉命令  
 結束目前的圖表，並建立一條線連接目前點的圖中的開始點。 此命令會建立線條會合 （角） 的最後一個區段與此圖中的第一個區段之間。  
  
|語法|  
|------------|  
|`Z`<br /><br /> -或-<br /><br /> `z`|  
  
<a name="pointsyntax"></a>   
## <a name="point-syntax"></a>點的語法  
 描述點 x 和 y 座標。  
  
|語法|  
|------------|  
|`x` `,` `y`<br /><br /> -或-<br /><br /> `x` `y`|  
  
|詞彙|說明|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=fullName><br /><br /> 點的 x 座標。|  
|`y`|<xref:System.Double?displayProperty=fullName><br /><br /> 點的 y 座標。|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a>特殊值  
 而不是標準的數值，您也可以使用下列特殊值。 這些值會區分大小寫。  
  
 Infinity  
 代表<xref:System.Double.PositiveInfinity?displayProperty=fullName>。  
  
 -Infinity  
 代表<xref:System.Double.NegativeInfinity?displayProperty=fullName>。  
  
 NaN  
 代表<xref:System.Double.NaN?displayProperty=fullName>。  
  
 您也可以使用科學記號標記法。 例如，`+1.e17`是有效的值。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Shapes.Path>   
 <xref:System.Windows.Media.StreamGeometry>   
 <xref:System.Windows.Media.PathGeometry>   
 <xref:System.Windows.Media.PathFigureCollection>   
 [圖案和基本繪圖中 WPF 概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [How to 主題](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)