---
title: "Easing 函式 | Microsoft Docs"
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
  - "將數學公式套用至動畫 [WPF]"
  - "將 easing 函式套用至動畫 [WPF]"
  - "將套用至動畫的數學公式 [WPF]"
  - "動畫 [WPF] 中，實際移動"
  - "easing 函式 [WPF]"
  - "自訂 easing 函式 [WPF]"
  - "easing 函式 [WPF] 定義"
  - "自訂的加/減速函數 [WPF]"
  - "套用動畫 [WPF]"
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Easing 函式
加/減速函數可讓您將自訂的數學公式套用至動畫。 例如，您可以實際上彈或行為，就好像彈簧上的物件。 您可以使用主要畫面格或甚至 From/To/By 動畫來模擬這些效果，但可能要花費相當多的工作，動畫會是較不精確比使用數學公式。  
  
 除了建立您自己自訂的加/減速函數，藉由繼承自<xref:System.Windows.Media.Animation.EasingFunctionBase>，您可以使用數個執行階段所提供的加/減速函數的其中一個來建立通用的效果。  
  
-   <xref:System.Windows.Media.Animation.BackEase>︰ 會稍微撤銷動畫的影片之前在指定的路徑中建立動畫。  
  
-   <xref:System.Windows.Media.Animation.BounceEase>︰ 建立彈跳的效果。  
  
-   <xref:System.Windows.Media.Animation.CircleEase>︰ 建立的動畫加速或減速使用循環函式。  
  
-   <xref:System.Windows.Media.Animation.CubicEase>︰ 建立的動畫加速或減速使用公式*f*( *t*) = *t*<sup>3</sup>。  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>︰ 建立類似彈簧之前休息來回擺動的動畫。  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>︰ 建立的動畫加速或減速使用指數的公式。  
  
-   <xref:System.Windows.Media.Animation.PowerEase>︰ 建立的動畫加速或減速使用公式*f*( *t*) = *t*<sup>p</sup>其中 p 是等於<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性。  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>︰ 建立的動畫加速或減速使用公式*f*( *t*) = *t*<sup>2</sup>。  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>︰ 建立的動畫加速或減速使用公式*f*( *t*) = *t*<sup>4</sup>。  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>︰ 建立的動畫加速或減速使用公式*f*( *t*) = *t*<sup>5</sup>。  
  
-   <xref:System.Windows.Media.Animation.SineEase>︰ 建立的動畫加速或減速使用正弦函數的公式。  
  
 您可以瀏覽下面的範例這些加/減速函式的行為。  
  
 [執行這個範例](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 若要套用至動畫的加/減速函數，使用`EasingFunction`動畫的屬性會指定要套用至動畫的加/減速函數。 下列範例會套用<xref:System.Windows.Media.Animation.BounceEase>加/減速函數來<xref:System.Windows.Media.Animation.DoubleAnimation>建立彈跳的效果。  
  
 [執行這個範例](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 在上述範例中，加/減速函數套用到 From/To/By 動畫。 您也可以套用至主要畫面格動畫的加/減速函數。 下列範例示範如何使用加/減速函數與其相關聯的主要畫面格建立矩形，合約向上，變慢，然後展開向下 （如同下降），然後撞到停駐點的動畫。  
  
 [執行這個範例](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 您可以使用<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>改變加/減速函數運作方式，亦即，屬性變更的動畫的插補。 有三個可能的值，您可以為<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode>︰ 插補遵循加/減速函數相關聯的數學公式。  
  
-   <xref:System.Windows.Media.Animation.EasingMode>︰ 插補如下的輸出減去的加/減速函數相關聯的公式的 100%插補。  
  
-   <xref:System.Windows.Media.Animation.EasingMode>︰ 使用插補<xref:System.Windows.Media.Animation.EasingMode>動畫的前半和<xref:System.Windows.Media.Animation.EasingMode>的後半部。  
  
 下列圖表示範不同的值<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>其中*f*( *x*) 代表動畫的進度和*t*代表時間。  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![BackEase EasingMode 圖形。] (../Image/BackEase_Graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode 圖形。] (../Image/BounceEase_Graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![CircleEase EasingMode 圖形。] (../Image/CircleEase_Graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![CubicEase EasingMode 圖形。] (../Image/CubicEase_Graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![不同加/減速模式圖形的 ElasticEase。] (../Image/ElasticEase_Graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![不同加/減速模式的 ExponentialEase 圖形。] (../Image/ExponentialEase_Graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![不同加/減速模式圖形的 QuarticEase。] (../Image/QuarticEase_Graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![不同加/減速模式圖形的 QuadraticEase](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![不同加/減速模式圖形的 QuarticEase。] (../Image/QuarticEase_Graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![不同加/減速模式圖形的 QuinticEase。] (../Image/QuinticEase_Graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![使用不同 EasingMode 值的 SineEase](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  您可以使用<xref:System.Windows.Media.Animation.PowerEase>建立相同的行為<xref:System.Windows.Media.Animation.CubicEase>， <xref:System.Windows.Media.Animation.QuadraticEase>， <xref:System.Windows.Media.Animation.QuarticEase>，和<xref:System.Windows.Media.Animation.QuinticEase>使用<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性。 例如，如果您想要使用<xref:System.Windows.Media.Animation.PowerEase>替換成<xref:System.Windows.Media.Animation.CubicEase>，指定<xref:System.Windows.Media.Animation.PowerEase.Power%2A>值為 3。  
  
 除了使用加/減速函數包含在執行階段中，您可以建立您自己自訂的加/減速函數，藉由繼承自<xref:System.Windows.Media.Animation.EasingFunctionBase>。 下列範例示範如何建立簡單的自訂 easing 函式。 您可以加入您自己的加/減速函數藉由覆寫的運作方式的數學邏輯<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>方法。  
  
 [執行這個範例](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]