---
title: "主要畫面格動畫概觀 | Microsoft Docs"
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
  - "動畫, 主要畫面格"
  - "主要畫面格 [WPF], 關於主要畫面格動畫"
  - "多個動畫目標值"
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
caps.latest.revision: 29
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# 主要畫面格動畫概觀
本主題介紹主要畫面格動畫。  主要畫面格動畫可讓您使用兩個以上的目標值來建立動畫，並且控制動畫的插補方法。  
  
 本主題包含下列章節。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
-   [必要條件](#prerequisites)  
  
-   [使用主要畫面格動畫](#keyframeanimations)  
  
-   [相關主題](#seeAlsoToggle)  
  
<a name="prerequisites"></a>   
## 必要條件  
 若要了解本概觀，您應該熟悉 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 動畫和時間表的概念。  如需動畫的簡介，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。熟悉 From\/To\/By 動畫也會有幫助。  如需詳細資訊，請參閱 [From\/To\/By 動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/from-to-by-animations-overview.md)。  
  
<a name="whatisakeyframeanimation"></a>   
## 何謂主要畫面格動畫  
 如同 From\/To\/By 動畫，主要畫面格動畫會以目標屬性的值建立動畫。  它會在 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 期間建立目標值間的轉換。  不過，不像 From\/To\/By 動畫只能建立兩個值之間的轉換，單一主要畫面格動畫可以建立任意個目標值之間的轉換。  此外，主要畫面格動畫沒有 From\/To\/By 動畫的 From、To 或 By 屬性可供設定目標值。  主要畫面格動畫的目標值是以主要畫面格物件來描述 \(所以才有「主要畫面格動畫」一詞\)。  若要指定動畫的目標值時，必須建立主要畫面格物件，再將這些物件加入至動畫的 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> 集合。  執行動畫時，就會在您指定的畫面格之間轉換。  
  
 有些主要畫面格方法除了可以支援多個目標值，甚至還可以支援多種插補方法。  動畫的插補方法定義了動畫如何從某個值轉換成下一個值。  共有三種插補類型：[離散](GTMT)、[線性](GTMT)和[曲線](GTMT)。  
  
 若要以主要畫面格建立動畫，請完成下列步驟。  
  
-   如同 from\/to\/by 動畫，先宣告動畫並指定其 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>。  
  
-   針對每個目標值建立適當類型的主要畫面格、設定其值和 <xref:System.Windows.Media.Animation.KeyTime>，然後將它加入至動畫的 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> 集合。  
  
-   如同 From\/To\/By 動畫，建立動畫與屬性的關聯。  如需使用腳本將動畫套用至屬性的詳細資訊，請參閱[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
 下列範例會使用 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> 以動畫方式將 <xref:System.Windows.Shapes.Rectangle> 項目變換到四個不同的位置。  
  
 [!code-xml[keyframes_ovw_snip#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]
 [!code-xml[keyframes_ovw_snip#BasicKeyFrameExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 如同 From\/To\/By 動畫，在標記和程式碼中使用 <xref:System.Windows.Media.Animation.Storyboard> 或在程式碼中使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法，即可將主要畫面格動畫套用至屬性。  您也可以使用主要畫面格動畫建立 <xref:System.Windows.Media.Animation.AnimationClock>，然後將它套用至一個或多個屬性。  如需套用動畫之不同方法的詳細資訊，請參閱[建立屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)。  
  
<a name="animation_types"></a>   
## 主要畫面格動畫類型  
 由於動畫會產生屬性值，因此屬性型別不同，動畫型別也不同。  若要以接受 <xref:System.Double> 的屬性 \(例如項目的 <xref:System.Windows.FrameworkElement.Width%2A> 屬性\) 建立動畫，請使用會產生 <xref:System.Double> 值的動畫。  如果要讓使用 <xref:System.Windows.Point> 的屬性顯示動畫，請使用會產生 <xref:System.Windows.Point> 值的動畫，依此類推。  
  
 主要畫面格動畫類別屬於 <xref:System.Windows.Media.Animation> 命名空間，並遵循下列命名慣例：  
  
 *\<型別\>* `AnimationUsingKeyFrames`  
  
 其中 *\<Type\>* 是類別顯示為動畫之值的型別。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供下列主要畫面格動畫類別。  
  
|屬性型別|對應的 from\/to\/by 動畫類別|支援的插補方法|  
|----------|---------------------------|-------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|離散|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|離散|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|離散|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|離散|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|離散、線性、曲線|  
  
<a name="animation_target_values"></a>   
## 目標值 \(主要畫面格\) 和關鍵時間  
 就如同不同類型的主要畫面格動畫適用於不同屬性類型的動畫，主要畫面格物件也有不同類型：每種主要畫面格物件各適用於一種值的動畫，且各支援一種插補方法。  主要畫面格類型會遵循下列命名慣例：  
  
 *\<InterpolationMethod\>\<Type\>* `KeyFrame`  
  
 其中 *\<InterpolationMethod\>* 為主要畫面格所使用的插補方法，而 *\<Type\>* 則為此類別使用的動畫值類型。  如果主要畫面格動畫支援所有插補方法，則有三種主要畫面格類型可供您使用。  例如，您可以對 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> 使用三種主要畫面格類型：<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>、<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> 和 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> \(後面的章節會詳述插補方法\)。  
  
 主要畫面格的主要目的在於指定 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> 和 <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>。  每種主要畫面格類型都提供下列兩個屬性。  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> 屬性指定該主要畫面格的目標值。  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> 屬性指定何時 \(在動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 之內\) 到達主要畫面格的 <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>。  
  
 當主要畫面格動畫開始時，會依主要畫面格的 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> 屬性所定義的順序逐一查看主要畫面格。  
  
-   如果在時間為 0 時沒有主要畫面格，則動畫會在目標屬性的目前值與第一個主要畫面格的 <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> 之間建立轉換。否則，動畫的輸出值會成為第一個主要畫面格的值。  
  
-   動畫會使用第二個主要畫面格所指定的插補方法，在第一個與第二個主要畫面格的 <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> 之間建立轉換。  此轉換會在第一個主要畫面格的 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> 開始，並在到達第二個主要畫面格的 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> 時結束。  
  
-   動畫會繼續在後續每個主要畫面格與其前一個主要畫面格之間建立轉換。  
  
-   最後，動畫會轉換至具有最大關鍵時間的主要畫面格的值，而該關鍵時間會小於或等於動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>。  
  
 如果動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 為 <xref:System.Windows.Duration.Automatic%2A>，或是其 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 等於最後一個主要畫面格的時間，動畫即會結束。  否則，如果動畫的 <xref:System.Windows.Duration> 大於最後一個主要畫面格的關鍵時間，則動畫會保留主要畫面格值，直到 <xref:System.Windows.Duration> 結束為止。  如同所有動畫一樣，主要畫面格動畫會使用其 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性，來決定是否要一直使用最後的值直到它的作用期結束為止。  如需詳細資訊，請參閱 [計時行為概觀](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)。  
  
 下列範例會使用上述範例中定義的 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> 物件，來示範 <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> 和 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> 屬性如何運作。  
  
-   第一個主要畫面格會立即將動畫的輸出值設定為 0。  
  
-   第二個主要畫面格會從 0 展示動畫至 350。  它會在第一個主要畫面格結束 \(時間等於 0 秒\) 後開始播放 2 秒，並且在時間等於 0:0:2 時結束。  
  
-   第三個主要畫面格會從 350 展示動畫至 50。  它會在第二個主要畫面格結束 \(時間等於 2 秒\) 時開始播放 5 秒，並且在時間等於 0:0:7 時結束。  
  
-   第四個主要畫面格會從 50 展示動畫至 200。  它會在第三個主要畫面格結束 \(時間等於 7 秒\) 時開始播放 1 秒，並且在時間等於 0:0:8 時結束。  
  
-   因為動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 屬性已設定為 10 秒，所以動畫會在最後的值停留 2 秒，然後在時間等於 0:0:10 時結束。  
  
 [!code-xml[keyframes_ovw_snip#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]
 [!code-xml[keyframes_ovw_snip#BasicKeyFrameExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>   
## 插補方法  
 前面幾節曾提到有些主要畫面格動畫可以支援多種插補方法。  動畫的插補方法描述了動畫如何在其持續期間內進行值之間的轉換。  選取動畫所要使用的主要畫面格類型，即可定義該主要畫面格區段的插補方法。  共有三種不同的插補類型：線性、離散和曲線。  
  
### 線性插補  
 使用[線性插補](GTMT) \(Linear Interpolation\) 時，動畫會在區段的持續期間內以不變的速率進行。  例如，如果主要畫面格區段在 5 秒的持續期間內從 0 轉換成 10，則動畫會在指定的時間輸出下列值：  
  
|時間|輸出值|  
|--------|---------|  
|0|0|  
|1|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4.5|9|  
|5|10|  
  
### 離散插補  
 使用[離散插補](GTMT) \(Discrete Interpolation\)，動畫功能會直接從某個值跳到下一個值，而不使用插補。  如果主要畫面格區段在 5 秒的持續期間內從 0 轉換成 10，則動畫會在指定的時間輸出下列值：  
  
|時間|輸出值|  
|--------|---------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4.5|0|  
|5|10|  
  
 請注意，直到區段的持續期間要結束時，動畫才會變更其輸出值。  
  
 [曲線插補](GTMT) \(Splined Interpolation\) 更為複雜。  下一節將加以說明。  
  
<a name="anim_spline"></a>   
### 曲線插補  
 曲線插補可以達到更逼真的時間效果。  因為動畫經常會用於模擬真實世界中發生的效果，因此開發人員需要精確控制物件的加速和減速情形，並且仔細操控時間區段。  曲線主要畫面格可讓您使用曲線插補來建立動畫。  使用其他主要畫面格時，您必須指定 <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> 和 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>。  使用曲線主要畫面格時，則還必須指定 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>。  下列範例顯示 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> 的單一曲線主要畫面格。  請注意 <xref:System.Windows.Media.Animation.KeySpline> 屬性，就是這個屬性使曲線主要畫面格與其他類型的主要畫面格有所不同。  
  
 [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]
 [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 [三次方貝茲曲線](GTMT)是由一個起始點、一個結束點和兩個控制點所定義。  曲線主要畫面格的 <xref:System.Windows.Media.Animation.KeySpline> 屬性會定義從 \(0,0\) 延伸至 \(1,1\) 之貝茲曲線的兩個控制點。  第一個控制點控制貝茲曲線前半段的曲率，第二個控制點則控制貝茲線段後半段的曲率。  產生的曲線即描述該曲線主要畫面格的變化速率。  曲線越陡峭，主要畫面格變更值的速度就越快。  曲線越平滑，主要畫面格變更值的速度就越慢。  
  
 您可以使用 <xref:System.Windows.Media.Animation.KeySpline> 來模擬實際軌跡 \(像是滴下的水或彈起的球\)，或將其他「加速」與「減速」效果套用至移動動畫。  至於使用者互動效果 \(像是背景淡出或控制按鈕彈回\)，您可以套用曲線插補，以特定方式加速或減慢動畫的變化速率。  
  
 下列範例以 0,1 1,0 指定 <xref:System.Windows.Media.Animation.KeySpline>，這會建立下列貝茲曲線。  
  
 ![貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm\_keyspline\_0\_1\_1\_0")  
控制點位於 \(0.0, 1.0\) 和 \(1.0, 0.0\) 的關鍵 Spline  
  
 [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]
 [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 這個主要畫面格在開始時會急速顯示動畫、而後減慢，然後在結束之前再次加速。  
  
 下列範例以 0.5,0.25 0.75,1.0 指定 <xref:System.Windows.Media.Animation.KeySpline>，這會建立下列貝茲曲線。  
  
 ![貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm\_keyspline\_025\_050\_075\_10")  
控制點位於 \(0.25, 0.5\) 和 \(0.75, 1.0\) 的關鍵 Spline  
  
 [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]
 [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExampleInline3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 因為貝茲曲線的曲率變化很小，所以這個主要畫面格幾乎是以不變的速率顯示動畫，而在結束之前會稍微減慢。  
  
 下列範例會使用 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> 以動畫的方式變換矩形的位置。  因為 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> 會使用 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> 物件，所以每個主要畫面格值之間的轉換都會使用曲線插補。  
  
 [!code-xml[keyframes_ovw_snip#SplinedInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]
 [!code-xml[keyframes_ovw_snip#SplinedInterpolationExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 曲線插補的概念可能不好懂，試試不同的設定會有所幫助。  [關鍵 Spline 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160011) \(英文\) 可讓您變更關鍵 Spline 值，並查看它在動畫上的效果。  
  
<a name="combininginterpolationmethods"></a>   
### 混用插補方法  
 在單一主要畫面格動畫中，您可以對各主要畫面格使用不同的插補類型。  當具有不同插補的兩個主要畫面格動畫彼此相隨時，第二個主要畫面格的插補方法會用於建立由第一個值至第二個值的轉換。  
  
 在下列範例中，會建立使用線性、曲線及離散插補的 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>。  
  
 [!code-xml[keyframes_ovw_snip#ComboInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]
 [!code-xml[keyframes_ovw_snip#ComboInterpolationExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>   
## 深入了解持續期間和關鍵時間  
 如同其他動畫，主要畫面格動畫也有 <xref:System.Windows.Duration> 屬性。  除了指定動畫的 <xref:System.Windows.Duration>，您還需要指定每個主要畫面格要使用這段期間的哪個部分。  若要這麼做，您必須描述動畫之每個主要畫面格的 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>。  每個主要畫面格的 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> 都指定該主要畫面格的結束時間。  
  
 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> 屬性並不是指主要畫面格的播放時間長度。  主要畫面格的播放時間量取決於主要畫面格的結束時間、前一個主要畫面格的結束時間，以及動畫的持續期間。  您可以時間值、百分比或以特殊值 \(<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> 或 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>\) 指定關鍵時間。  
  
 下列清單說明用於指定關鍵時間的幾種不同方法。  
  
### TimeSpan 值  
 您可以使用 <xref:System.TimeSpan> 值來指定 <xref:System.Windows.Media.Animation.KeyTime>。  此值應該大於或等於 0，並且小於或等於動畫的持續期間。  下列範例顯示的動畫具有 10 秒的持續期間和四個主要畫面格，其中每個主要畫面格的關鍵時間都是以時間值指定。  
  
-   第一個主要畫面格會在前 3 秒顯示從基底實值至 100 的動畫，並且在時間等於 0:0:03 時結束。  
  
-   第二個主要畫面格會從 100 展示動畫至 200。  它會在第一個主要畫面格結束 \(時間等於 3 秒\) 後開始播放 5 秒，並且在時間等於 0:0:8 時結束。  
  
-   第三個主要畫面格會從 200 展示動畫至 500。  它會在第二個主要畫面格結束 \(時間等於 8 秒\) 時開始播放 1 秒，並且在時間等於 0:0:9 時結束。  
  
-   第四個主要畫面格會從 500 展示動畫至 600。  它會在第三個主要畫面格結束 \(時間等於 9 秒\) 時開始播放 1 秒，並且在時間等於 0:0:10 時結束。  
  
 [!code-xml[keyframes_ovw_snip#TimeSpanKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyTimesExample.xaml#timespankeytimeexample)]
 [!code-xml[keyframes_ovw_snip#TimeSpanKeyTimeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### 百分比值  
 百分比值，指定主要畫面格在動畫到達 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 的某個百分比時結束。  在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，百分比的指定方式為在數字後面加上 `%` 符號。  在程式碼中，則需將使用 <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> 方法並將表示百分比 <xref:System.Double> 傳遞給它。  此值必須大於或等於 0，並且小於或等於 100%。  下列範例顯示的動畫具有 10 秒的持續期間和四個主要畫面格，其中每個主要畫面格的關鍵時間都是以百分比指定。  
  
-   第一個主要畫面格會在前 3 秒顯示從基底實值至 100 的動畫，並且在時間等於 0:0:3 時結束。  
  
-   第二個主要畫面格會從 100 展示動畫至 200。  它會在第一個主要畫面格結束 \(時間等於 3 秒\) 後開始播放 5 秒，並且在時間等於 0:0:8 \(0.8 \* 10 \= 8\) 時結束。  
  
-   第三個主要畫面格會從 200 展示動畫至 500。  它會在第二個主要畫面格結束 \(時間等於 8 秒\) 時開始播放 1 秒，並且在時間等於 0:0:9 \(0.9 \* 10 \= 9\) 時結束。  
  
-   第四個主要畫面格會從 500 展示動畫至 600。  它會在第三個主要畫面格結束 \(時間等於 9 秒\) 時開始播放 1 秒，並且在時間等於 0:0:10 \(1 \* 10 \= 10\) 時結束。  
  
 [!code-xml[keyframes_ovw_snip#PercentageKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyTimesExample.xaml#percentagekeytimeexample)]
 [!code-xml[keyframes_ovw_snip#PercentageKeyTimeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### Uniform 特殊值  
 當您希望每個主要畫面格都使用相同的時間量時，請使用 <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> 時間。  
  
 <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> 關鍵時間會依主要畫面格數目將可用時間做平均分割，以決定每個主要畫面格的結束時間。  下列範例顯示的動畫具有 10 秒的持續期間和四個主要畫面格，其中每個主要畫面格的關鍵時間都是以 <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> 指定。  
  
-   第一個主要畫面格會在前 2.5 秒顯示從基底實值至 100 的動畫，並且在時間等於 0:0:2.5 時結束。  
  
-   第二個主要畫面格會從 100 展示動畫至 200。  它會在第一個主要畫面格結束 \(時間等於 2.5 秒\) 後開始播放約 2.5 秒，並且在時間等於 0:0:5 時結束。  
  
-   第三個主要畫面格會從 200 展示動畫至 500。  它會在第二個主要畫面格結束 \(時間等於 5 秒\) 時開始播放 2.5 秒，並且在時間等於 0:0:7.5 時結束。  
  
-   第四個主要畫面格會從 500 展示動畫至 600。  它會在第二個主要畫面格結束 \(時間等於 7.5 秒\) 時開始播放 2.5 秒，並且在時間等於 0:0:1 時結束。  
  
 [!code-xml[keyframes_ovw_snip#UniformKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyTimesExample.xaml#uniformkeytimeexample)]
 [!code-xml[keyframes_ovw_snip#UniformKeyTimeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### Paced 特殊值  
 當您要以不變的速率顯示動畫時，請使用 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> 時間。  
  
 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> 關鍵時間會根據每個主要畫面格的長度來配置可用時間，以決定每個畫面格的持續期間。  這樣會使動畫的速度或步調維持不變。  下列範例顯示的動畫具有 10 秒的持續期間和三個主要畫面格，其中每個主要畫面格的關鍵時間都是以 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> 指定。  
  
 [!code-xml[keyframes_ovw_snip#PacedKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyTimesExample.xaml#pacedkeytimeexample)]
 [!code-xml[keyframes_ovw_snip#PacedKeyTimeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 請注意，如果最後一個主要畫面格的關鍵時間為 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> 或 <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>，其解析後的關鍵時間將會設定 100%。  如果多格動畫中的第一個主要畫面格已設定速度，其解析後的關鍵時間將會設定 0。  如果主要畫面格集合僅包含單一主要畫面格，而且是已設定速度的主要畫面格，其解析後的關鍵時間將會設定為 100%。  
  
 單一主要畫面格動畫中的不同主要畫面格可以使用不同的主要畫面格類型。  
  
<a name="combiningkeytimes"></a>   
## 合併關鍵時間、不按順序的主要畫面格  
 您可以在相同動畫中使用具有不同 <xref:System.Windows.Media.Animation.KeyTime> 值類型的主要畫面格。  而且，雖然建議您依播放順序加入主要畫面格，但這不是必要的。  動畫和計時系統能夠解析不按順序的主要畫面格。  系統會忽略具有無效關鍵時間的主要畫面格。  
  
 下列清單說明在主要畫面格動畫中，解析主要畫面格關鍵時間的程序。  
  
1.  解析 <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> 值。  
  
2.  決定動畫的「總插補時間」，也就是主要畫面格動畫用於完成向前查看的總時間。  
  
    1.  如果動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 不是 <xref:System.Windows.Duration.Automatic%2A> 或 <xref:System.Windows.Duration.Forever%2A>，則總插補時間為動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 屬性值。  
  
    2.  否則，總插補時間為在其主要畫面格中指定的最大 <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> 值 \(如果有的話\)。  
  
    3.  否則，總插補時間為 1 秒。  
  
3.  使用總插補時間值來解析 <xref:System.Windows.Media.Animation.KeyTimeType> <xref:System.Windows.Media.Animation.KeyTime> 值。  
  
4.  如果尚未在先前步驟中解析最後一個主要畫面格，則加以解析。  如果最後一個主要畫面格的 <xref:System.Windows.Media.Animation.KeyTime> 為 <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> 或 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>，則其解析後的時間將會等於總插補時間。  
  
     如果第一個主要畫面格的 <xref:System.Windows.Media.Animation.KeyTime> 為 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> 且此動畫有不只一個主要畫面格，則將其 <xref:System.Windows.Media.Animation.KeyTime> 值解析為零。如果只有一個主要畫面格且其 <xref:System.Windows.Media.Animation.KeyTime> 值為 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>，則會如前一個步驟所述而解析為總插補時間。  
  
5.  解析剩餘的 <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> 值：它們都會平等分到可用時間。  在此程序期間，未解析的 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> 值會暫時視為 <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> 值，而取得暫時解析的時間。  
  
6.  使用宣告最接近且已解析 <xref:System.Windows.Media.Animation.KeyTime> 值的主要畫面格，來解析未指定關鍵時間之主要畫面格的 <xref:System.Windows.Media.Animation.KeyTime> 值。  
  
7.  解析剩餘的 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> 值。  <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> 會使用鄰近主要畫面格的 <xref:System.Windows.Media.Animation.KeyTime> 值來決定其解析後的時間。  這是為了確保動畫的速度維持在此主要畫面格的解析時間左右。  
  
8.  按照解析後的時間的順序 \(主索引鍵\) 和宣告的順序 \(次要索引鍵\) 來排序主要畫面格，也就是使用以解析後的主要畫面格 <xref:System.Windows.Media.Animation.KeyTime> 值為基礎的穩定排序。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.KeyTime>   
 <xref:System.Windows.Media.Animation.KeySpline>   
 <xref:System.Windows.Media.Animation.Timeline>   
 [關鍵 Spline 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160011)   
 [KeyFrame 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [主要畫面格 HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)   
 [計時行為概觀](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)