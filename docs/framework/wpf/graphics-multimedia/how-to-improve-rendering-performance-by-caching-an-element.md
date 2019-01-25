---
title: HOW TO：透過快取元素改善轉譯效能
ms.date: 03/30/2017
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
ms.openlocfilehash: 79f427198be370d9cb48cab429906202a62bb72d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647568"
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>HOW TO：透過快取元素改善轉譯效能
使用<xref:System.Windows.Media.BitmapCache>類別來改善轉譯效能複雜<xref:System.Windows.UIElement>。 若要快取項目，建立的新執行個體<xref:System.Windows.Media.BitmapCache>類別，並將它指派給項目的<xref:System.Windows.UIElement.CacheMode%2A>屬性。 您可以重複使用<xref:System.Windows.Media.BitmapCache>有效率地在<xref:System.Windows.Media.BitmapCacheBrush>。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何建立複雜的項目，並加以快取為點陣圖，進而改善效能，當項目以動畫顯示。 元素是包含具有許多頂點的圖形幾何的畫布。 A<xref:System.Windows.Media.BitmapCache>使用預設值指派給<xref:System.Windows.UIElement.CacheMode%2A>畫布範圍，請和動畫顯示的快取的點陣圖 smooth 縮放比例。  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [如何：使用快取項目當做筆刷](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
