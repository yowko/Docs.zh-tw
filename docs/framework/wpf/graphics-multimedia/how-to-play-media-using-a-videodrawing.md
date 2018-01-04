---
title: "如何：使用 VideoDrawing 播放媒體"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 773a0a1e2252b3f7154ef218f887be6f56e9995f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-media-using-a-videodrawing"></a>如何：使用 VideoDrawing 播放媒體
若要播放的音訊或視訊檔案，您使用<xref:System.Windows.Media.VideoDrawing>和<xref:System.Windows.Media.MediaPlayer>。 有兩種方法可以載入及播放媒體。 第一個方法是使用<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>本身，和第二個方法是建立您自己<xref:System.Windows.Media.MediaTimeline>搭配<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>。  
  
> [!NOTE]
>  利用您的應用程式散發媒體時，您無法跟散發影像一樣，使用媒體檔案當作專案資源。 在您的專案檔中，您必須改為將媒體類型設定為 `Content`，並將 `CopyToOutputDirectory` 設定為 `PreserveNewest` 或 `Always`。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.VideoDrawing>和<xref:System.Windows.Media.MediaPlayer>播放視訊檔案一次。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 若要取得媒體的詳細計時控制權，請使用<xref:System.Windows.Media.MediaTimeline>與<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>物件。 <xref:System.Windows.Media.MediaTimeline>可讓您指定是否應該重複視訊。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.MediaTimeline>與<xref:System.Windows.Media.MediaPlayer>和<xref:System.Windows.Media.VideoDrawing>重複播放視訊的物件。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 請注意，當您使用<xref:System.Windows.Media.MediaTimeline>，您會使用互動式<xref:System.Windows.Media.Animation.ClockController>從傳回<xref:System.Windows.Media.Animation.Clock.Controller%2A>屬性<xref:System.Windows.Media.MediaClock>控制媒體播放，而不是互動式方法<xref:System.Windows.Media.MediaPlayer>。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Media.VideoDrawing>  
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
