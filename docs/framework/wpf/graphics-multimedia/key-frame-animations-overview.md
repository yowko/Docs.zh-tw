---
title: 主要畫面格動畫概觀
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
ms.openlocfilehash: be815ca522cf18ea2403ea7af5549ceaf922854e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186675"
---
# <a name="key-frame-animations-overview"></a>主要畫面格動畫概觀
本主題介紹主要畫面格動畫。 主要畫面格動畫可讓您使用兩個以上的目標值來建立動畫，並且控制動畫的插補方法。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 若要了解本概觀，您應該熟悉 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 動畫和時間軸。 如需動畫的簡介，請參閱[動畫概觀](animation-overview.md)。 它也有助於熟悉 From/To/By 動畫。 如需詳細資訊，請參閱 From/To/By 動畫概觀。  
  
<a name="whatisakeyframeanimation"></a>
## <a name="what-is-a-key-frame-animation"></a>什麼是主要畫面格動畫？  
 就像 From/To/By 動畫一樣，主要畫面格動畫會以目標屬性的值產生動畫。 它在其目標值之間在其 上創建一<xref:System.Windows.Media.Animation.Timeline.Duration%2A>個轉換。 不過，不像 From/To/By 動畫只能建立兩個值之間的轉換，單一畫面格動畫可以建立任意數目目標值之間的轉換。 不同於 From/To/By 動畫，主要畫面格動畫沒有 From、To 或 By 屬性可供設定目標值。 主要畫面格動畫的目標值是以主要畫面格物件來描述 (因此有「主要畫面格動畫」一詞)。 要指定動畫的目標值，請創建關鍵幀物件並將其添加到動畫<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A>的集合中。 動畫執行時，就會在您指定的畫面格之間轉換。  
  
 除了支援多個目標值之外，某些主要畫面格方法甚至支援多種插補方法。 動畫的插補方法定義了動畫如何從某個值轉換成下一個值。 插補有以下三種類型：離散、線性和曲線。  
  
 若要以主要畫面格動畫建立動畫，您必須完成下列步驟。  
  
- 聲明動畫並指定其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>，就像從/到/由動畫一樣。  
  
- 對於每個目標值，創建相應類型的關鍵幀，設置其值和<xref:System.Windows.Media.Animation.KeyTime>，並將其添加到動畫<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A>的集合中。  
  
- 如同 From/To/By 動畫，建立動畫與屬性的關聯。 如需使用分鏡腳本將動畫套用至屬性的詳細資訊，請參閱[分鏡腳本概觀](storyboards-overview.md)。  
  
 下面的示例使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>將<xref:System.Windows.Shapes.Rectangle>元素動畫添加到四個不同位置。  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 與 From/To/By 動畫一樣，關鍵幀動畫可以通過在標記和代碼<xref:System.Windows.Media.Animation.Storyboard>中使用 或在代碼中使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法應用於屬性。 您還可以使用關鍵幀動畫創建 ，<xref:System.Windows.Media.Animation.AnimationClock>並將其應用於一個或多個屬性。 有關應用動畫的不同方法的詳細資訊，請參閱[屬性動畫技術概述](property-animation-techniques-overview.md)。  
  
<a name="animation_types"></a>
## <a name="key-frame-animation-types"></a>主要畫面格動畫型別  
 由於動畫會產生屬性值，因此針對不同的屬性類型會有不同的動畫類型。 要為採用（<xref:System.Double>如元素<xref:System.Windows.FrameworkElement.Width%2A>的屬性）的屬性設置動畫，請使用生成<xref:System.Double>值的動畫。 要為採用<xref:System.Windows.Point>的屬性設置動畫，請使用生成<xref:System.Windows.Point>值的動畫，等等。  
  
 關鍵幀動畫類屬於<xref:System.Windows.Media.Animation>命名空間，並遵循以下命名約定：  
  
 * \<鍵入>*`AnimationUsingKeyFrames`  
  
 * \<類型>* 是類動畫的數值型別。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供下列主要畫面格動畫類別。  
  
|屬性類型|對應 from/to/by 動畫類別|支援的插補方法|  
|-------------------|------------------------------------------------|-------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|Discrete|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|Discrete|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|Discrete|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Discrete|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|離散、線性、曲線|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|離散、線性、曲線|  
  
