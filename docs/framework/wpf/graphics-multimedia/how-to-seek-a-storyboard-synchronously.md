---
title: "如何：同步搜尋腳本 | Microsoft Docs"
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
  - "同步搜尋腳本"
  - "分鏡腳本, 同步搜尋"
ms.assetid: 03e06271-a946-4810-88ea-3fb4cfa9e0f1
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：同步搜尋腳本
下列範例顯示如何使用 <xref:System.Windows.Media.Animation.Storyboard> 的 <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> 方法，以同步搜尋腳本動畫中的任何位置。  
  
## 範例  
 以下是範例的 XAML 標記。  
  
 [!code-xml[SeekStoryboard_snip#SeekStoryboardSynchronouslyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml#seekstoryboardsynchronouslyexamplewholepage)]  
  
## 範例  
 以下是使用上面 XAML 程式碼的程式碼。  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml.cs#seekstoryboardsynchronouslycodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardSynchronouslyExample.xaml.vb#seekstoryboardsynchronouslycodebehindexamplewholepage)]