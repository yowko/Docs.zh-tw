---
title: "如何：使用 VideoDrawing 播放媒體 | Microsoft Docs"
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
  - "類別, MediaPlayer"
  - "類別, VideoDrawing"
  - "MediaPlayer 類別"
  - "媒體播放"
  - "VideoDrawing 類別"
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：使用 VideoDrawing 播放媒體
若要播放音訊或視訊檔，您可使用 <xref:System.Windows.Media.VideoDrawing> 和 <xref:System.Windows.Media.MediaPlayer>。  載入及播放媒體的方法有兩種。  第一種方法是使用 <xref:System.Windows.Media.MediaPlayer> 和 <xref:System.Windows.Media.VideoDrawing> 本身的功能，第二種方法是建立您自己的 <xref:System.Windows.Media.MediaTimeline> 來搭配 <xref:System.Windows.Media.MediaPlayer> 和 <xref:System.Windows.Media.VideoDrawing>。  
  
> [!NOTE]
>  使用您的應用程式散發媒體時，您不能像處理影像一樣，將媒體檔案當做專案資源來用。  在專案檔中，您必須改為將媒體類型設為 `Content`，並將 `CopyToOutputDirectory` 設為 `PreserveNewest` 或 `Always`。  
  
## 範例  
 下列範例使用 <xref:System.Windows.Media.VideoDrawing> 和 <xref:System.Windows.Media.MediaPlayer> 播放一次視訊檔。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 若要取得媒體的其他計時控制項，請使用 <xref:System.Windows.Media.MediaTimeline> 搭配 <xref:System.Windows.Media.MediaPlayer> 和 <xref:System.Windows.Media.VideoDrawing> 物件。  <xref:System.Windows.Media.MediaTimeline> 可讓您指定視訊是否應重複。  
  
## 範例  
 下列範例使用 <xref:System.Windows.Media.MediaTimeline> 搭配 <xref:System.Windows.Media.MediaPlayer> 和 <xref:System.Windows.Media.VideoDrawing> 物件，來重複播放視訊。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 請注意，當您使用 <xref:System.Windows.Media.MediaTimeline> 時，您是使用 <xref:System.Windows.Media.MediaClock> 的 <xref:System.Windows.Media.Animation.Clock.Controller%2A> 屬性所傳回的互動式 <xref:System.Windows.Media.Animation.ClockController> 來控制媒體播放，而非使用 <xref:System.Windows.Media.MediaPlayer> 的互動式方法。  
  
## 請參閱  
 <xref:System.Windows.Media.VideoDrawing>   
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)