---
title: 主要畫面格動畫概觀
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
ms.openlocfilehash: eda91ab6d81150749dc542139949fb92684c0fe1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316735"
---
# <a name="key-frame-animations-overview"></a>主要畫面格動畫概觀
本主題介紹主要畫面格動畫。 主要畫面格動畫可讓您使用兩個以上的目標值來建立動畫，並且控制動畫的插補方法。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本概觀，您應該熟悉 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 動畫和時間軸。 如需動畫的簡介，請參閱[動畫概觀](animation-overview.md)。 它也有助於熟悉 From/To/By 動畫。 如需詳細資訊，請參閱 From/To/By 動畫概觀。  
  
<a name="whatisakeyframeanimation"></a>   
## <a name="what-is-a-key-frame-animation"></a>什麼是主要畫面格動畫？  
 就像 From/To/By 動畫一樣，主要畫面格動畫會以目標屬性的值產生動畫。 它透過建立目標值間的轉換其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。 不過，不像 From/To/By 動畫只能建立兩個值之間的轉換，單一畫面格動畫可以建立任意數目目標值之間的轉換。 不同於 From/To/By 動畫，主要畫面格動畫沒有 From、To 或 By 屬性可供設定目標值。 主要畫面格動畫的目標值是以主要畫面格物件來描述 (因此有「主要畫面格動畫」一詞)。 若要指定動畫的目標值，方法，您可以建立主要畫面格物件，並將它們加入至動畫的<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A>集合。 動畫執行時，就會在您指定的畫面格之間轉換。  
  
 除了支援多個目標值之外，某些主要畫面格方法甚至支援多種插補方法。 動畫的插補方法定義了動畫如何從某個值轉換成下一個值。 插補有以下三種類型：離散、線性和曲線。  
  
 若要以主要畫面格動畫建立動畫，您必須完成下列步驟。  
  
-   宣告動畫並指定其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>，就像您一樣的 from/to/by 動畫。  
  
-   每個目標值，建立適當型別的主要畫面格，請將其值和<xref:System.Windows.Media.Animation.KeyTime>，並將它加入至動畫的<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A>集合。  
  
-   如同 From/To/By 動畫，建立動畫與屬性的關聯。 如需使用分鏡腳本將動畫套用至屬性的詳細資訊，請參閱[分鏡腳本概觀](storyboards-overview.md)。  
  
 下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>來以動畫顯示<xref:System.Windows.Shapes.Rectangle>四個不同位置的項目。  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 像 From/To/By 動畫，主要畫面格動畫可以藉由套用至屬性<xref:System.Windows.Media.Animation.Storyboard>標記和程式碼或使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>在程式碼中的方法。 您也可以使用主要畫面格動畫建立<xref:System.Windows.Media.Animation.AnimationClock>並將它套用至一或多個屬性。 如需套用動畫之不同方法的詳細資訊，請參閱[屬性動畫技術概觀](property-animation-techniques-overview.md)。  
  
<a name="animation_types"></a>   
## <a name="key-frame-animation-types"></a>主要畫面格動畫型別  
 由於動畫會產生屬性值，因此針對不同的屬性類型會有不同的動畫類型。 若要動畫顯示採用的屬性<xref:System.Double>(例如項目的<xref:System.Windows.FrameworkElement.Width%2A>屬性)，您使用會產生動畫<xref:System.Double>值。 若要動畫顯示採用的屬性<xref:System.Windows.Point>，您使用會產生動畫<xref:System.Windows.Point>值，並依此類推。  
  
 主要畫面格動畫類別屬於<xref:System.Windows.Media.Animation>命名空間，並遵循下列命名慣例：  
  
 *\<Type>* `AnimationUsingKeyFrames`  
  
 其中 *\<Type>* 是該類別建立動畫的值類型。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供下列主要畫面格動畫類別。  
  
