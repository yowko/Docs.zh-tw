---
title: "如何：尋找腳本 | Microsoft Docs"
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
  - "搜尋腳本"
  - "分鏡腳本, 搜尋"
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# 如何：尋找腳本
下列範例示範如何使用 <xref:System.Windows.Media.Animation.Storyboard> 的 <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> 方法，跳到腳本動畫中的任何位置。  
  
## 範例  
 以下是此範例的 XAML 標記。  
  
 [!code-xml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## 範例  
 以下是搭配上述 XAML 程式碼一起使用的程式碼。  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## 請參閱  
 [同步搜尋腳本](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)