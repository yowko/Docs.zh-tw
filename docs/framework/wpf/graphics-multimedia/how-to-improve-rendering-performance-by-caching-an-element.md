---
title: "如何：透過快取項目改善轉譯效能 | Microsoft Docs"
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
  - "BitmapCache [WPF], 改善轉譯效能"
  - "CacheMode [WPF], 改善轉譯效能"
  - "效能 [WPF], 快取項目"
  - "轉譯效能 [WPF], 快取項目"
  - "UIElement [WPF], 快取"
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：透過快取項目改善轉譯效能
使用 <xref:System.Windows.Media.BitmapCache> 類別，改善複雜 <xref:System.Windows.UIElement> 的呈現效能。  若要快取項目，請建立 <xref:System.Windows.Media.BitmapCache> 類別的新執行個體，並將它指派給項目的 <xref:System.Windows.UIElement.CacheMode%2A> 屬性。  您可以在 <xref:System.Windows.Media.BitmapCacheBrush> 中有效率地重複使用 <xref:System.Windows.Media.BitmapCache>。  
  
## 範例  
 下列程式碼範例顯示如何建立複雜項目，並將它快取為點陣圖，以改善在建立項目動畫時的效能。  這個項目是畫布，可以保留具有許多頂點的圖形幾何。  會將具有預設值的 <xref:System.Windows.Media.BitmapCache> 指派給畫布的 <xref:System.Windows.UIElement.CacheMode%2A>，而且動畫會平滑地縮放快取的點陣圖。  
  
 [!code-xml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## 請參閱  
 <xref:System.Windows.Media.BitmapCache>   
 <xref:System.Windows.Media.BitmapCacheBrush>   
 <xref:System.Windows.UIElement.CacheMode%2A>   
 [如何：將快取的項目當做筆刷使用](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)