---
title: "如何：以動畫播放媒體 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "多媒體、 以動畫播放"
  - "媒體，以動畫播放"
  - "動畫播放媒體"
  - "以動畫播放媒體"
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：以動畫播放媒體
此範例示範如何同時播放媒體和動畫，使用<xref:System.Windows.Media.MediaTimeline>和<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>在同一個類別<xref:System.Windows.Media.Animation.Storyboard>。  
  
## <a name="example"></a>範例  
 您可以使用一或多個<xref:System.Windows.Media.MediaTimeline>物件<xref:System.Windows.Media.Animation.Storyboard>連同其他<xref:System.Windows.Media.Animation.Timeline>物件，例如動畫。  
  
 下列範例會設定<xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>屬性<xref:System.Windows.Media.Animation.Storyboard>為`Slip`，以指定動畫並不會不進行直到媒體 （在此範例中影片） 進行。 如果播放媒體因為載入時間延遲，可能會需要這項功能。  
  
 [!code-xml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.MediaTimeline>   
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>   
 [How to 主題](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)   
 [腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)