---
title: Easing 函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
ms.openlocfilehash: a25bde5098af853c3906a174a189fc35f33f0525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186492"
---
# <a name="easing-functions"></a>Easing 函式
Easing 函式可讓您將自訂的數學公式套用至動畫。 例如，您可能想要物件實際表現出反彈或像是在彈簧上一樣。 您可以使用主要畫面格或甚至 From/To/By 動畫來模擬這些效果，但所需的工作量可能很大，而且和使用數學公式相比，動畫會較不精確。  
  
 除了通過繼承創建自己的自訂緩動函數外<xref:System.Windows.Media.Animation.EasingFunctionBase>，您還可以使用運行時提供的幾個緩動函數之一來創建常見效果。  
  
- <xref:System.Windows.Media.Animation.BackEase>：在動畫開始在指示的路徑中設置動畫之前稍微縮回動畫的運動。  
  
- <xref:System.Windows.Media.Animation.BounceEase>：創建彈跳效果。  
  
- <xref:System.Windows.Media.Animation.CircleEase>：創建使用圓形函數加速和/或減速的動畫。  
  
- <xref:System.Windows.Media.Animation.CubicEase>： 創建使用公式*f*（*t*） = *t*<sup>3</sup>加速和/或減速的動畫。  
  
- <xref:System.Windows.Media.Animation.ElasticEase>：創建類似于彈簧來回擺動的動畫，直到它開始休息。  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>：創建使用指數公式加速和/或減速的動畫。  
  
- <xref:System.Windows.Media.Animation.PowerEase>： 創建使用公式*f*（*t*） = *t*<sup>p</sup>的公式加速和/或減速的動畫<xref:System.Windows.Media.Animation.PowerEase.Power%2A>，其中 p 等於屬性。  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>： 創建使用公式*f*（*t*） = *t*<sup>2</sup>加速和/或減速的動畫。  
  
- <xref:System.Windows.Media.Animation.QuarticEase>： 創建使用公式*f*（*t*） = *t*<sup>4</sup>加速和/或減速的動畫。  
  
- <xref:System.Windows.Media.Animation.QuinticEase>： 創建使用公式*f*（*t*） = *t*<sup>5</sup>加速和/或減速的動畫。  
  
- <xref:System.Windows.Media.Animation.SineEase>：創建使用子項公式加速和/或減速的動畫。  
  
 要將緩動函數應用於動畫，請使用動畫`EasingFunction`的屬性指定要應用於動畫的緩動函數。 下面的示例將<xref:System.Windows.Media.Animation.BounceEase>緩動函數應用於<xref:System.Windows.Media.Animation.DoubleAnimation>創建彈跳效果。  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 在上述範例中，easing 函式套用至 From/To/By 動畫。 您也可以將這些 easing 函式套用至主要畫面格動畫。 下列範例示範如何使用主要畫面格搭配其相關聯的 easing 函式，來建立收縮向上，減慢，然後向下展開 (如同下降)，然後不斷彈跳直到停止的動畫。  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 可以使用 屬性<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>更改緩動函數的特性，即更改動畫插值的方式。 您可以為<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>：  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>：插值遵循與緩動函數關聯的數學公式。  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>：插值遵循 100% 插值減去與緩動函數關聯的公式的輸出。  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>：插值用於<xref:System.Windows.Media.Animation.EasingMode.EaseIn>動畫的上半部分和<xref:System.Windows.Media.Animation.EasingMode.EaseOut>下半場。  
  
 下圖顯示了*f*（*x* <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> ） 表示動畫進度和*t*表示時間的不同值。  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![BackEase EasingMode 圖形。](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode 圖形。](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![CircleEase EasingMode 圖形。](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![CubicEase EasingMode 圖形。](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![包含不同加/減速模式圖形的 ElasticEase。](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![不同加/減速模式的 ExponentialEase 圖形。](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![包含不同加/減速模式圖形的 QuarticEase。](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![具有不同緩動模式的圖形的二次緩動](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![包含不同加/減速模式圖形的 QuarticEase。](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![包含不同加/減速模式圖形的 QuinticEase。](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![使用不同 EasingMode 值的 SineEase](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
> 可以使用 創建<xref:System.Windows.Media.Animation.PowerEase>與<xref:System.Windows.Media.Animation.CubicEase><xref:System.Windows.Media.Animation.QuadraticEase><xref:System.Windows.Media.Animation.QuarticEase>、 和<xref:System.Windows.Media.Animation.QuinticEase>以及 使用 屬性<xref:System.Windows.Media.Animation.PowerEase.Power%2A>相同的行為。 例如，如果要使用<xref:System.Windows.Media.Animation.PowerEase>替換<xref:System.Windows.Media.Animation.CubicEase>，請指定<xref:System.Windows.Media.Animation.PowerEase.Power%2A>值 3。  
  
 除了使用運行時中包含的緩動函數外，還可以通過繼承 來<xref:System.Windows.Media.Animation.EasingFunctionBase>創建自己的自訂緩動函數。 下列範例將示範如何建立簡單的自訂 easing 函式。 您可以添加您自己的數學邏輯，用於緩動函數如何通過重寫<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>方法來運行。
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
