---
title: "如何：控制 MediaElement (播放、暫停、停止、音量和速度) | Microsoft Docs"
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
  - "控制媒體播放"
  - "媒體, 控制播放"
  - "多媒體, 控制媒體播放"
  - "媒體播放, 控制"
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：控制 MediaElement (播放、暫停、停止、音量和速度)
下列範例示範如何使用 <xref:System.Windows.Controls.MediaElement> 控制媒體的播放。  此範例會建立簡單的媒體播放程式，供您用來播放、暫停、停止並前後快轉媒體，以及調整音量和播放速率。  
  
## 範例  
 下列程式碼會建立 UI。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement> 的 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> 屬性必須設定為 `Manual`，才能夠以互動方式停止、暫停及播放媒體。  
  
 [!code-xml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## 範例  
 下列程式碼會實作範例 UI 控制項的功能。  <xref:System.Windows.Controls.MediaElement.Play%2A>、<xref:System.Windows.Controls.MediaElement.Pause%2A> 和 <xref:System.Windows.Controls.MediaElement.Stop%2A> 方法分別用來播放、暫停及停止媒體。  變更 <xref:System.Windows.Controls.MediaElement> 的 <xref:System.Windows.Controls.MediaElement.Position%2A> 屬性可讓您快轉媒體。  最後，<xref:System.Windows.Controls.MediaElement.Volume%2A> 和 <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> 屬性則是用來調整媒體的音量和播放速度。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## 請參閱  
 [使用腳本控制 MediaElement](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)