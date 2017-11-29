---
title: "Easing 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 198ec8b8cb0b27e009f01f8e60a47e8086a7dbc7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="easing-functions"></a>Easing 函式
Easing 函式可讓您將自訂的數學公式套用至動畫。 例如，您可能想要物件實際表現出反彈或像是在彈簧上一樣。 您可以使用主要畫面格或甚至 From/To/By 動畫來模擬這些效果，但所需的工作量可能很大，而且和使用數學公式相比，動畫會較不精確。  
  
 除了繼承以建立您自己自訂的 easing 函式從<xref:System.Windows.Media.Animation.EasingFunctionBase>，您可以使用其中一個執行階段提供的幾個 easing 函式來建立通用的效果。  
  
-   <xref:System.Windows.Media.Animation.BackEase>： 會撤銷動畫的動畫看的起來稍有後，才開始以動畫方式顯示在指定的路徑。  
  
-   <xref:System.Windows.Media.Animation.BounceEase>： 建立彈跳的效果。  
  
-   <xref:System.Windows.Media.Animation.CircleEase>： 建立的動畫加速或減速使用循環函式。  
  
-   <xref:System.Windows.Media.Animation.CubicEase>： 建立的動畫加速或減速使用公式*f*(*t*) = *t*<sup>3</sup>。  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>： 建立類似 spring，直到到達貼齊來回擺動的動畫。  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>： 建立的動畫加速或減速使用指數的公式。  
  
-   <xref:System.Windows.Media.Animation.PowerEase>： 建立的動畫加速或減速使用公式*f*(*t*) = *t*<sup>p</sup> p 等於<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性。  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>： 建立的動畫加速或減速使用公式*f*(*t*) = *t*<sup>2</sup>。  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>： 建立的動畫加速或減速使用公式*f*(*t*) = *t*<sup>4</sup>。  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>： 建立的動畫加速或減速使用公式*f*(*t*) = *t*<sup>5</sup>。  
  
-   <xref:System.Windows.Media.Animation.SineEase>： 建立的動畫加速或減速使用正弦的公式。  
  
 您可以使用下列範例來探索這些 easing 函式的行為。  
  
 [執行這個範例](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 若要套用至動畫的 easing 函式，使用`EasingFunction`動畫屬性指定要套用至動畫的 easing 函式。 下列範例會套用<xref:System.Windows.Media.Animation.BounceEase>easing 函式可<xref:System.Windows.Media.Animation.DoubleAnimation>建立彈跳的效果。  
  
 [執行這個範例](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 在上述範例中，easing 函式套用至 From/To/By 動畫。 您也可以將這些 easing 函式套用至主要畫面格動畫。 下列範例示範如何使用主要畫面格搭配其相關聯的 easing 函式，來建立收縮向上，減慢，然後向下展開 (如同下降)，然後不斷彈跳直到停止的動畫。  
  
 [執行這個範例](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 您可以使用<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>改變 easing 函式的行為，亦即，屬性變更動畫的插補。 有三個可能的值，您可以提供<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseIn>： 插補遵循 easing 函式相關聯的數學公式。  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseOut>： 插補如下輸出減去 easing 函式相關聯的公式的 100%插補。  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>： 使用插補<xref:System.Windows.Media.Animation.EasingMode.EaseIn>前半的動畫和<xref:System.Windows.Media.Animation.EasingMode.EaseOut>第二個半。  
  
 下列圖表示範不同的值<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>其中*f*(*x*) 表示的動畫進度和*t*代表時間。  
  
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
>  您可以使用<xref:System.Windows.Media.Animation.PowerEase>建立相同的行為<xref:System.Windows.Media.Animation.CubicEase>， <xref:System.Windows.Media.Animation.QuadraticEase>， <xref:System.Windows.Media.Animation.QuarticEase>，和<xref:System.Windows.Media.Animation.QuinticEase>使用<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性。 例如，如果您想要使用<xref:System.Windows.Media.Animation.PowerEase>替換<xref:System.Windows.Media.Animation.CubicEase>，指定<xref:System.Windows.Media.Animation.PowerEase.Power%2A>值為 3。  
  
 除了使用加/減速函數包含在執行階段中，您可以建立您自己自訂的加/減速函數透過繼承自<xref:System.Windows.Media.Animation.EasingFunctionBase>。 下列範例將示範如何建立簡單的自訂 easing 函式。 您可以加入您自己的 easing 函式藉由覆寫的操作方式的數學邏輯<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>方法。  
  
 [執行這個範例](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
