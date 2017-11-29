---
title: "如何：透過快取項目改善轉譯效能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d754d0ed2f3951c39b3eaeae097589adf3510f5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>如何：透過快取項目改善轉譯效能
使用<xref:System.Windows.Media.BitmapCache>類別來改善呈現效能複雜<xref:System.Windows.UIElement>。 若要快取項目，建立的新執行個體<xref:System.Windows.Media.BitmapCache>類別，並將它指派給項目的<xref:System.Windows.UIElement.CacheMode%2A>屬性。 您可以重複使用<xref:System.Windows.Media.BitmapCache>有效率地在<xref:System.Windows.Media.BitmapCacheBrush>。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何建立複雜的項目並快取在稱為點陣圖，進而改善效能時的動畫項目。 元素是保存有許多頂點圖形幾何的畫布。 A<xref:System.Windows.Media.BitmapCache>與預設值指派給<xref:System.Windows.UIElement.CacheMode%2A>畫布範圍，請和動畫顯示的快取點陣圖 smooth 縮放比例。  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [操作說明：將快取的元素當做筆刷使用](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