|屬性類型|對應 from/to/by 動畫類別|支援的插補方法|  
|-------------------|------------------------------------------------|-------------------------------------|  
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
## <a name="target-values-key-frames-and-key-times"></a>目標值 (主要畫面格) 和關鍵時間  
 就如同不同型別的主要畫面格動畫適用於不同屬性型別的動畫，主要畫面格物件也有不同型別：每種主要畫面格物件各適用於一種值的動畫，且各支援一種插補方法。 主要畫面格型別會遵循下列命名慣例：  
  
 *\<InterpolationMethod>\<Type>* `KeyFrame`  
  
 其中 *\<InterpolationMethod>* 是主要畫面格使用的插補方法，而 *\<Type>* 是該類別建立動畫的值類型。 支援所有三種插補方法的主要畫面格動畫，會有三種主要畫面格型別可供您使用。 例如，您可以使用三個主要畫面格類型及其<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>: <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>， <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>，和<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>。 (稍後的章節會詳述插補方法。)  
  
 主要畫面格的主要目的是指定<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>和<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>。 每個主要畫面格型別都提供下列兩個屬性。  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>屬性會指定該主要畫面格的目標值。  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>屬性會指定何時 (在動畫<xref:System.Windows.Media.Animation.Timeline.Duration%2A>) 主要畫面格的<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>為止。  
  
 主要畫面格動畫開始時，逐一查看主要畫面格所定義的順序及其<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>屬性。  
  
-   如果在時間 0 有沒有主要畫面格動畫可建立目標屬性的目前值之間的轉換和<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>的第一個主要畫面格; 否則動畫的輸出值會變成第一個主要畫面格的值。  
  
-   動畫建立之間的轉換<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>第一個和第二個主要畫面格使用指定的第二個主要畫面格的插補方法。 在轉換開始第一個主要畫面格的<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>時結束，第二個主要畫面格的<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>為止。  
  
-   動畫會繼續在後續每個主要畫面格與其前一個主要畫面格之間建立轉換。  
  
-   最後，主要畫面格的最大的索引鍵時間，動畫會轉換成的值就等於或小於動畫的<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。  
  
 如果動畫<xref:System.Windows.Media.Animation.Timeline.Duration%2A>已<xref:System.Windows.Duration.Automatic%2A>或其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>等於最後一個主要畫面格，在動畫結束時間。 否則，如果動畫<xref:System.Windows.Duration>大於最後一個主要畫面格，主要畫面格的值，直到它到達結尾動畫保存的關鍵時間其<xref:System.Windows.Duration>。 如同所有動畫，主要畫面格動畫會使用其<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性來判斷是否它會保留其最終值到達它的作用期結束時。 如需詳細資訊，請參閱[計時行為概觀](timing-behaviors-overview.md)。  
  
 下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>物件，定義在上述範例中示範如何<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>和<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>屬性運作。  
  
-   第一個主要畫面格會立即將動畫的輸出值設定為 0。  
  
-   第二個主要畫面格會從 0 展示動畫至 350。 它會在第一個主要畫面格結束 (時間等於 0 秒) 後開始播放 2 秒，並且在時間等於 0:0:2 時結束。  
  
-   第三個主要畫面格會從 350 展示動畫至 50。 它會在第二個主要畫面格結束 (時間等於 2 秒) 時開始播放 5 秒，並且在時間等於 0:0:7 時結束。  
  
-   第四個主要畫面格會從 50 展示動畫至 200。 它會在第三個主要畫面格結束 (時間等於 7 秒) 時開始播放 1 秒，並且在時間等於 0:0:8 時結束。  
  
-   因為<xref:System.Windows.Media.Animation.Timeline.Duration%2A>動畫的屬性設定為 10 秒，則動畫會保留其最終的值為兩秒，然後結束時間等於 0:0:10。  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>   
## <a name="interpolation-methods"></a>插補方法  
 前面幾節曾提到有些主要畫面格動畫可以支援多種插補方法。 動畫的插補描述了動畫如何在其持續期間內進行值之間的轉換。 選取動畫所要使用的主要畫面格型別，即可定義該主要畫面格區段的插補方法。 插補方法有三種不同類型：線性、離散和曲線。  
  
### <a name="linear-interpolation"></a>線性插補  
 使用線性插補，動畫在區段的持續時間會以不變的速率進行。 例如，如果主要畫面格區段在 5 秒的持續期間從 0 轉換為 10，動畫將會於指定的時間輸出下列值：  
  