<a name="animation_target_values"></a>
## <a name="target-values-key-frames-and-key-times"></a>目標值 (主要畫面格) 和關鍵時間  
 就如同不同型別的主要畫面格動畫適用於不同屬性型別的動畫，主要畫面格物件也有不同型別：每種主要畫面格物件各適用於一種值的動畫，且各支援一種插補方法。 主要畫面格型別會遵循下列命名慣例：  
  
 *插值方法>\<類型>\< *`KeyFrame`  
  
 其中*\<插值方法>* 是關鍵幀使用的插值方法，*\<類型>* 是類動畫的數值型別。 支援所有三種插補方法的主要畫面格動畫，會有三種主要畫面格型別可供您使用。 例如，可以使用三個關鍵框架類型與<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>：<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>和<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>。 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> (稍後的章節會詳述插補方法。)  
  
 關鍵幀的主要目的是指定 和<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>。 <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> 每個主要畫面格型別都提供下列兩個屬性。  
  
- 屬性<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>指定該關鍵幀的目標值。  
  
- 該<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>屬性指定何時（在動畫的<xref:System.Windows.Media.Animation.Timeline.Duration%2A>）中到達關鍵幀。 <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>  
  
 當關鍵幀動畫開始時，按其<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>屬性定義的順序遍接其關鍵幀。  
  
- 如果時間 0 時沒有關鍵幀，動畫會在目標屬性的當前值和第<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>一個關鍵幀之間的轉換;否則，動畫的輸出值將成為第一個關鍵幀的值。  
  
- 動畫使用第二個關鍵幀指定的<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>插值方法在第一個關鍵幀和第二個關鍵幀之間創建過渡。 轉換從第一個關鍵幀開始<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>，並在到達第二個關鍵幀<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>時結束。  
  
- 動畫會繼續在後續每個主要畫面格與其前一個主要畫面格之間建立轉換。  
  
- 最後，動畫轉換為關鍵幀的值，其最大鍵時間等於或小於動畫的值<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。  
  
 如果動畫的<xref:System.Windows.Media.Animation.Timeline.Duration%2A>或<xref:System.Windows.Duration.Automatic%2A>其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>等於最後一個關鍵幀的時間，則動畫結束。 否則，如果動畫大於<xref:System.Windows.Duration>最後一個關鍵幀的鍵時間，則動畫將保留關鍵幀值，直到到達其<xref:System.Windows.Duration>的末尾。 與所有動畫一樣，關鍵幀動畫使用其<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性來確定在到達活動週期結束時是否保留最終值。 如需詳細資訊，請參閱[計時行為概觀](timing-behaviors-overview.md)。  
  
 下面的示例使用上例<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>中定義的物件來演示<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>和<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>屬性的工作原理。  
  
- 第一個主要畫面格會立即將動畫的輸出值設定為 0。  
  
- 第二個主要畫面格會從 0 展示動畫至 350。 它會在第一個主要畫面格結束 (時間等於 0 秒) 後開始播放 2 秒，並且在時間等於 0:0:2 時結束。  
  
- 第三個主要畫面格會從 350 展示動畫至 50。 它會在第二個主要畫面格結束 (時間等於 2 秒) 時開始播放 5 秒，並且在時間等於 0:0:7 時結束。  
  
- 第四個主要畫面格會從 50 展示動畫至 200。 它會在第三個主要畫面格結束 (時間等於 7 秒) 時開始播放 1 秒，並且在時間等於 0:0:8 時結束。  
  
- 由於動畫<xref:System.Windows.Media.Animation.Timeline.Duration%2A>的屬性設置為 10 秒，因此動畫在時間結束前保留其最終值兩秒 = 0：0：10。  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>
## <a name="interpolation-methods"></a>插補方法  
 前面幾節曾提到有些主要畫面格動畫可以支援多種插補方法。 動畫的插補描述了動畫如何在其持續期間內進行值之間的轉換。 選取動畫所要使用的主要畫面格型別，即可定義該主要畫面格區段的插補方法。 插補方法有三種不同類型：線性、離散和曲線。  
  
### <a name="linear-interpolation"></a>線性插補  
 使用線性插補，動畫在區段的持續時間會以不變的速率進行。 例如，如果主要畫面格區段在 5 秒的持續期間從 0 轉換為 10，動畫將會於指定的時間輸出下列值：  
  
