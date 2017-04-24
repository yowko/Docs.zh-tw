---
title: "使用純色和漸層繪製的概觀 | Microsoft Docs"
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
  - "筆刷, 使用漸層繪製"
  - "筆刷, 使用純色繪製"
  - "漸層, 繪製方式"
  - "使用漸層繪製"
  - "使用純色繪製"
  - "純色, 繪製方式"
ms.assetid: f5b182f3-c5c7-4cbe-9f2f-65e690d08255
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 使用純色和漸層繪製的概觀
本主題說明如何使用 <xref:System.Windows.Media.SolidColorBrush>、<xref:System.Windows.Media.LinearGradientBrush> 及 <xref:System.Windows.Media.RadialGradientBrush> 物件以純色、線形漸層及放射狀漸層繪製。  
  
   
  
<a name="solidcolor"></a>   
## 使用純色繪製區域  
 不論在什麼平台，最常見的作業之一就是使用純 <xref:System.Windows.Media.Color> 繪製區域。  為了完成這個工作，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 會提供 <xref:System.Windows.Media.SolidColorBrush> 類別 \(Class\)。  下列各節會說明使用 <xref:System.Windows.Media.SolidColorBrush> 繪製的不同方式。  
  
<a name="solidcolorinxaml"></a>   
### 在 "XAML" 中使用 SolidColorBrush  
 若要在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中使用純色繪製區域，請選擇下列其中一個方法。  
  
-   依據名稱選取預先定義的純色筆刷。  例如，您可以將按鈕的 <xref:System.Windows.Controls.Control.Background%2A> 設為 "Red" 或 "MediumBlue"。  如需其他預先定義之純色筆刷的清單，請參閱 <xref:System.Windows.Media.Brushes> 類別的靜態 \(Static\) 屬性。  以下是範例。  
  
     [!code-xml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]  
  
-   選擇 32 位元色板的其中一個色彩，方法是指定單一純色之紅色、綠色及藍色的量來混合成某個色彩。  指定 32 位元色板中的其中一個色彩時，格式為 "*\#rrggbb*"，其中 *rr* 是兩位數字的十六進位數字，指定紅色的相對份量、*gg* 指定綠色的相對份量，而 *bb* 指定藍色的相對份量。  此外，色彩可以指定為 "\#*aarrggbb*"，其中 *aa* 指定色彩的 *Alpha* 值或透明度。  這個方法可以讓您建立部分透明的色彩。  在下列範例中，會使用十六進位標記法將 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.Background%2A> 設為完全不透明的紅色。  
  
     [!code-xml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]  
  
-   使用屬性標記 \(Tag\) 語法來描述 <xref:System.Windows.Media.SolidColorBrush>。  這個語法比較複雜，但是可以讓您指定額外設定，例如筆刷的不透明度。  在下列範例中，兩個 <xref:System.Windows.Controls.Button> 項目的 <xref:System.Windows.Controls.Control.Background%2A> 屬性會設為完全不透明的紅色。  第一個筆刷的色彩是用預先定義的色彩名稱來描述。  第二個筆刷的色彩則是用十六進位標記法來描述。  
  
     [!code-xml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]  
  
<a name="solidcolorsincode"></a>   
### 在程式碼中使用 SolidColorBrush 繪製  
 若要在程式碼中使用純色繪製區域，請選擇下列其中一個方法。  
  
-   使用 <xref:System.Windows.Media.Brushes> 類別提供的其中一個預先定義的筆刷。  在下列範例中，<xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.Background%2A> 設為 <xref:System.Windows.Media.Brushes.Red%2A>。  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]  
  
