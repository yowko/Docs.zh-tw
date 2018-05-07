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
ms.openlocfilehash: c791dbbe02faaba790c650d482db092702730fa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-reflection"></a>如何：建立反映
這個範例示範如何使用<xref:System.Windows.Media.VisualBrush>來建立反映。 因為<xref:System.Windows.Media.VisualBrush>可顯示現有的 visual，您可以使用這項功能來產生有趣的視覺效果，例如反射和縮放比例。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.VisualBrush>來建立反映的<xref:System.Windows.Controls.Border>，其中包含數個項目。 下圖顯示的是這個範例產生的輸出。  
  
 ![A 反映視覺物件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
反映後的 Visual 物件  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 如需完整的範例中，包括範例，說明如何放大螢幕的部分，以及如何建立反射，請參閱[VisualBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160049)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.VisualBrush>  
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
