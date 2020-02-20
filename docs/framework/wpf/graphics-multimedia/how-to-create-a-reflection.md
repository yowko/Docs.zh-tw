---
title: 如何：建立反映
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 8a5ed345c0aa25312bd74799264e1f66ab4554e0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452054"
---
# <a name="how-to-create-a-reflection"></a>如何：建立反映
這個範例會示範如何使用 <xref:System.Windows.Media.VisualBrush> 來建立反映。 因為 <xref:System.Windows.Media.VisualBrush> 可以顯示現有的視覺效果，所以您可以使用這項功能來產生有趣的視覺效果，例如反射和縮放比例。  
  
## <a name="example"></a>範例  
 下列範例會使用 <xref:System.Windows.Media.VisualBrush> 來建立包含數個元素之 <xref:System.Windows.Controls.Border> 的反映。 下圖顯示的是這個範例產生的輸出。  
  
 ![反映後的 Visual 物件](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
反映後的 Visual 物件  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 如需完整的範例，其中包括示範如何放大螢幕各個部分，以及如何建立反射的範例，請參閱[VisualBrush 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.VisualBrush>
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