-   使用 <xref:System.Windows.Media.Color> 結構建立 <xref:System.Windows.Media.SolidColorBrush> 並設定其 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 屬性。  您可以使用 <xref:System.Windows.Media.Colors> 類別中預先定義的色彩，或使用靜態 <xref:System.Windows.Media.Color.FromArgb%2A> 方法建立 <xref:System.Windows.Media.Color>。  
  
     下列範例顯示如何使用預先定義的色彩設定 <xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 屬性。  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]  
  
 靜態 <xref:System.Windows.Media.Color.FromArgb%2A> 可以讓您指定色彩的 [Alpha](GTMT)、紅色、綠色及藍色值。  這些值的範圍通常都是 0\-255。  例如，[Alpha](GTMT) 值為 0 時表示色彩是完全透明的，而值為 255 時表示色彩是完全不透明的。  同樣地，紅色值為 0 時表示色彩中沒有紅色，而值為 255 時表示色彩中具有最大份量的紅色。  在下列範例中，筆刷色彩是由指定 Alpha、紅色、綠色及藍色值加以描述。  
  
 [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]  
  
 如需指定色彩的其他方法，請參閱 <xref:System.Windows.Media.Color> 參考主題。  
  
<a name="gradient"></a>   
## 使用漸層繪製區域  
 漸層筆刷會使用多種色彩繪製區域，這些色彩會沿著某個軸漸漸融合。  您可以使用它們建立光影效果，讓控制項有立體的感覺。  您也可以使用它們來模擬玻璃、金屬、水和其他平滑表面。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供兩種類型的漸層筆刷：<xref:System.Windows.Media.LinearGradientBrush> 和 <xref:System.Windows.Media.RadialGradientBrush>。  
  
