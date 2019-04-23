---
title: HOW TO：使用快取的項目作為筆刷
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: 78df242c7f00b69e36ea4ab6751f51509d9e2220
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229364"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a>HOW TO：使用快取的項目作為筆刷
使用<xref:System.Windows.Media.BitmapCacheBrush>類別，以有效率地重複使用的快取的項目。 若要快取項目，建立的新執行個體<xref:System.Windows.Media.BitmapCache>類別，並將它指派給項目的<xref:System.Windows.UIElement.CacheMode%2A>屬性。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何重複使用的快取的項目。 快取的項目是<xref:System.Windows.Controls.Image>顯示大型影像的控制項。 <xref:System.Windows.Controls.Image>控制項為點陣圖快取使用<xref:System.Windows.Media.BitmapCache>類別，而快取會重複使用將它指派給<xref:System.Windows.Media.BitmapCacheBrush>。 若要顯示有效重複使用，筆刷會指派給 25 個按鈕的背景。  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [如何：透過快取元素改善轉譯效能](how-to-improve-rendering-performance-by-caching-an-element.md)
