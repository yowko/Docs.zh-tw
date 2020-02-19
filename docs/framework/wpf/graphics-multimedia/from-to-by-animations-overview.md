---
title: 從動畫總覽
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 661c035f55ba1fb550726d75921cd01a72b2eecc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448996"
---
# <a name="fromtoby-animations-overview"></a>From/To/By 動畫概觀
本主題說明如何使用 From/To/By 動畫以動畫顯示相依性屬性。 From/To/By 動畫可建立兩個值之間的轉換。  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Prerequisites  
 若要瞭解本主題，您應該熟悉 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫功能。 如需動畫功能的簡介，請參閱[動畫總覽](animation-overview.md)。  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>什麼是 From/To/By 動畫？  
 From/To/By 動畫是一種 <xref:System.Windows.Media.Animation.AnimationTimeline> 類型，可在起始值和結束值之間建立轉換。 完成轉換所需的時間量取決於該動畫的 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>。  
  
 您可以將 From/To/By 動畫套用至屬性，方法是使用標記和程式碼中的 <xref:System.Windows.Media.Animation.Storyboard>，或在程式碼中使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法。 您也可以使用 From/To/By 動畫來建立 <xref:System.Windows.Media.Animation.AnimationClock>，並將它套用至一或多個屬性。 如需套用動畫之不同方法的詳細資訊，請參閱[屬性動畫技術概觀](property-animation-techniques-overview.md)。  
  
 From/To/By 動畫的目標值不能超過兩個。 如果您所需的動畫會有兩個以上的目標值，請使用主要畫面格動畫。 主要畫面格動畫會在[主要畫面格動畫總覽](key-frame-animations-overview.md)中加以說明。  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>From/To/By 動畫類型  
 由於動畫會產生屬性值，因此針對不同的屬性類型會有不同的動畫類型。 若要以動畫顯示採用 <xref:System.Double>的屬性（例如元素的 <xref:System.Windows.FrameworkElement.Width%2A> 屬性），請使用會產生 <xref:System.Double> 值的動畫。 若要以動畫顯示接受 <xref:System.Windows.Point>的屬性，請使用會產生 <xref:System.Windows.Point> 值的動畫等等。  
  
 From/To/By 動畫類別屬於 <xref:System.Windows.Media.Animation> 命名空間，並使用下列命名慣例：  
  
 *\<類型 >* `Animation`  
  
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
 From/To/By 動畫可建立兩個目標值之間的轉換。 通常會指定起始值（使用 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性加以設定）和結束值（使用 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性加以設定）。 不過，您也可以只指定起始值、目的值或位移值。 在這些情況下，動畫會從以動畫顯示的屬性，取得遺漏的目標值。 下列清單說明指定動畫目標值的不同方式。  
  
- **起始值**  
  
     當您想要明確指定動畫的起始值時，請使用 [<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>] 屬性。 您可以單獨使用 [<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>] 屬性，或搭配 [<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>] 或 [<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>] 屬性。 如果您只指定 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性，動畫會從該值轉換成動畫屬性的基底值。  
  
- **結束值**  
  
     若要指定動畫的結束值，請使用其 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性。 如果您單獨使用 [<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>] 屬性，動畫會從正在進行動畫處理的屬性取得其起始值，或從套用至相同屬性的另一個動畫的輸出中取得。 您可以使用 [<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>] 屬性搭配 [<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>] 屬性，以明確指定動畫的開始和結束值。  
  
- **位移值**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性可讓您指定位移，而不是動畫的明確開始或結束值。 動畫的 [<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>] 屬性會指定動畫在其持續時間內變更值的程度。 您可以使用 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性本身或 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性。 如果您只指定 [<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>] 屬性，動畫會將 [位移] 值新增至屬性的基底值或另一個動畫的輸出。  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>使用 From/To/By 值  
 下列各節說明如何一起或分別使用 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>和 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性。  
  
 本節中的範例會使用 <xref:System.Windows.Media.Animation.DoubleAnimation>，這是 From/To/By 動畫的類型，用來以動畫顯示10個裝置獨立圖元高和100裝置獨立圖元寬的 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 屬性。  
  
 雖然每個範例都使用 <xref:System.Windows.Media.Animation.DoubleAnimation>，但 from、To 和 By 動畫的全部內容都有相同的行為。 雖然這些範例中的每一個都使用 <xref:System.Windows.Media.Animation.Storyboard>，但您可以透過其他方式使用 From/To/By 動畫。 如需詳細資訊，請參閱[屬性動畫技術總覽](property-animation-techniques-overview.md)。  
  
