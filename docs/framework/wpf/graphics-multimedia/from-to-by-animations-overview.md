---
title: 逐個動畫概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 135f01823d374b30f8d4d41762d2267a254f98c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186455"
---
# <a name="fromtoby-animations-overview"></a>From/To/By 動畫概觀
本主題說明如何使用 From/To/By 動畫以動畫顯示相依性屬性。 From/To/By 動畫可建立兩個值之間的轉換。  
  
<a name="prereq"></a>
## <a name="prerequisites"></a>必要條件  
 要理解本主題，您應該熟悉[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動畫功能。 有關動畫功能的簡介，請參閱[動畫概述](animation-overview.md)。  
  
<a name="whatisanimation"></a>
## <a name="what-is-a-fromtoby-animation"></a>什麼是 From/To/By 動畫？  
 From/To/By 動畫是在起始值和<xref:System.Windows.Media.Animation.AnimationTimeline>結束值之間創建過渡的類型。 過渡完成所需的時間由該動畫<xref:System.Windows.Media.Animation.Timeline.Duration%2A>的由該動畫確定。  
  
 可以通過在標記和代碼中使用 或<xref:System.Windows.Media.Animation.Storyboard>在代碼中使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法對屬性應用"從/到/通過"動畫動畫。 您還可以使用"從/到/按動畫"創建 ，<xref:System.Windows.Media.Animation.AnimationClock>並將其應用於一個或多個屬性。 有關應用動畫的不同方法的詳細資訊，請參閱[屬性動畫技術概述](property-animation-techniques-overview.md)。  
  
 From/To/By 動畫的目標值不能超過兩個。 如果您所需的動畫會有兩個以上的目標值，請使用主要畫面格動畫。 關鍵幀動畫在[關鍵幀動畫概述](key-frame-animations-overview.md)中描述。  
  
<a name="animation_types"></a>
## <a name="fromtoby-animation-types"></a>From/To/By 動畫類型  
 由於動畫會產生屬性值，因此針對不同的屬性類型會有不同的動畫類型。 要為採用<xref:System.Double>的屬性（如元素<xref:System.Windows.FrameworkElement.Width%2A>的屬性）設置動畫，請使用生成<xref:System.Double>值的動畫。 要為 採用<xref:System.Windows.Point>的屬性設置動畫，請使用生成<xref:System.Windows.Point>值的動畫，等等。  
  
 從/到/按動畫類屬於<xref:System.Windows.Media.Animation>命名空間，並使用以下命名約定：  
  
 * \<鍵入>*`Animation`  
  
 * \<類型>* 是類動畫的數值型別。  
  
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
 From/To/By 動畫可建立兩個目標值之間的轉換。 通常指定起始值（使用<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性設置它）和結束值（使用 屬性<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>設置）。 不過，您也可以只指定起始值、目的值或位移值。 在這些情況下，動畫會從以動畫顯示的屬性，取得遺漏的目標值。 下列清單說明指定動畫目標值的不同方式。  
  
- **起始值**  
  
     如果要顯式<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>指定動畫的起始值，請使用 該屬性。 您可以自行使用<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>該屬性，也可以使用 或<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A><xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。 如果僅指定該<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性，動畫將從該值轉換為動畫屬性的基值。  
  
- **結束值**  
  
     要指定動畫的結束值，請使用其<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性。 如果本身使用該<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性，動畫將從正在進行動畫處理的屬性或應用於同一屬性的另一個動畫的輸出中獲取其起始值。 可以將 屬性<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>與<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性一起使用，以顯式指定動畫的開始和結束值。  
  
- **位移值**  
  
     屬性<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>使您能夠為動畫指定偏移，而不是顯式起始值或結束值。 動畫<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>的屬性按動畫在其持續時間內更改值的數量指定。 您可以自行使用該<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性，也可以使用 屬性<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>。 如果僅指定該<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性，則動畫會將偏移值添加到屬性的基值或其他動畫的輸出。  
  
<a name="examples"></a>
## <a name="using-fromtoby-values"></a>使用 From/To/By 值  
 以下各節介紹如何一起使用<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>和<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>或單獨使用。  
  
 本節中的示例每個示例都使用<xref:System.Windows.Media.Animation.DoubleAnimation>一個 ，這是一種"從/到/按"動畫，<xref:System.Windows.FrameworkElement.Width%2A>為 10 個設備獨立圖元高和 100 個與設備無關的圖元寬的屬性<xref:System.Windows.Shapes.Rectangle>進行動畫處理。  
  
 儘管每個示例使用<xref:System.Windows.Media.Animation.DoubleAnimation>的 "從"、To 和"按"屬性的所有"從/到/按"動畫的行為相同。 儘管每個示例都使用<xref:System.Windows.Media.Animation.Storyboard>，但可以通過其他方式使用"從/到/按"動畫。 有關詳細資訊，請參閱[屬性動畫技術概述](property-animation-techniques-overview.md)。  
  
### <a name="fromto"></a>寄件者/收件者  
 將<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>和<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>值一起設置時，動畫將從<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性指定的值到<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性指定的值進行。  
  
 下面的示例將 屬性<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A><xref:System.Windows.Media.Animation.DoubleAnimation>設置為 50，其<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性將設置為 300。 因此，的<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.Shapes.Rectangle>動畫從 50 到 300。  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>至  
 僅設置<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性時，動畫將從動畫屬性的基值或以前應用於同一屬性的合成動畫的輸出到<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性指定的值進行。  
  
 （"組合動畫"是指以前應用於使用<xref:System.Windows.Media.Animation.ClockState.Active>移交<xref:System.Windows.Media.Animation.ClockState.Filling>行為應用當前動畫時仍然有效的同一屬性的<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>動畫或動畫。  
  
 下面的示例僅設置 到<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A><xref:System.Windows.Media.Animation.DoubleAnimation>300 的屬性。 由於沒有指定起始值，因此<xref:System.Windows.Media.Animation.DoubleAnimation>使用<xref:System.Windows.FrameworkElement.Width%2A>屬性的基值 （100） 作為其起始值。 的<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.Shapes.Rectangle>動畫從 100 到動畫的目標值 300。  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>依據  
 僅設置動畫<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>的屬性時，動畫將從要動畫的屬性的基值或合成動畫的輸出到該值和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性指定的值的總和。  
  
 下面的示例僅設置 到<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A><xref:System.Windows.Media.Animation.DoubleAnimation>300 的屬性。 由於該示例未指定起始值，因此<xref:System.Windows.Media.Animation.DoubleAnimation>使用<xref:System.Windows.FrameworkElement.Width%2A>屬性 100 的基值作為其起始值。 結束值是通過將動畫 300<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>的值添加到其起始值 100： 400 來確定的。 因此，的<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.Shapes.Rectangle>動畫從 100 到 400。  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>From/By  
 設置 動畫<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>的<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>和 屬性時，動畫將從<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性指定的值到 由<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性的總和指定的值。  
  
 下面的示例將 屬性<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A><xref:System.Windows.Media.Animation.DoubleAnimation>設置為 50，其<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性將設置為 300。 結束值是通過將動畫 300<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>的值添加到其起始值 50：350 來確定的。 因此，的<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.Shapes.Rectangle>動畫從 50 到 350。  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>從  
 僅指定動畫<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>的值時，動畫將從<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性指定的值、正在動畫的屬性的基值或合成動畫的輸出前進。  
  
 下面的示例僅設置 到<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A><xref:System.Windows.Media.Animation.DoubleAnimation>50 的屬性。 由於沒有指定結束值，因此<xref:System.Windows.Media.Animation.DoubleAnimation>使用<xref:System.Windows.FrameworkElement.Width%2A>屬性 100 的基值作為其結束值。 的<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.Shapes.Rectangle>動畫從 50 到<xref:System.Windows.FrameworkElement.Width%2A>屬性的基值 100。  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>To/By  
 如果同時設置<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>動畫和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>動畫的屬性，則將忽略該<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。  
  
<a name="otheranimationtypes"></a>
## <a name="other-animation-types"></a>其他動畫類型  
 "從/到/按"動畫不是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供的唯一動畫類型：它還提供關鍵幀動畫和路徑動畫。  
  
- 主要畫面格動畫會沿著使用主要畫面格所描繪的任意目的數值以動畫顯示。 有關詳細資訊，請參閱[關鍵幀動畫概述](key-frame-animations-overview.md)。  
  
- 路徑動畫從 生成輸出值<xref:System.Windows.Media.PathGeometry>。 有關詳細資訊，請參閱[路徑動畫概述](path-animations-overview.md)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也可讓您建立自己的自訂動畫類型。 有關詳細資訊，請參閱[自訂動畫概述](custom-animations-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [動畫概觀](animation-overview.md)
- [分鏡腳本概觀](storyboards-overview.md)
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [路徑動畫概觀](path-animations-overview.md)
- [自訂動畫概觀](custom-animations-overview.md)
- [From、To 和 By 動畫目標值範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
