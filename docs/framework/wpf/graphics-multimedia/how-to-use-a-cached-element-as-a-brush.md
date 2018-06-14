---
title: 如何：將快取的項目當做筆刷使用
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: c43c4ecbefe99d6e38766705378d85d92ecc5729
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561520"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a>如何：將快取的項目當做筆刷使用
使用<xref:System.Windows.Media.BitmapCacheBrush>有效率地重複使用快取之元素的類別。 若要快取項目，建立的新執行個體<xref:System.Windows.Media.BitmapCache>類別，並將它指派給項目的<xref:System.Windows.UIElement.CacheMode%2A>屬性。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何重複使用快取的項目。 快取項目，則<xref:System.Windows.Controls.Image>顯示大型影像的控制項。 <xref:System.Windows.Controls.Image>控制項使用快取為點陣圖<xref:System.Windows.Media.BitmapCache>類別和快取會重複使用所指派到<xref:System.Windows.Media.BitmapCacheBrush>。 筆刷顯示有效率地重複使用指派給 25 個按鈕的背景。  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [操作說明：透過快取元素改善轉譯效能](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
