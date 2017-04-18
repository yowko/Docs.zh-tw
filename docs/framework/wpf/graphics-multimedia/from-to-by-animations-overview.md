---
title: "From/To/By 動畫概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動畫, From/to/by"
  - "From/to/by 動畫"
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# From/To/By 動畫概觀
本主題說明如何使用 From\/To\/By 動畫建立[相依性屬性](GTMT)的動畫效果。  From\/To\/By 動畫會在兩個值之間建立轉換。  
  
 本主題包含下列章節。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prereq"></a>   
## 必要條件  
 若要了解本主題，您應該熟悉 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫功能。  如需動畫功能的簡介，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
<a name="whatisanimation"></a>   
## 什麼是 From\/To\/By 動畫  
 From\/To\/By 動畫是一種 <xref:System.Windows.Media.Animation.AnimationTimeline>，會在開始值與結束值之間建立轉換。  轉換完成所需的時間是由動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 決定。  
  
 要將 From\/To\/By 動畫套用到屬性，可以在標記和程式碼中使用 <xref:System.Windows.Media.Animation.Storyboard>，或在程式碼中使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法。  您也可以使用 From\/To\/By 動畫建立 <xref:System.Windows.Media.Animation.AnimationClock>，然後將它套用到一個或多個屬性。  如需套用動畫之不同方法的詳細資訊，請參閱[建立屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)。  
  
 From\/To\/By 動畫的目標值不能超過兩個。  若需要有兩個以上目標值的動畫，請使用主要畫面格動畫。  有關主要畫面格動畫的說明，請參閱[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
<a name="animation_types"></a>   
## From\/To\/By 動畫型別  
 由於動畫會產生屬性值，因此屬性型別不同，動畫型別也不同。  如果要讓使用 <xref:System.Double> 的屬性 \(例如項目的 <xref:System.Windows.FrameworkElement.Width%2A> 屬性\) 顯示動畫，請使用會產生 <xref:System.Double> 值的動畫。  如果要讓使用 <xref:System.Windows.Point> 的屬性顯示動畫，請使用會產生 <xref:System.Windows.Point> 值的動畫，依此類推。  
  
 From\/To\/By 動畫類別屬於 <xref:System.Windows.Media.Animation> 命名空間，使用下列命名規範：  
  
 *\<型別\>* `Animation`  
  
 其中 *\<Type\>* 是類別顯示為動畫之值的型別。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供下列 From\/To\/By 動畫類別。  
  
|屬性型別|對應的 From\/To\/By 動畫類別|  
|----------|---------------------------|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimation>|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimation>|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16Animation>|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32Animation>|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64Animation>|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimation>|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimation>|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimation>|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimation>|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimation>|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimation>|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimation>|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimation>|  
  
<a name="anim_values"></a>   
## 目標值  
 From\/To\/By 動畫會在兩個目標值之間建立轉換。  一般會指定開始值 \(使用 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性設定\) 和結束值 \(使用 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性設定\)。  不過，您也可以只指定開始值、目的值或位移 \(Offset\) 值。  在這些情況下，動畫會從顯示為動畫的屬性取得缺少的目標值。  下列清單說明指定動畫目標值的幾種不同方法。  
  
-   **開始值**  
  
     若要明確指定動畫的開始值時，請使用 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性。  您可以單獨使用 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性，或與 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 或 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性一起使用。  如果只指定 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性，動畫會從該值轉換到動畫屬性的基底值。  
  
-   **結束值**  
  
     若要指定動畫的結束值，請使用動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性。  如果單獨使用 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性，動畫會從顯示為動畫的屬性取得開始值，或是套用到相同屬性之其他動畫的輸出取得開始值。  您可以將 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性與 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性一起使用，明確指定動畫的開始和結束值。  
  
-   **位移值**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性可用來指定動畫的位移，而非明確的開始或結束值。  動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性會指定動畫在整個期間相對於某個值的變化。  您可以單獨使用 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性，或與 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性一起使用。  如果只指定 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性，動畫會將位移值加到屬性的基底值或其他動畫的輸出。  
  
<a name="examples"></a>   
## 使用 From\/To\/By 值  
 下列章節描述如何一起或單獨使用 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 和 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性。  
  
 本節的幾個範例都使用 <xref:System.Windows.Media.Animation.DoubleAnimation> \(From\/To\/By 動畫的一種\)，將 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 屬性顯示為動畫，這個矩形的高度為 10 個[與裝置無關的像素](GTMT)，寬度為 100 個[與裝置無關的像素](GTMT)。  
  
 雖然這幾個範例都使用 <xref:System.Windows.Media.Animation.DoubleAnimation>，但所有 From\/To\/By 動畫的 From、To 和 By 屬性的作用完全相同。  儘管這些範例也都使用 <xref:System.Windows.Media.Animation.Storyboard>，不過 From\/To\/By 動畫也有其他用法。  如需詳細資訊，請參閱 [建立屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)。  
  
### From\/To  
 當您同時設定 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 和 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 值時，動畫會從 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性指定的值開始，一直到 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性指定的值為止。  
  
 下列範例會將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性設為 50，並且將 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性設為 300。  因此，<xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 會從 50 到 300 顯示動畫效果。  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### 若要  
 如果只設定 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性，動畫則會從動畫屬性的基底值開始，或從先前套用到相同屬性之組合動畫的輸出開始，一直到 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性指定的值為止。  
  
 \(「組合動畫」是指先前套用到相同屬性的 <xref:System.Windows.Media.Animation.ClockState> 或 <xref:System.Windows.Media.Animation.ClockState> 動畫，當目前的動畫使用 <xref:System.Windows.Media.Animation.HandoffBehavior> 傳遞行為套用時，該動畫仍有作用\)  
  
 下列範例只會將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性設為 300。  由於沒有指定開始值，因此 <xref:System.Windows.Media.Animation.DoubleAnimation> 會使用 <xref:System.Windows.FrameworkElement.Width%2A> 屬性的基底值 \(100\) 做為開始值。  <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 會從 100 開始顯示動畫，一直到動畫的目標值 300 為止。  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### By  
 若只設定動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性，動畫會從顯示為動畫之屬性的基底值開始，或從組合動畫的輸出開始，一直到該值與 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性指定的值相加總和為止。  
  
 下列範例只會將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性設為 300。  由於此範例沒有指定開始值，因此 <xref:System.Windows.Media.Animation.DoubleAnimation> 會使用 <xref:System.Windows.FrameworkElement.Width%2A> 屬性的基底值 100 做為開始值。  結束值則是將動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 值 300 加上開始值 100 所決定，也就是 400。  因此，<xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 會從 100 到 400 顯示動畫效果。  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### From\/By  
 當您設定動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 和 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性時，動畫會從 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性指定的值開始，一直到 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 與 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性相加的總和值為止。  
  
 下列範例會將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性設為 50，並且將 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性設為 300。  結束值則是將動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 值 300 加上開始值 50 所決定，也就是 350。  因此，<xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 會從 50 到 350 顯示動畫效果。  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### From  
 若只指定動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 值，動畫會從 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性指定的值開始，一直到顯示為動畫之屬性的基底值，或到組合動畫的輸出為止。  
  
 下列範例只會將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性設為 50。  由於未指定結束值，因此 <xref:System.Windows.Media.Animation.DoubleAnimation> 會使用 <xref:System.Windows.FrameworkElement.Width%2A> 的基底值 100 做為結束值。  <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 會從 50 開始顯示動畫，一直到 <xref:System.Windows.FrameworkElement.Width%2A> 屬性的基底值 \(100\) 為止。  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### To\/By  
 如果同時設定動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 和 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性，將會忽略 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性。  
  
<a name="otheranimationtypes"></a>   
## 其他動畫型別  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 不只提供 From\/To\/By 一種動畫而已，另外也提供主要畫面格動畫和路徑動畫。  
  
-   主要畫面格動畫會沿著任何數目的目的值顯示動畫，這些目的值是使用主要畫面格指定的。  如需詳細資訊，請參閱 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
-   路徑動畫則會從 <xref:System.Windows.Media.PathGeometry> 產生輸出值。  如需詳細資訊，請參閱 [路徑動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也可讓您建立自訂動畫型別。  如需詳細資訊，請參閱 [自訂動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.Timeline>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [路徑動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)   
 [自訂動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)   
 [From、To 和 By 動畫目標值範例](http://go.microsoft.com/fwlink/?LinkID=159988)