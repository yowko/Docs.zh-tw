---
title: HOW TO：建立反映
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 8d29b29d349e9a5ee76ace72837d67e791c25d51
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353565"
---
# <a name="how-to-create-a-reflection"></a>HOW TO：建立反映
此範例示範如何使用<xref:System.Windows.Media.VisualBrush>來建立反映。 因為<xref:System.Windows.Media.VisualBrush>可以顯示現有的視覺效果，您可以使用這項功能來產生有趣的視覺效果，例如反映與放大。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.VisualBrush>來建立的反映<xref:System.Windows.Controls.Border>，其中包含數個項目。 下圖顯示的是這個範例產生的輸出。  
  
 ![A 反映視覺物件](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
反映後的 Visual 物件  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 完整的範例，其中包含說明如何放大螢幕的部分，以及如何建立反映的範例，請參閱 < [VisualBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160049)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.VisualBrush>
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
