---
title: "如何：將快取的項目當做筆刷使用 | Microsoft Docs"
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
  - "BitmapCache [WPF], 使用"
  - "BitmapCacheBrush [WPF], 使用"
  - "快取的項目 [WPF], 當做筆刷使用"
  - "CacheMode [WPF], 使用"
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：將快取的項目當做筆刷使用
使用 <xref:System.Windows.Media.BitmapCacheBrush> 類別，可以有效率地重複使用快取的項目。  若要快取項目，請建立 <xref:System.Windows.Media.BitmapCache> 類別的新執行個體，並將它指派給項目的 <xref:System.Windows.UIElement.CacheMode%2A> 屬性。  
  
## 範例  
 下列程式碼範例顯示如何重複使用快取的項目。  快取的項目是顯示大型影像的 <xref:System.Windows.Controls.Image> 控制項。  使用 <xref:System.Windows.Media.BitmapCache> 類別，可以將 <xref:System.Windows.Controls.Image> 控制項快取為點陣圖，而將快取指派給 <xref:System.Windows.Media.BitmapCacheBrush>，就可以重複使用快取。  筆刷是指派給具有 25 個按鈕的背景，以顯示有效率的重複使用。  
  
 [!code-xml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## 請參閱  
 <xref:System.Windows.Media.BitmapCache>   
 <xref:System.Windows.Media.BitmapCacheBrush>   
 <xref:System.Windows.UIElement.CacheMode%2A>   
 [如何：透過快取項目改善轉譯效能](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)