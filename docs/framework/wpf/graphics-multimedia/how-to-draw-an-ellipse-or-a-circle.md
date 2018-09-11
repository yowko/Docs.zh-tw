---
title: 如何：繪製橢圓形或圓形
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: ddeada8619d1b6c8970f1efb7cca1bc98773d0c5
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262070"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>如何：繪製橢圓形或圓形
此範例示範如何使用繪製橢圓形和圓形<xref:System.Windows.Shapes.Ellipse>項目。 若要繪製橢圓形，建立<xref:System.Windows.Shapes.Ellipse>項目，並指定其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>。 使用其<xref:System.Windows.Shapes.Shape.Fill%2A>屬性來指定<xref:System.Windows.Media.Brush>，用來繪製橢圓形內部。 使用其<xref:System.Windows.Shapes.Shape.Stroke%2A>屬性來指定<xref:System.Windows.Media.Brush>，用來繪製外框的橢圓形。 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>屬性指定的橢圓形外框粗細。  
  
 若要繪製圓形，請<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>的<xref:System.Windows.Shapes.Ellipse>彼此相等的項目。  
  
 下列範例會繪製四<xref:System.Windows.Shapes.Ellipse>內的項目<xref:System.Windows.Controls.Canvas>。  
  
## <a name="example"></a>範例  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 雖然此範例會使用<xref:System.Windows.Controls.Canvas>包含省略符號，您可以使用 ellipse 項目 （和其他圖形元素） 的任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。  
  
 這個範例屬於較大型的範例;如需完整的範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Shapes.Ellipse>  
 <xref:System.Windows.Shapes.Shape>  
 [圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)
