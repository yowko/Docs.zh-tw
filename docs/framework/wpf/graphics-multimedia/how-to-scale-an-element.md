---
title: HOW TO：縮放項目
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 6decc10c954b51d64c6045c01f1264df35429862
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358609"
---
# <a name="how-to-scale-an-element"></a>HOW TO：縮放項目
此範例示範如何使用<xref:System.Windows.Media.ScaleTransform>來縮放元素。  
  
 使用<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性所指定的因數調整元素的大小。 比方說，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>的 1.5 倍的值會自動縮放其原始寬度的 150%的項目。 A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 50%的值為 0.5 會縮小的項目的高度。  
  
 使用<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>屬性，以指定的縮放作業中心點。 根據預設，<xref:System.Windows.Media.ScaleTransform>中心點 (0，0)，其對應至矩形左上角。 這具有移動元素同時也使它看起來更大的程式，因為當您將套用的效果<xref:System.Windows.Media.Transform>，變更物件所在的座標空間。  
  
 下列範例會使用<xref:System.Windows.Media.ScaleTransform>x 50 50 大小的兩倍<xref:System.Windows.Shapes.Rectangle>。 <xref:System.Windows.Media.ScaleTransform>具有值為 0 （預設值），同時<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>。  
  
## <a name="example"></a>範例  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 一般而言，您設定<xref:System.Windows.Media.ScaleTransform.CenterX%2A>並<xref:System.Windows.Media.ScaleTransform.CenterY%2A>之物件的縮放中心: (<xref:System.Windows.FrameworkElement.Width%2A>/2，  <xref:System.Windows.FrameworkElement.Height%2A> /2)。  
  
 下列範例示範另一個<xref:System.Windows.Shapes.Rectangle>，會增加一倍的大小; 不過，這<xref:System.Windows.Media.ScaleTransform>兩個具有的值為 25<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>，它會對應至矩形的中心。  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 下圖顯示兩者之間的差異<xref:System.Windows.Media.ScaleTransform>作業。 虛線顯示的是矩形在縮放之前的大小和位置。  
  
 ![採用不同中心點的 2 倍縮放](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
兩個有相同 ScaleX 和 ScaleY 值，但不同中心的 ScaleTransform 作業  
  
 如需完整範例，請參閱 [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [轉換概觀](transforms-overview.md)
- [HOW-TO 主題](transformations-how-to-topics.md)
