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
ms.openlocfilehash: 038d9423ddae6f16165ed0618beab8391c462ac9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461705"
---
# <a name="easing-functions"></a>Easing 函式
Easing 函式可讓您將自訂的數學公式套用至動畫。 例如，您可能想要物件實際表現出反彈或像是在彈簧上一樣。 您可以使用主要畫面格或甚至 From/To/By 動畫來模擬這些效果，但所需的工作量可能很大，而且和使用數學公式相比，動畫會較不精確。  
  
 除了建立您自己自訂的 easing 函式，藉由繼承自<xref:System.Windows.Media.Animation.EasingFunctionBase>，您可以使用其中一個執行階段所提供的數個 easing 函式來建立常見效果。  
  
-   <xref:System.Windows.Media.Animation.BackEase>： 會撤銷動畫的動作稍有之前就會開始在指示的路徑中建立動畫。  
  
-   <xref:System.Windows.Media.Animation.BounceEase>： 建立彈跳效果。  
  
-   <xref:System.Windows.Media.Animation.CircleEase>： 建立加速和/或減速使用循環函式的動畫。  
  
-   <xref:System.Windows.Media.Animation.CubicEase>： 建立加速和/或減速使用公式的動畫*f*(*t*) = *t*<sup>3</sup>。  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>： 建立類似彈簧來回擺動直到來回的動畫。  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>： 建立加速和/或減速使用指數公式的動畫。  
  
-   <xref:System.Windows.Media.Animation.PowerEase>： 建立加速和/或減速使用公式的動畫*f*(*t*) = *t*<sup>p</sup>其中 p 等於<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性。  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>： 建立加速和/或減速使用公式的動畫*f*(*t*) = *t*<sup>2</sup>。  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>： 建立加速和/或減速使用公式的動畫*f*(*t*) = *t*<sup>4</sup>。  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>： 建立加速和/或減速使用公式的動畫*f*(*t*) = *t*<sup>5</sup>。  
  
-   <xref:System.Windows.Media.Animation.SineEase>： 建立加速和/或減速使用正弦公式的動畫。  
  
 若要套用至動畫的 easing 函式，使用`EasingFunction`動畫的屬性會指定要套用至動畫的 easing 函式。 下列範例會套用<xref:System.Windows.Media.Animation.BounceEase>easing 函式以<xref:System.Windows.Media.Animation.DoubleAnimation>建立彈跳效果。  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 在上述範例中，easing 函式套用至 From/To/By 動畫。 您也可以將這些 easing 函式套用至主要畫面格動畫。 下列範例示範如何使用主要畫面格搭配其相關聯的 easing 函式，來建立收縮向上，減慢，然後向下展開 (如同下降)，然後不斷彈跳直到停止的動畫。  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 您可以使用<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>屬性來改變 easing 函式的運作方式，也就是變更動畫插入的方式。 有三個可能的值，您可以為<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseIn>： 插補會遵循相關聯的 easing 函式的數學公式。  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseOut>： 插補會遵循 100%插補減去輸出相關聯的 easing 函式的公式。  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>︰ 內插補點會使用<xref:System.Windows.Media.Animation.EasingMode.EaseIn>動畫的前半和<xref:System.Windows.Media.Animation.EasingMode.EaseOut>的後半部。  
  
 下圖示範不同的值<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>何處*f*(*x*) 代表動畫進度並*t*代表時間。  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![BackEase EasingMode 圖形。](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode 圖形。](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![CircleEase EasingMode 圖形。](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![CubicEase EasingMode 圖形。](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![包含不同加/減速模式圖形的 ElasticEase。](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![不同加/減速模式的 ExponentialEase 圖形。](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![包含不同加/減速模式圖形的 QuarticEase。](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![包含不同加/減速模式圖形的 QuadraticEase。](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![包含不同加/減速模式圖形的 QuarticEase。](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![包含不同加/減速模式圖形的 QuinticEase。](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![使用不同 EasingMode 值的 SineEase](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  您可以使用<xref:System.Windows.Media.Animation.PowerEase>來建立相同的行為<xref:System.Windows.Media.Animation.CubicEase>， <xref:System.Windows.Media.Animation.QuadraticEase>， <xref:System.Windows.Media.Animation.QuarticEase>，並<xref:System.Windows.Media.Animation.QuinticEase>使用<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性。 例如，如果您想要<xref:System.Windows.Media.Animation.PowerEase>來替代<xref:System.Windows.Media.Animation.CubicEase>，指定<xref:System.Windows.Media.Animation.PowerEase.Power%2A>3 的值。  
  
 除了使用包含在執行階段的 easing 函式，您可以建立您自己自訂的 easing 函式，藉由繼承自<xref:System.Windows.Media.Animation.EasingFunctionBase>。 下列範例將示範如何建立簡單的自訂 easing 函式。 您可以新增您自己的 easing 函式藉由覆寫的運作方式的數學邏輯<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>方法。   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
