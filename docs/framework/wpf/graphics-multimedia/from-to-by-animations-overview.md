---
title: From-至-By 動畫概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: c1aaaca83b8631a87a8987b9676b53161e821117
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407206"
---
# <a name="fromtoby-animations-overview"></a>From/To/By 動畫概觀
本主題說明如何使用 From/To/By 動畫以動畫顯示相依性屬性。 From/To/By 動畫可建立兩個值之間的轉換。  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該熟悉[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫功能。 如需動畫功能，請參閱 <<c0> [ 動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>什麼是 From/To/By 動畫？  
 From/To/By 動畫是一種<xref:System.Windows.Media.Animation.AnimationTimeline>，建立起始值和結束值之間的轉換。 完成轉換所需的時間長度由<xref:System.Windows.Media.Animation.Timeline.Duration%2A>的動畫。  
  
 您可以套用 From/To/By 動畫所使用的屬性<xref:System.Windows.Media.Animation.Storyboard>標記和程式碼，或使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>在程式碼中的方法。 您也可以使用 by 動畫建立<xref:System.Windows.Media.Animation.AnimationClock>並將它套用至一或多個屬性。 如需套用動畫之不同方法的詳細資訊，請參閱[屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)。  
  
 From/To/By 動畫的目標值不能超過兩個。 如果您所需的動畫會有兩個以上的目標值，請使用主要畫面格動畫。 主要畫面格動畫中所述[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>From/To/By 動畫類型  
 由於動畫會產生屬性值，因此針對不同的屬性類型會有不同的動畫類型。 若要動畫顯示採用的屬性<xref:System.Double>，這類<xref:System.Windows.FrameworkElement.Width%2A>屬性的項目，使用會產生動畫<xref:System.Double>值。 若要動畫顯示採用的屬性<xref:System.Windows.Point>，使用會產生動畫<xref:System.Windows.Point>值，並依此類推。  
  
 From/To/By 動畫類別屬於<xref:System.Windows.Media.Animation>命名空間，並使用下列命名慣例：  
  
 *\<Type>* `Animation`  
  
 其中 *\<Type>* 是該類別建立動畫的值類型。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供下列 From/To/By 動畫類別。  
  
|屬性類型|對應 From/To/By 動畫類別|  
|-------------------|------------------------------------------------|  
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
## <a name="target-values"></a>目標值  
 From/To/By 動畫可建立兩個目標值之間的轉換。 它會指定起始值 (使用<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性) 和結束值 (使用<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性)。 不過，您也可以只指定起始值、目的值或位移值。 在這些情況下，動畫會從以動畫顯示的屬性，取得遺漏的目標值。 下列清單說明指定動畫目標值的不同方式。  
  
-   **起始值**  
  
     使用<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性，當您想要明確指定動畫的起始值。 您可以使用<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>本身，或使用屬性<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>或<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。 如果您只有指定<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性，動畫從該值的基底值的轉換動畫的屬性。  
  
-   **結束值**  
  
     若要指定動畫的結束值，請使用其<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性。 如果您使用<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>本身的屬性，動畫會取得其起始值從動畫顯示屬性，或從另一個套用至相同屬性的動畫的輸出。 您可以使用<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性搭配<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>來明確指定開始和結束值動畫的屬性。  
  
-   **位移值**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性可讓您指定的位移，而非明確啟動或動畫的結束值。 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>動畫的屬性會指定多少動畫所變更的值在其持續期間內。 您可以使用<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性本身，或使用<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性。 如果您只有指定<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性，動畫之屬性的基底值或另一個動畫的輸出，請新增位移的值。  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>使用 From/To/By 值  
 下列各節說明如何使用<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>， <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性一起或分開。  
  
 本節中的範例會每次使用<xref:System.Windows.Media.Animation.DoubleAnimation>，這是一種 From/To/By 動畫來以動畫顯示<xref:System.Windows.FrameworkElement.Width%2A>屬性<xref:System.Windows.Shapes.Rectangle>也就是 10 個裝置獨立像素高和 100 裝置獨立像素寬。  
  
 雖然每個範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>、 From、 To 和 By 屬性的所有 From/To/By 動畫的行為相同。 雖然每個範例會使用<xref:System.Windows.Media.Animation.Storyboard>，您可以使用 From/To/By 動畫以其他方式。 如需詳細資訊，請參閱 <<c0> [ 屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)。  
  
### <a name="fromto"></a>寄件者/收件者  
 當您設定<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>並<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>值放在一起，動畫會從所指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性所指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性。  
  
 下列範例會設定<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>的屬性<xref:System.Windows.Media.Animation.DoubleAnimation>設為 50 及其<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>到 300 之間的屬性。 如此一來，<xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.Shapes.Rectangle>從 50 至 300 動畫顯示。  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>以  
 當您將剛<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性，動畫會從基底值的動畫的屬性，或從先前套用至相同的屬性，為所指定的值至組成動畫輸出<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性。  
  
 (「 組成動畫 」 是指<xref:System.Windows.Media.Animation.ClockState.Active>或是<xref:System.Windows.Media.Animation.ClockState.Filling>先前套用至使用套用目前動畫時，仍在作用中是相同屬性的動畫<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>遞移式行為。)  
  
 下列範例會將剛<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性<xref:System.Windows.Media.Animation.DoubleAnimation>到 300 之間。 指定沒有起始值，因為<xref:System.Windows.Media.Animation.DoubleAnimation>使用的基底值 (100)<xref:System.Windows.FrameworkElement.Width%2A>做為其起始值的屬性。 <xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.Shapes.Rectangle>從 100 至動畫的目標值 300 動畫顯示。  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>By  
 當您將剛<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>動畫的屬性，動畫會從基底值之屬性的動畫顯示，或從該值與所指定的值總和的組成動畫輸出<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。  
  
 下列範例會將剛<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性<xref:System.Windows.Media.Animation.DoubleAnimation>到 300 之間。 因為範例沒有指定起始值，所以<xref:System.Windows.Media.Animation.DoubleAnimation>使用的基底值<xref:System.Windows.FrameworkElement.Width%2A>屬性，100，做為其起始值。 結束值取決於新增<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>動畫，300，其起始值 100: 400 的值。 如此一來，<xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.Shapes.Rectangle>從 100 至 400 動畫顯示。  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>From/By  
 當您設定<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>並<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>動畫的屬性，動畫會從所指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性，以指定之總和的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。  
  
 下列範例會設定<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>的屬性<xref:System.Windows.Media.Animation.DoubleAnimation>設為 50 及其<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>到 300 之間的屬性。 結束值取決於新增<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>300，其起始值 50: 350 動畫的值。 如此一來，<xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.Shapes.Rectangle>從 50 至 350 動畫顯示。  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>從  
 當您指定剛<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>的值為動畫，動畫會從所指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性，以動畫顯示屬性的基底值，或者組成動畫輸出。  
  
 下列範例會將剛<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性<xref:System.Windows.Media.Animation.DoubleAnimation>為 50。 不指定任何結束值，因為<xref:System.Windows.Media.Animation.DoubleAnimation>使用的基底值<xref:System.Windows.FrameworkElement.Width%2A>屬性，100，做為其結束值。 <xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.Shapes.Rectangle>從 50 至基底值的動畫顯示<xref:System.Windows.FrameworkElement.Width%2A>屬性，100。  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>To/By  
 如果您同時設定<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>而<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性的動畫，<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性會被忽略。  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>其他動畫類型  
 From/To/By 動畫不是唯一的動畫類型，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供： 它也提供主要畫面格動畫和路徑動畫。  
  
-   主要畫面格動畫會沿著使用主要畫面格所描繪的任意目的數值以動畫顯示。 如需詳細資訊，請參閱 <<c0> [ 主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
-   路徑動畫會產生輸出值<xref:System.Windows.Media.PathGeometry>。 如需詳細資訊，請參閱 <<c0> [ 路徑動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也可讓您建立自己的自訂動畫類型。 如需詳細資訊，請參閱 <<c0> [ 自訂動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [路徑動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)  
 [自訂動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)  
 [From、To 和 By 動畫目標值範例](https://go.microsoft.com/fwlink/?LinkID=159988)