|時間|輸出值|  
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
  
|時間|輸出值|  
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
 曲線插補可用來達成更逼真的時間效果。 因為動畫經常用來模擬真實世界中發生的效果，因此開發人員需要精確控制物件的加速和減速情形，並且仔細操控時間區段。 曲線主要畫面格可讓您使用曲線插補來建立動畫。 使用其他主要畫面格，您指定<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>和<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>。 使用曲線主要畫面格，您也指定<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>。 下列範例顯示的單一曲線主要畫面格<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>。 請注意<xref:System.Windows.Media.Animation.KeySpline>屬性; 就是讓曲線主要畫面格不同於其他類型的主要畫面格。  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 三次方貝茲曲線是由一個起始點、一個結束點和兩個控制點所定義。 <xref:System.Windows.Media.Animation.KeySpline>的曲線主要畫面格的屬性會定義從 (0，0) 延伸至 (1，1) 之貝茲曲線的兩個控制點。 第一個控制點控制貝茲曲線前半段的曲率，第二個控制點則控制貝茲線段後半段的曲率。 產生的曲線即描述該曲線主要畫面格的變化速率。 曲線越陡峭，主要畫面格變更值的速度就越快。 曲線越平滑，主要畫面格變更值的速度就越慢。  
  
 您可以使用<xref:System.Windows.Media.Animation.KeySpline>來模擬實體滴下，例如切換 water 或彈跳球，或將其他 「 加速 」 與 「 減速 」 效果套用至移動動畫。 至於使用者互動效果 (像是背景淡出或控制按鈕彈回)，您可以套用曲線插補，以特定方式加速或減慢動畫的變化速率。  
  
 下列範例會指定<xref:System.Windows.Media.Animation.KeySpline>的 0，1 1，這會建立下列貝茲曲線，0。  
  
 ![貝茲曲線](./media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
控制點位於 (0.0, 1.0) 和 (1.0, 0.0) 的主要曲線  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 這個主要畫面格在開始時會急速顯示動畫，而後減慢，然後在結束之前再次加速。  
  
 下列範例會指定<xref:System.Windows.Media.Animation.KeySpline>的 0.5,0.25 0.75,1.0，這會建立下列貝茲曲線。  
  
 ![貝茲曲線](./media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
控制點位於 (0.25, 0.5) 和 (0.75, 1.0) 的主要曲線  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 因為貝茲曲線的曲率變化很小，所以這個主要畫面格幾乎是以不變的速率顯示動畫；它在結束之前會稍微減慢。  
  
 下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>以動畫顯示矩形的位置。 因為<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>使用<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>物件，每個主要畫面格值之間的轉換使用曲線插補。  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 曲線插補的概念可能不好理解；試試不同的設定會有所幫助。 [主要曲線動畫範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=160011) 可讓您變更主要曲線值，並查看它在動畫上的效果。  
  
<a name="combininginterpolationmethods"></a>   
### <a name="combining-interpolation-methods"></a>結合插補方法  
 在單一主要畫面格動畫中，您可以使用主要畫面格搭配不同的插補類型。 當具有不同插補的兩個主要畫面格動畫彼此相隨時，第二個主要畫面格的插補方法會用來建立第一個值到第二個值的轉換。  
  
 在下列範例中，<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>會建立該使用線性、 曲線和離散插補。  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>   
## <a name="more-about-duration-and-key-times"></a>深入了解持續期間和關鍵時間  
 如同其他動畫，主要畫面格動畫也有<xref:System.Windows.Duration>屬性。 除了指定動畫的<xref:System.Windows.Duration>，您必須指定這段期間的哪個部分提供給每個主要畫面格。 您可以透過描述<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>針對每個動畫的主要畫面格。 每個主要畫面格的<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>指定該主要畫面格的結束時。  
  
 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>屬性不會指定多久的關鍵時間播放。 主要畫面格的播放時間量取決於主要畫面格的結束時間、前一個主要畫面格的結束時間，以及動畫的持續期間。 可能指定關鍵時間，做為時間值，而百分比，或做為特殊值<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>或<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>。  
  
 下列清單說明指定關鍵時間的幾種不同方式。  
  
### <a name="timespan-values"></a>TimeSpan 值  
 您可以使用<xref:System.TimeSpan>值來指定<xref:System.Windows.Media.Animation.KeyTime>。 此值應該大於或等於 0，並且小於或等於動畫的持續期間。 下列範例顯示的動畫具有 10 秒的持續期間和四個主要畫面格，其中每個主要畫面格的關鍵時間都是以時間值指定。  
  
-   第一個主要畫面格會在前 3 秒顯示從基底值至 100 的動畫，並且在時間等於 0:0:03 時結束。  
  
-   第二個主要畫面格會從 100 展示動畫至 200。 它會在第一個主要畫面格結束 (時間等於 3 秒) 後開始播放 5 秒，並且在時間等於 0:0:8 時結束。  
  
-   第三個主要畫面格會從 200 展示動畫至 500。 它會在第二個主要畫面格結束 (時間等於 8 秒) 時開始播放 1 秒，並且在時間等於 0:0:9 時結束。  
  
-   第四個主要畫面格會從 500 展示動畫至 600。 它會在第三個主要畫面格結束 (時間等於 9 秒) 時開始播放 1 秒，並且在時間等於 0:0:10 時結束。  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>百分比值  
 百分比值，指定主要畫面格結尾的動畫的某個百分比<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，百分比的指定方式為在數字後面加上 `%` 符號。 在程式碼中，您會使用<xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A>方法並將它傳遞<xref:System.Double>指出的百分比。 值必須大於或等於 0 且小於或等於 100%。 下列範例顯示的動畫具有 10 秒的持續期間和四個主要畫面格，其中每個主要畫面格的關鍵時間都是以百分比指定。  
  
-   第一個主要畫面格會在前 3 秒顯示從基底值至 100 的動畫，並且在時間等於 0:0:3 時結束。  
  
-   第二個主要畫面格會從 100 展示動畫至 200。 它會在第一個主要畫面格結束 (時間等於 3 秒) 後開始播放 5 秒，並且在時間等於 0:0:8 (0.8 * 10 = 8) 時結束。  
  
-   第三個主要畫面格會從 200 展示動畫至 500。 它會在第二個主要畫面格結束 (時間等於 8 秒) 時開始播放 1 秒，並且在時間等於 0:0:9 (0.9 * 10 = 9) 時結束。  
  
-   第四個主要畫面格會從 500 展示動畫至 600。 它會在第三個主要畫面格結束 (時間等於 9 秒) 時開始播放 1 秒，並且在時間等於 0:0:10 (1 * 10 = 10) 時結束。  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>特殊值 Uniform  
 使用<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>逾時要採取相同的時間量的每個主要畫面格。  
  
 A<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>關鍵時間將可用時間平均除以來判斷每個主要畫面格的結束時間的主要畫面格數目。 下列範例顯示的動畫具有 10 秒的持續時間，並指定為索引鍵時間的四個主要畫面格<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>。  
  
-   第一個主要畫面格會在前 2.5 秒顯示從基底值至 100 的動畫，並且在時間等於 0:0:2.5 時結束。  
  
-   第二個主要畫面格會從 100 展示動畫至 200。 它會在第一個主要畫面格結束 (時間等於 2.5 秒) 後開始播放 2.5 秒，並且在時間等於 0:0:5 時結束。  
  
-   第三個主要畫面格會從 200 展示動畫至 500。 它會在第二個主要畫面格結束 (時間等於 5 秒) 時開始播放 2.5 秒，並且在時間等於 0:0:7.5 時結束。  
  
-   第四個主要畫面格會從 500 展示動畫至 600。 它會在第二個主要畫面格結束 (時間等於 7.5 秒) 時開始播放 2.5 秒，並且在時間等於 0:0:1 時結束。  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>特殊值 Paced  
 使用<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>逾時您想要以動畫顯示變的速率。  
  
 A<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>關鍵時間會配置可用的時間，根據每個主要畫面格，以判斷每個畫面格的持續時間的長度。  這樣會使動畫的速度或步調維持不變。  下列範例顯示的動畫具有 10 秒的持續時間，並指定為索引鍵時間的三個主要畫面格<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>。  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 請注意，如果最後一個主要畫面格的關鍵時間<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>或<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>，其解析後的關鍵時間將會設定為 100%。 如果多格動畫中的第一個主要畫面格已設定速度，其解析後的關鍵時間將會設定 0。 (如果主要畫面格集合僅包含單一主要畫面格，而且是已設定速度的主要畫面格，其解析後的關鍵時間將會設定為 100%。)  
  
 單一主要畫面格動畫中的不同主要畫面格可以使用不同的主要畫面格型別。  
  
<a name="combiningkeytimes"></a>   
## <a name="combining-key-times-out-of-order-key-frames"></a>合併關鍵時間、不按順序的主要畫面格  
 您可以使用主要畫面格具有不同<xref:System.Windows.Media.Animation.KeyTime>實值型別，在相同的動畫。 而且，雖然建議您依播放順序加入主要畫面格，但這不是必要的。 動畫和計時系統能夠解析不按順序的主要畫面格。 系統會忽略具有無效關鍵時間的主要畫面格。  
  
 下列清單說明在主要畫面格動畫中，解析主要畫面格關鍵時間的程序。  
  
1. 解決<xref:System.TimeSpan><xref:System.Windows.Media.Animation.KeyTime>值。  
  
2. 決定動畫的「總插補時間」，也就是主要畫面格動畫用於完成向前逐一查看的總時間。  
  
    1.  如果動畫<xref:System.Windows.Media.Animation.Timeline.Duration%2A>不是<xref:System.Windows.Duration.Automatic%2A>或是<xref:System.Windows.Duration.Forever%2A>，總插補時間為動畫的<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性。  
  
    2.  否則，總插補時間是最大<xref:System.TimeSpan><xref:System.Windows.Media.Animation.KeyTime>如果有的話，在其主要畫面中，指定的值。  
  
    3.  否則，總插補時間為 1 秒。  
  
3. 使用總插補時間值來解決<xref:System.Windows.Media.Animation.KeyTimeType.Percent><xref:System.Windows.Media.Animation.KeyTime>值。  
  
4. 如果尚未在先前步驟中解析最後一個主要畫面格，則加以解析。 如果<xref:System.Windows.Media.Animation.KeyTime>之最後一個是主要畫面格<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>或<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>，其解析後的時間將會等於總插補時間。  
  
     如果<xref:System.Windows.Media.Animation.KeyTime>的第一個主要畫面格是<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>這個動畫有多個主要畫面格，在解決和其<xref:System.Windows.Media.Animation.KeyTime>值為零; 如果只有一個主要畫面格並將其<xref:System.Windows.Media.Animation.KeyTime>值是<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>，它會解析成總計插補時間，在上一個步驟中所述。  
  
5. 解析剩餘<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime>值： 每個授與他們為平均共用可用的時間。  在此過程中，無法解析<xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime>值會暫時視為<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime>值，以及取得暫時的解決時間。  
  
6. 解決<xref:System.Windows.Media.Animation.KeyTime>使用的主要畫面格的值未指定關鍵時間，使用主要畫面格宣告最接近解決<xref:System.Windows.Media.Animation.KeyTime>值。  
  
7. 解析剩餘<xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime>值。 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> 使用<xref:System.Windows.Media.Animation.KeyTime>鄰近的值索引鍵來判斷其解析後的時間的畫面格。  這是為了確保動畫的速度維持在此主要畫面格的解析時間。  
  
8. 也就是排序主要畫面格的解決時間 （主索引鍵） 的順序和宣告 （次要索引鍵） 的順序，請使用穩定的排序根據已解析的主要畫面格<xref:System.Windows.Media.Animation.KeyTime>值。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.KeyTime>
- <xref:System.Windows.Media.Animation.KeySpline>
- <xref:System.Windows.Media.Animation.Timeline>
- [主要曲線動畫範例](https://go.microsoft.com/fwlink/?LinkID=160011)
- [主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)
- [動畫概觀](animation-overview.md)
- [分鏡腳本概觀](storyboards-overview.md)
- [主要畫面格操作說明主題](key-frame-animation-how-to-topics.md)
- [計時行為概觀](timing-behaviors-overview.md)
