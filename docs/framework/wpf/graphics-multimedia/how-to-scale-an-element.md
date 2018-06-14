---
title: 操作說明：縮放元素
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: f39bb4408e5b61912da30088de7c9f62587bc278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562163"
---
# <a name="how-to-scale-an-element"></a>操作說明：縮放元素
這個範例示範如何使用<xref:System.Windows.Media.ScaleTransform>調整項目。  
  
 使用<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性，以調整元素大小依您指定的比例。 例如，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>值為 1.5 延伸到 150%其原始寬度的項目。 A<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>值為 0.5 壓縮百分之 50 項目的高度。  
  
 使用<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>屬性，以指定的調整規模作業的中心點。 根據預設，<xref:System.Windows.Media.ScaleTransform>會集中在時間點 (0，0)，對應至矩形左上角。 這是移動項目，讓它看起來更大，因為當您將套用的效果<xref:System.Windows.Media.Transform>，變更座標空間存放物件。  
  
 下列範例會使用<xref:System.Windows.Media.ScaleTransform>x 50 50 的大小增加兩倍<xref:System.Windows.Shapes.Rectangle>。 <xref:System.Windows.Media.ScaleTransform>兩個具有值為 0 （預設值）<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>。  
  
## <a name="example"></a>範例  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 通常您設定<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>縮放物件的中央: (<xref:System.Windows.FrameworkElement.Width%2A>/2，  <xref:System.Windows.FrameworkElement.Height%2A> /2)。  
  
 下列範例示範另一個<xref:System.Windows.Shapes.Rectangle>，就會加倍大小; 不過，這<xref:System.Windows.Media.ScaleTransform>兩者中的值為 25<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>，它會對應到中央的矩形。  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 下圖顯示兩者之間的差異<xref:System.Windows.Media.ScaleTransform>作業。 虛線顯示的是矩形在縮放之前的大小和位置。  
  
 ![採用不同中心點的 2 倍縮放](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
兩個有相同 ScaleX 和 ScaleY 值，但不同中心的 ScaleTransform 作業  
  
 如需完整範例，請參閱 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
