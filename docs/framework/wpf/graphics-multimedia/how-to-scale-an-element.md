---
title: 操作說明：縮放元素
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: a383ad84f1db4d937469943092a03517f68777ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187442"
---
# <a name="how-to-scale-an-element"></a>操作說明：縮放元素
此示例演示如何使用<xref:System.Windows.Media.ScaleTransform>縮放元素。  
  
 使用<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性按指定的因數調整元素的大小。 例如，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>值 1.5 將元素拉伸到其原始寬度的 150%。 值<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>0.5 將元素的高度縮小 50%。  
  
 使用<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>屬性指定是比例操作中心的點。 預設情況下，a<xref:System.Windows.Media.ScaleTransform>居中居於與矩形左上角相對應的點 （0，0）。 這具有移動元素的效果，並且也使元素看起來更大，因為當您應用 時<xref:System.Windows.Media.Transform>，您將更改物件所在的座標空間。  
  
 下面的示例使用 將<xref:System.Windows.Media.ScaleTransform>50 乘 50<xref:System.Windows.Shapes.Rectangle>的大小加倍。 和<xref:System.Windows.Media.ScaleTransform>的值為 0（預設值）。 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>  
  
## <a name="example"></a>範例  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 通常，您設置<xref:System.Windows.Media.ScaleTransform.CenterX%2A>並<xref:System.Windows.Media.ScaleTransform.CenterY%2A>設置為縮放的物件的中心：（/2，/2）。<xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A>  
  
 下面的示例顯示了另一<xref:System.Windows.Shapes.Rectangle>個大小加倍的，但是，這<xref:System.Windows.Media.ScaleTransform>兩個 值為<xref:System.Windows.Media.ScaleTransform.CenterX%2A>25，<xref:System.Windows.Media.ScaleTransform.CenterY%2A>對應于矩形的中心。  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 下圖顯示了兩<xref:System.Windows.Media.ScaleTransform>個操作之間的差異。 虛線顯示的是矩形在縮放之前的大小和位置。  
  
 ![採用不同中心點的 2 倍縮放](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
兩個有相同 ScaleX 和 ScaleY 值，但不同中心的 ScaleTransform 作業  
  
 如需完整範例，請參閱 [2D 轉換範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [轉換概觀](transforms-overview.md)
- [如何使用主題](transformations-how-to-topics.md)