<a name="lineargradientbrush"></a>   
## 線形漸層  
 <xref:System.Windows.Media.LinearGradientBrush> 會使用沿著某個線條 \(即「漸層軸」\) 定義的漸層來繪製區域。  您可以使用 <xref:System.Windows.Media.GradientStop> 物件指定漸層的色彩及其在漸層軸上的位置。  您也可以修改漸層軸，以建立水平和垂直漸層以及反轉漸層方向。  漸層軸會在下一節中做說明。  預設會建立對角線的漸層。  
  
 下列範例會顯示程式碼，用以建立由四個色彩組成的線形漸層。  
  
 [!code-xml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 這個程式碼會產生下列漸層。  
  
 ![對角線性漸層](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-diaglgradient-nolabel.png "wcpsdk\_graphicsmm\_diaglgradient\_nolabel")  
  
 **注意**：本主題中的漸層範例會使用預設座標系統設定起始點和結束點。  預設座標系統是相對於週框方塊：0 表示週框方塊的 0%，而 1 表示週框方塊的 100%。  您可以藉由將 <xref:System.Windows.Media.GradientBrush.MappingMode%2A> 屬性設為值 <xref:System.Windows.Media.BrushMappingMode>，變更這個座標系統。  絕對座標系統不會相對於週框方塊。  值會直接在本機空間中解譯。  
  
 <xref:System.Windows.Media.GradientStop> 是漸層筆刷的基本建置組塊 \(Building Block\)。  漸層停駐點會指定漸層軸上位於某個 <xref:System.Windows.Media.GradientStop.Offset%2A> 的 <xref:System.Windows.Media.GradientStop.Color%2A>。  
  
-   漸層停駐點的 <xref:System.Windows.Media.GradientStop.Color%2A> 屬性指定漸層停駐點的色彩。  您可以使用預先定義的色彩 \(由 <xref:System.Windows.Media.Colors> 類別提供\) 或指定 ScRGB 或 ARGB 值來設定色彩。  在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，您也可以使用十六進位標記法來描述色彩。  如需詳細資訊，請參閱 <xref:System.Windows.Media.Color> 結構。  
  
-   漸層停駐點的 <xref:System.Windows.Media.GradientStop.Offset%2A> 屬性指定漸層停駐點色彩在漸層軸上的位置。  位移是 <xref:System.Double> 值，範圍從 0 到 1。  漸層停駐點的位移值越接近 0，色彩就越接近漸層起始點。  漸層的位移值越接近 1，色彩就越接近漸層結束點。  
  
 漸層停駐點之間每個點的色彩是以線性方式插補為兩個相鄰漸層停駐點之色彩的組合。  下圖標出上一個範例中的漸層停駐點。  圓圈表示漸層停駐點的位置，虛線則表示漸層軸。  
  
 ![線性漸層中的漸層停駐點](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk\_graphicsmm\_4gradientstops")  
  
 第一個漸層停駐點指定位移 `0.0` 處的色彩為黃色。  第二個漸層停駐點指定位移 `0.25` 處的色彩為紅色。  沿著漸層軸從左移到右時，這兩個停駐點之間的點會逐漸從黃色變成紅色。  第三個漸層停駐點指定位移 `0.75` 處的色彩為藍色。  第二個和第三個漸層停駐點之間的點會逐漸從紅色變成藍色。  第四個漸層停駐點指定位移 `1.0` 處的色彩為淡黃綠色。  第三個和第四個漸層停駐點之間的點會逐漸從藍色變成淡黃綠色。  
  
<a name="gradientaxis"></a>   
### 漸層軸  
 之前已說明過，線形漸層筆刷的漸層停駐點的位置是沿著線條 \(漸層軸\) 決定。  您可以使用筆刷的 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 屬性變更這個線條的方向和粗細。  藉由管理筆刷的 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>，您可以建立水平和垂直的漸層、反轉漸層方向、縮小漸層範圍等等。  
  
 根據預設，線形漸層筆刷的 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 是相對於要繪製的區域。  \(0,0\) 這個點表示要繪製之區域的左上角，而 \(1,1\) 則表示要繪製之區域的右下角。  <xref:System.Windows.Media.LinearGradientBrush> 的預設 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 為 \(0,0\)，預設 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 為 \(1,1\)，這樣會建立從要繪製之區域的左上角延伸至右下角的對角線漸層。  下圖顯示具有預設 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 之線形漸層筆刷的漸層軸。  
  
 ![對角線性漸層的漸層軸](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk\_graphicsmm\_diagonalgradientaxis")  
  
 下列範例顯示如何藉由指定筆刷的 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 建立水平漸層。  請注意，漸層停駐點與前述範例相同，只有變更 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>，而漸層即從對角線變成水平。  
  
 [!code-xml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 下圖顯示建立的漸層。  漸層軸以虛線標示，漸層停駐點則以圓圈標示。  
  
 ![水平線性漸層的漸層軸](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-horizontalgradient.png "wcpsdk\_graphicsmm\_horizontalgradient")  
  
 下一個範例顯示如何建立垂直漸層。  
  
 [!code-xml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 下圖顯示建立的漸層。  漸層軸以虛線標示，漸層停駐點則以圓圈標示。  
  
 ![垂直漸層的漸層軸](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-verticalgradient.png "wcpsdk\_graphicsmm\_verticalgradient")  
  
<a name="radialgradients"></a>   
## 放射狀漸層  
 如同 <xref:System.Windows.Media.LinearGradientBrush>，<xref:System.Windows.Media.RadialGradientBrush> 會以沿著某個軸逐漸融合的色彩繪製區域。  前述範例顯示出線形漸層筆刷的軸是條直線。  放射狀漸層筆刷的軸則是由圓圈定義，其色彩會從其原點向外「放射」。  
  
 在下列範例中，會使用放射狀漸層筆刷來繪製矩形的內部。  
  
 [!code-xml[GradientBrushExamples_snip#RadialGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]  
  
 下圖顯示在上一個範例中建立的漸層。  其中標示了筆刷的漸層停駐點。  請注意，雖然結果不同，但是這個範例中的漸層停駐點與前面線形漸層筆刷範例中的漸層停駐點是相同的。  
  
 ![放射狀漸層中的漸層停駐點](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk\_graphicsmm\_4gradientstops\_rg")  
  
 <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> 會指定放射狀漸層筆刷之漸層軸的起始點。  漸層軸會從漸層原點放射至漸層圓圈。  筆刷的漸層圓圈是由其 <xref:System.Windows.Media.RadialGradientBrush.Center%2A>、<xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A> 及 <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> 屬性定義。  
  
 下圖顯示具有不同 <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>、<xref:System.Windows.Media.RadialGradientBrush.Center%2A>、<xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A> 及 <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> 設定的數個放射狀漸層。  
  
 ![RadialGradientBrush 設定](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-originscirclesandradii.png "wcpsdk\_graphicsmm\_originscirclesandradii")  
具有不同 GradientOrigin、中心、RadiusX 及 RadiusY 設定的 RadialGradientBrushes。  
  
<a name="specifyinggradientcolors"></a>   
## 指定透明或部分透明的漸層停駐點  
 因為漸層停駐點不提供不透明屬性，所以您必須在標記 \(Markup\) 中使用 [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] 十六進位標記法指定 Alpha 色頻，或使用 <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=fullName> 方法建立透明或部分透明的漸層停駐點。  下列各節會說明如何使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和程式碼建立部分透明的漸層停駐點。  如需設定整個筆刷的不透明度的詳細資訊，請參閱[指定筆刷的不透明度](#brushesAndOpacity)一節。  
  
<a name="argbsyntax"></a>   
### 在 "XAML" 中指定色彩不透明度  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，您可以使用 [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] 十六進位標記法指定個別色彩的不透明度。  [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] 十六進位標記法則使用下列語法：  
  
 `#`**aa** *rrggbb*  
  
 上一行中的 *aa* 代表兩個位數的十六進位值，用來指定色彩的不透明度。  *rr*、*gg* 和 *bb* 分別代表兩個位數的十六進位值，用來指定紅色、綠色及藍色的數量。  每個十六進位位數的值可以是 0\-9 或 A\-F。  0 是最小的值，F 是最大的值。  Alpha 值 00 指定色彩為完全透明，而 FF Alpha 值則會建立完全不透明的色彩。  在下列範例中，會使用十六進位 [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] 標記法指定兩個色彩。  第一個是部分透明 \(具有 x20 的 Alpha 值\)，而第二個則是完全不透明。  
  
 [!code-xml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]  
  
<a name="fromscrgbsyntax"></a>   
### 在程式碼中指定色彩不透明度  
 使用程式碼建立色彩時，您可以利用靜態 <xref:System.Windows.Media.Color.FromArgb%2A> 方法指定 Alpha 值。  這個方法接受四個 <xref:System.Byte> 型別的參數。  第一個參數會指定色彩的 Alpha 色頻，其他三個參數則會指定色彩的紅色、綠色及藍色值。  每個值都應介於 0 到 255 之間 \(含 0 和 255\)。  Alpha 值為 0 會指定色彩為完全透明，而 Alpha 值為 255 則指定色彩為完全不透明。  在下列範例中，會使用 <xref:System.Windows.Media.Color.FromArgb%2A> 方法產生兩個色彩。  第一個色彩是部分透明 \(具有 32 的 Alpha 值\)，而第二個色彩是完全不透明。  
  
 [!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]  
  
 或者，您也可以使用 <xref:System.Windows.Media.Color.FromScRgb%2A> 方法，這個方法可以讓您使用 ScRGB 值建立色彩。  
  
<a name="otherbrushes"></a>   
## 使用影像、繪圖、視覺資料及模式繪製  
 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.DrawingBrush> 及 <xref:System.Windows.Media.VisualBrush> 類別可以讓您使用影像、繪圖或視覺資料繪製區域。  如需使用影像、繪圖及模式繪製的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.Brush>   
 <xref:System.Windows.Media.SolidColorBrush>   
 <xref:System.Windows.Media.LinearGradientBrush>   
 <xref:System.Windows.Media.RadialGradientBrush>   
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [筆刷轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)   
 [圖形轉譯層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)