---
title: "如何：使用 From、To 和 By 控制動畫 | Microsoft Docs"
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
  - "動畫，從/到/by"
  - "基本動畫"
  - "動畫，加入基本動畫"
  - "From/to/by 動畫"
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用 From、To 和 By 控制動畫
「 From/To/By 」 或 「 基本動畫 」 會建立兩個目標值之間的轉換 (請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)不同類型的動畫的簡介)。 若要設定基本動畫的目標值，使用其<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>，<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。  下表摘要說明如何<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>，<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性可能一起或分開來決定動畫的目標值。  
  
|指定的屬性|產生的行為|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|動畫會從指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性動畫之屬性的基底值或前一個動畫的輸出值，視前一個動畫的設定方式而定。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> and                              <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|動畫會從指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性所指定的值為<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> and                              <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|動畫會從指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性指定的總和值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|從動畫的屬性的基底值的動畫開始進展或前一個動畫的輸出所指定的值的值<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|動畫會從動畫之屬性的基底值或前一個動畫輸出值，該值與所指定的值的總和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。|  
  
> [!NOTE]
>  無法同時設定<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>上相同的動畫屬性。  
  
 若要使用其他插補方法，或建立兩個以上的目標值之間的動畫，使用主要畫面格動畫。 請參閱[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)如需詳細資訊。  
  
 將多個動畫套用至單一屬性的相關資訊，請參閱[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
 下列範例將說明不同設定的效果<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>，<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>動畫的屬性。  
  
## <a name="example"></a>範例  
 [!code-xml[BasicAnimations_snippet#AnimationTargetValuesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>另請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [From、 To 和動畫目標值範例](http://go.microsoft.com/fwlink/?LinkID=159988)