|Time|輸出值|  
|----------|------------------|  
|0|0|  
|1|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4.5|9|  
|5|10|  
  
### <a name="discrete-interpolation"></a>離散插補  
 使用離散插補，動畫功能會從某個值跳到下個值而不使用插補。 如果主要畫面格區段在 5 秒的持續期間從 0 轉換為 10，動畫將會於指定的時間輸出下列值：  
  
|Time|輸出值|  
|----------|------------------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4.5|0|  
|5|10|  
  
 請注意，在區段持續期間結束之前，動畫不會變更其輸出值。  
  
 曲線插補更為複雜。 下一節將加以說明。  
  
<a name="anim_spline"></a>
### <a name="splined-interpolation"></a>曲線插補  
 曲線插補可用來達成更逼真的時間效果。 因為動畫經常用來模擬真實世界中發生的效果，因此開發人員需要精確控制物件的加速和減速情形，並且仔細操控時間區段。 曲線主要畫面格可讓您使用曲線插補來建立動畫。 使用其他關鍵幀，請指定<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>和<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>。 使用樣條線鍵框架，還可以指定 。 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> 下面的示例顯示了 的<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>單個樣條線鍵框架。 請注意屬性<xref:System.Windows.Media.Animation.KeySpline>;這就是樣條線關鍵幀不同于其他類型的關鍵幀的原因。  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 三次方貝茲曲線是由一個起始點、一個結束點和兩個控制點所定義。 <xref:System.Windows.Media.Animation.KeySpline>樣條線關鍵幀的屬性定義貝茲曲線的兩個控制點，從 （0，0） 一直延伸到 （1，1）。 第一個控制點控制貝茲曲線前半段的曲率，第二個控制點則控制貝茲線段後半段的曲率。 產生的曲線即描述該曲線主要畫面格的變化速率。 曲線越陡峭，主要畫面格變更值的速度就越快。 曲線越平滑，主要畫面格變更值的速度就越慢。  
  
 您可以使用<xref:System.Windows.Media.Animation.KeySpline>來類比物理軌跡，如落水或彈跳球，或將其他"緩入"和"緩出"效果應用於運動動畫。 至於使用者互動效果 (像是背景淡出或控制按鈕彈回)，您可以套用曲線插補，以特定方式加速或減慢動畫的變化速率。  
  
 下面的示例指定 0，1 <xref:System.Windows.Media.Animation.KeySpline> 1，0，這將創建以下貝茲曲線。  
  
 ![貝茲曲線](./media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
控制點位於 (0.0, 1.0) 和 (1.0, 0.0) 的主要曲線  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 這個主要畫面格在開始時會急速顯示動畫，而後減慢，然後在結束之前再次加速。  
  
 下面的示例指定 0.5，0.25 <xref:System.Windows.Media.Animation.KeySpline> 0.75，1.0，這將創建以下貝茲曲線。  
  
 ![貝茲曲線](./media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
控制點位於 (0.25, 0.5) 和 (0.75, 1.0) 的主要曲線  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 因為貝茲曲線的曲率變化很小，所以這個主要畫面格幾乎是以不變的速率顯示動畫；它在結束之前會稍微減慢。  
  
 下面的示例使用 為<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>矩形位置設置動畫。 由於<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>使用<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>物件，因此每個關鍵幀值之間的過渡都使用傾斜的插值。  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 曲線插補的概念可能不好理解；試試不同的設定會有所幫助。 [主要曲線動畫範例 (英文)](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations) 可讓您變更主要曲線值，並查看它在動畫上的效果。  
  
<a name="combininginterpolationmethods"></a>
### <a name="combining-interpolation-methods"></a>結合插補方法  
 在單一主要畫面格動畫中，您可以使用主要畫面格搭配不同的插補類型。 當具有不同插補的兩個主要畫面格動畫彼此相隨時，第二個主要畫面格的插補方法會用來建立第一個值到第二個值的轉換。  
  
 在下面的示例中，<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>創建使用線性、拼接和離散插值的 創建。  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>
## <a name="more-about-duration-and-key-times"></a>深入了解持續期間和關鍵時間  
 與其他動畫一樣，關鍵幀動畫具有屬性<xref:System.Windows.Duration>。 除了指定動畫的<xref:System.Windows.Duration>外，還需要指定每個關鍵幀的持續時間的哪一部分。 為此，您可以為每個動畫的關鍵<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>幀描述 。 每個關鍵幀指定<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>該關鍵幀的結束時間。  
  
 屬性<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>不指定金鑰時間播放的時間。 主要畫面格的播放時間量取決於主要畫面格的結束時間、前一個主要畫面格的結束時間，以及動畫的持續期間。 關鍵時間可以指定為時間值、百分比或特殊值<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>或<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>。  
  
 下列清單說明指定關鍵時間的幾種不同方式。  
  
### <a name="timespan-values"></a>TimeSpan 值  
 可以使用<xref:System.TimeSpan>值指定 。 <xref:System.Windows.Media.Animation.KeyTime> 此值應該大於或等於 0，並且小於或等於動畫的持續期間。 下列範例顯示的動畫具有 10 秒的持續期間和四個主要畫面格，其中每個主要畫面格的關鍵時間都是以時間值指定。  
  
- 第一個主要畫面格會在前 3 秒顯示從基底值至 100 的動畫，並且在時間等於 0:0:03 時結束。  
  
- 第二個主要畫面格會從 100 展示動畫至 200。 它會在第一個主要畫面格結束 (時間等於 3 秒) 後開始播放 5 秒，並且在時間等於 0:0:8 時結束。  
  
- 第三個主要畫面格會從 200 展示動畫至 500。 它會在第二個主要畫面格結束 (時間等於 8 秒) 時開始播放 1 秒，並且在時間等於 0:0:9 時結束。  
  
- 第四個主要畫面格會從 500 展示動畫至 600。 它會在第三個主要畫面格結束 (時間等於 9 秒) 時開始播放 1 秒，並且在時間等於 0:0:10 時結束。  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>百分比值  
 百分比值指定關鍵幀以動畫的某些<xref:System.Windows.Media.Animation.Timeline.Duration%2A>百分比結束。 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，百分比的指定方式為在數字後面加上 `%` 符號。 在代碼中，使用<xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A>方法並傳遞一個<xref:System.Double>指示百分比的方法。 值必須大於或等於 0 且小於或等於 100%。 下列範例顯示的動畫具有 10 秒的持續期間和四個主要畫面格，其中每個主要畫面格的關鍵時間都是以百分比指定。  
  
- 第一個主要畫面格會在前 3 秒顯示從基底值至 100 的動畫，並且在時間等於 0:0:3 時結束。  
  
- 第二個主要畫面格會從 100 展示動畫至 200。 它會在第一個主要畫面格結束 (時間等於 3 秒) 後開始播放 5 秒，並且在時間等於 0:0:8 (0.8 * 10 = 8) 時結束。  
  
- 第三個主要畫面格會從 200 展示動畫至 500。 它會在第二個主要畫面格結束 (時間等於 8 秒) 時開始播放 1 秒，並且在時間等於 0:0:9 (0.9 * 10 = 9) 時結束。  
  
- 第四個主要畫面格會從 500 展示動畫至 600。 它會在第三個主要畫面格結束 (時間等於 9 秒) 時開始播放 1 秒，並且在時間等於 0:0:10 (1 * 10 = 10) 時結束。  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>特殊值 Uniform  
 當您<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>希望每個關鍵幀花費相同的時間時，請使用計時。  
  
 <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>關鍵時間將可用時間平均除以關鍵幀數，以確定每個關鍵幀的結束時間。 下面的示例顯示持續時間為 10 秒的動畫和四個關鍵幀，其關鍵時間指定為<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>。  
  
- 第一個主要畫面格會在前 2.5 秒顯示從基底值至 100 的動畫，並且在時間等於 0:0:2.5 時結束。  
  
- 第二個主要畫面格會從 100 展示動畫至 200。 它會在第一個主要畫面格結束 (時間等於 2.5 秒) 後開始播放 2.5 秒，並且在時間等於 0:0:5 時結束。  
  
- 第三個主要畫面格會從 200 展示動畫至 500。 它會在第二個主要畫面格結束 (時間等於 5 秒) 時開始播放 2.5 秒，並且在時間等於 0:0:7.5 時結束。  
  
- 第四個主要畫面格會從 500 展示動畫至 600。 它會在第二個主要畫面格結束 (時間等於 7.5 秒) 時開始播放 2.5 秒，並且在時間等於 0:0:1 時結束。  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>特殊值 Paced  
 如果要<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>以恒定速率進行動畫處理，請使用計時。  
  
 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>關鍵時間根據每個關鍵幀的長度分配可用時間，以確定每個幀的持續時間。  這樣會使動畫的速度或步調維持不變。  下面的示例顯示持續時間為 10 秒的動畫和三個關鍵幀，其關鍵時間指定為<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>。  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 請注意，如果最後一個關鍵幀的金鑰時間是<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>或<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>，則其解析的金鑰時間將設置為 100%。 如果多格動畫中的第一個主要畫面格已設定速度，其解析後的關鍵時間將會設定 0。 (如果主要畫面格集合僅包含單一主要畫面格，而且是已設定速度的主要畫面格，其解析後的關鍵時間將會設定為 100%。)  
  
 單一主要畫面格動畫中的不同主要畫面格可以使用不同的主要畫面格型別。  
  
<a name="combiningkeytimes"></a>
## <a name="combining-key-times-out-of-order-key-frames"></a>合併關鍵時間、不按順序的主要畫面格  
 您可以在同一動畫中使用具有不同<xref:System.Windows.Media.Animation.KeyTime>數值型別的關鍵幀。 而且，雖然建議您依播放順序加入主要畫面格，但這不是必要的。 動畫和計時系統能夠解析不按順序的主要畫面格。 系統會忽略具有無效關鍵時間的主要畫面格。  
  
 下列清單說明在主要畫面格動畫中，解析主要畫面格關鍵時間的程序。  
  
1. 解析<xref:System.TimeSpan><xref:System.Windows.Media.Animation.KeyTime>值。  
  
2. 決定動畫的「總插補時間」**，也就是主要畫面格動畫用於完成向前逐一查看的總時間。  
  
    1. 如果動畫的<xref:System.Windows.Media.Animation.Timeline.Duration%2A>不是<xref:System.Windows.Duration.Automatic%2A>或<xref:System.Windows.Duration.Forever%2A>，則總插值時間是動畫<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性的值。  
  
    2. 否則，總插值時間是其關鍵幀（<xref:System.TimeSpan><xref:System.Windows.Media.Animation.KeyTime>如果有）之間指定的最大值。  
  
    3. 否則，總插補時間為 1 秒。  
  
3. 使用總插值時間值解析<xref:System.Windows.Media.Animation.KeyTimeType.Percent><xref:System.Windows.Media.Animation.KeyTime>值。  
  
4. 如果尚未在先前步驟中解析最後一個主要畫面格，則加以解析。 如果最後<xref:System.Windows.Media.Animation.KeyTime>一個關鍵幀為<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>或<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>，則其解析時間將等於總插值時間。  
  
     如果第<xref:System.Windows.Media.Animation.KeyTime>一個關鍵幀的，<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>並且此動畫比關鍵幀多，則將其<xref:System.Windows.Media.Animation.KeyTime>值解析為零;如果只有一個關鍵幀，並且其<xref:System.Windows.Media.Animation.KeyTime>值為<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>，則解析為總插值時間，如上一步所述。  
  
5. 解析剩餘<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime>值：每個值都給定可用時間的相等份額。  在此過程中<xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime>，未解析的值將暫時視為<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime>值，並獲得臨時解析的時間。  
  
6. 使用聲明<xref:System.Windows.Media.Animation.KeyTime>的最接近具有已解析<xref:System.Windows.Media.Animation.KeyTime>值的關鍵幀，解決未指定金鑰時間的關鍵幀的值。  
  
7. 解析剩餘<xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime>值。 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime>使用相鄰<xref:System.Windows.Media.Animation.KeyTime>關鍵幀的值來確定其解析時間。  這是為了確保動畫的速度維持在此主要畫面格的解析時間。  
  
8. 按解析時間（主鍵）和聲明順序（輔助鍵）對關鍵幀進行排序，即根據已解決的關鍵幀<xref:System.Windows.Media.Animation.KeyTime>值使用穩定排序。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.KeyTime>
- <xref:System.Windows.Media.Animation.KeySpline>
- <xref:System.Windows.Media.Animation.Timeline>
- [主要曲線動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations)
- [主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)
- [動畫概觀](animation-overview.md)
- [分鏡腳本概觀](storyboards-overview.md)
- [主要畫面格操作說明主題](key-frame-animation-how-to-topics.md)
- [計時行為概觀](timing-behaviors-overview.md)