### <a name="fromto"></a>來源/目的地  
 當您同時設定 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 和 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 值時，動畫會從 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性所指定的值，到 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性所指定的值。  
  
 下列範例會將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性設為50，並將其 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性設定為300。 因此，<xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 會從50到300的動畫。  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>至  
 當您只設定 [<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>] 屬性時，動畫會從動畫屬性的基底值進行，或從先前套用至相同屬性的組合動畫的輸出，到 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性所指定的值。  
  
 （「撰寫動畫」是指先前套用至相同屬性的 <xref:System.Windows.Media.Animation.ClockState.Active> 或 <xref:System.Windows.Media.Animation.ClockState.Filling> 動畫，而當目前的動畫是使用 <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> 的遞交行為來套用時，仍會生效）。  
  
 下列範例只會將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 屬性設定為300。 因為沒有指定起始值，所以 <xref:System.Windows.Media.Animation.DoubleAnimation> 會使用 <xref:System.Windows.FrameworkElement.Width%2A> 屬性的基底值（100）做為其起始值。 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 會從100動畫到動畫的目標值300。  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>依據  
 當您只設定動畫的 [<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>] 屬性時，動畫會從正在進行動畫之屬性的基底值進行，或從撰寫動畫的輸出到該值的總和，以及由 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性所指定的值來進行。  
  
 下列範例只會將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性設定為300。 因為此範例不會指定起始值，所以 <xref:System.Windows.Media.Animation.DoubleAnimation> 會使用 <xref:System.Windows.FrameworkElement.Width%2A> 屬性的基底值（100）做為其起始值。 結束值的判斷方式是將動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 值300，加上其起始值100：400。 因此，<xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 會從100到400的動畫。  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>From/By  
 當您設定動畫的 [<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>] 和 [<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>] 屬性時，動畫會從 [<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>] 屬性所指定的值，到 [<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>] 和 [<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>] 屬性的總和所指定的值。  
  
 下列範例會將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性設為50，並將其 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性設定為300。 結束值的判斷方式是將動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 值300，加上其起始值50：350。 因此，<xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 會從50到350的動畫。  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>從  
 當您只指定動畫的 [<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>] 值時，動畫會從 [<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>] 屬性所指定的值，到正在製作動畫之屬性的基底值，或是在撰寫動畫的輸出中進行。  
  
 下列範例只會將 <xref:System.Windows.Media.Animation.DoubleAnimation> 的 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 屬性設定為50。 因為未指定結束值，所以 <xref:System.Windows.Media.Animation.DoubleAnimation> 會使用 <xref:System.Windows.FrameworkElement.Width%2A> 屬性的基底值100做為其結束值。 <xref:System.Windows.Shapes.Rectangle> 的 <xref:System.Windows.FrameworkElement.Width%2A> 會從50動畫到 <xref:System.Windows.FrameworkElement.Width%2A> 屬性100的基底值。  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>To/By  
 如果您同時設定 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 和動畫的 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性，則會忽略 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 屬性。  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>其他動畫類型  
 From/To/By 動畫不是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供的唯一動畫類型：它也提供主要畫面格動畫和路徑動畫。  
  
- 主要畫面格動畫會沿著使用主要畫面格所描繪的任意目的數值以動畫顯示。 如需詳細資訊，請參閱[主要畫面格動畫總覽](key-frame-animations-overview.md)。  
  
- 路徑動畫會從 <xref:System.Windows.Media.PathGeometry>產生輸出值。 如需詳細資訊，請參閱[路徑動畫總覽](path-animations-overview.md)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也可讓您建立自己的自訂動畫類型。 如需詳細資訊，請參閱[自訂動畫總覽](custom-animations-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [動畫概觀](animation-overview.md)
- [分鏡腳本概觀](storyboards-overview.md)
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [路徑動畫概觀](path-animations-overview.md)
- [自訂動畫概觀](custom-animations-overview.md)
- [From、To 和 By 動畫目標值範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
