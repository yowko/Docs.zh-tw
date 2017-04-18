---
title: "如何：使用腳本控制 MediaElement | Microsoft Docs"
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
  - "控制媒體播放, 使用腳本"
  - "媒體, 使用腳本控制播放"
  - "多媒體, 使用腳本控制媒體播放"
  - "媒體播放, 使用腳本控制"
  - "分鏡腳本, 控制媒體播放"
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：使用腳本控制 MediaElement
本範例說明如何在 <xref:System.Windows.Media.Animation.Storyboard> 中使用 <xref:System.Windows.Media.MediaTimeline> 控制 <xref:System.Windows.Controls.MediaElement>。  
  
## 範例  
 在 <xref:System.Windows.Media.Animation.Storyboard> 中使用 <xref:System.Windows.Media.MediaTimeline> 控制 <xref:System.Windows.Controls.MediaElement> 的執行時間時，功能就與其他 <xref:System.Windows.Media.Animation.Timeline> 物件 \(如動畫\) 完全相同。  例如，<xref:System.Windows.Media.MediaTimeline> 會使用如 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 的 <xref:System.Windows.Media.Animation.Timeline> 屬性，指定何時啟動 <xref:System.Windows.Controls.MediaElement> \(開始播放媒體\)。  它也會使用 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 屬性指定 <xref:System.Windows.Controls.MediaElement> 的作用中時間 \(即播放媒體的持續時間\)。  如需在 <xref:System.Windows.Media.Animation.Storyboard> 使用 <xref:System.Windows.Media.Animation.Timeline> 物件的詳細資訊，請參閱[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
 這個範例顯示如何建立簡單的媒體播放程式，此程式會使用 <xref:System.Windows.Media.MediaTimeline> 控制播放。  這個媒體播放程式有播放、暫停、繼續和停止按鈕。  此外也有 <xref:System.Windows.Controls.Slider> 控制項做為進度列。  
  
 下列範例會建立媒體播放程式的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。  
  
 [!code-xml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 下列範例會建立進度列的功能。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## 請參閱  
 <xref:System.Windows.Controls.MediaElement>   
 <xref:System.Windows.Media.MediaTimeline>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 [控制 MediaElement \(播放、暫停、停止、音量和速度\)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)   
 [腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)   
 [圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)