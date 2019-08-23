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
ms.openlocfilehash: 72118711dfd40ad8c665157e09f01c60085db903
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965738"
---
# <a name="easing-functions"></a>Easing 函式
Easing 函式可讓您將自訂的數學公式套用至動畫。 例如，您可能想要物件實際表現出反彈或像是在彈簧上一樣。 您可以使用主要畫面格或甚至 From/To/By 動畫來模擬這些效果，但所需的工作量可能很大，而且和使用數學公式相比，動畫會較不精確。  
  
 除了藉由繼承<xref:System.Windows.Media.Animation.EasingFunctionBase>來建立自己的自訂緩動函式之外, 您還可以使用執行時間所提供的數個緩動函式之一來建立常見的效果。  
  
- <xref:System.Windows.Media.Animation.BackEase>：先撤銷動畫的動作, 再開始在指定的路徑中建立動畫。  
  
- <xref:System.Windows.Media.Animation.BounceEase>：建立跳動的效果。  
  
- <xref:System.Windows.Media.Animation.CircleEase>：使用迴圈函式建立加速和 (或) 減速的動畫。  
  
- <xref:System.Windows.Media.Animation.CubicEase>：使用公式*f*(*t*) = *t*<sup>3</sup>, 建立加速及/或減速的動畫。  
  
- <xref:System.Windows.Media.Animation.ElasticEase>：建立類似彈簧的動畫, 直到進入 rest 為止。  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>：建立使用指數公式加速和 (或) 減速的動畫。  
  
- <xref:System.Windows.Media.Animation.PowerEase>：使用公式*f*(*t*) = *t*<sup>p</sup> (其中 p 等於<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性), 建立加速及/或減速的動畫。  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>：使用公式*f*(*t*) = *t*<sup>2</sup>, 建立加速及/或減速的動畫。  
  
- <xref:System.Windows.Media.Animation.QuarticEase>：使用公式*f*(*t*) = *t*<sup>4</sup>, 建立加速及/或減速的動畫。  
  
- <xref:System.Windows.Media.Animation.QuinticEase>：使用公式*f*(*t*) = *t*<sup>5</sup>來建立加速及/或減速的動畫。  
  
- <xref:System.Windows.Media.Animation.SineEase>：建立使用正弦公式加速和 (或) 減速的動畫。  
  
 若要將緩動函式套用至動畫, `EasingFunction`請使用動畫的屬性, 指定要套用至動畫的緩時函數。 下列範例會將<xref:System.Windows.Media.Animation.BounceEase>緩動函式套用<xref:System.Windows.Media.Animation.DoubleAnimation>至, 以建立跳動效果。  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 在上述範例中，easing 函式套用至 From/To/By 動畫。 您也可以將這些 easing 函式套用至主要畫面格動畫。 下列範例示範如何使用主要畫面格搭配其相關聯的 easing 函式，來建立收縮向上，減慢，然後向下展開 (如同下降)，然後不斷彈跳直到停止的動畫。  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 您可以使用<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>屬性來改變緩動函式的行為, 也就是變更動畫的插補方式。 有三個可能的值可供<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>您指定:  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>：插補會遵循與緩動函數相關聯的數學公式。  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>：插補會遵循 100% 插補, 減去與緩動函數相關聯的公式輸出。  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>：插補<xref:System.Windows.Media.Animation.EasingMode.EaseIn>會在動畫的前半部和<xref:System.Windows.Media.Animation.EasingMode.EaseOut>後半部使用。  
  
 下列<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>圖表示範不同的值, 其中*f*(*x*) 代表動畫進度, 而*t*代表時間。  
  
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
  
 ![包含不同加/減速模式圖形的 QuadraticEase。](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![包含不同加/減速模式圖形的 QuarticEase。](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![包含不同加/減速模式圖形的 QuinticEase。](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![使用不同 EasingMode 值的 SineEase](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
> 您可以使用<xref:System.Windows.Media.Animation.PowerEase>來建立與<xref:System.Windows.Media.Animation.CubicEase>、、 <xref:System.Windows.Media.Animation.QuarticEase>和<xref:System.Windows.Media.Animation.QuinticEase>相同<xref:System.Windows.Media.Animation.QuadraticEase>的行為, 方法是使用<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性。 例如, 如果您想要使用<xref:System.Windows.Media.Animation.PowerEase>替代的<xref:System.Windows.Media.Animation.CubicEase>, 請指定<xref:System.Windows.Media.Animation.PowerEase.Power%2A>值3。  
  
 除了使用執行時間中包含的緩動函式之外, 您還可以藉由繼承<xref:System.Windows.Media.Animation.EasingFunctionBase>來建立自己的自訂緩動函數。 下列範例將示範如何建立簡單的自訂 easing 函式。 您可以藉由覆寫<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>方法來新增您自己的數學邏輯, 以瞭解緩時函數的行為方式。   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
