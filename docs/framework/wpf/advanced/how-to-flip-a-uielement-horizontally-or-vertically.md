---
title: 如何：水平或垂直翻轉 UIElement
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 89dcf668f1fe361480dabdab227a35ea40c344a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544391"
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a>如何：水平或垂直翻轉 UIElement
這個範例示範如何使用<xref:System.Windows.Media.ScaleTransform>翻轉<xref:System.Windows.UIElement>水平或垂直。 在此範例中，<xref:System.Windows.Controls.Button>控制項 (一種<xref:System.Windows.UIElement>) 翻轉藉由套用<xref:System.Windows.Media.ScaleTransform>至其<xref:System.Windows.UIElement.RenderTransform%2A>屬性。  
  
## <a name="example"></a>範例  
 下圖顯示要翻轉的按鈕。  
  
 ![不含轉換的按鈕](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")  
若要翻轉 UIElement  
  
 以下顯示的程式碼，建立按鈕。  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a>範例  
 若要水平翻轉的按鈕，建立<xref:System.Windows.Media.ScaleTransform>並設定其<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>屬性設為-1。 套用<xref:System.Windows.Media.ScaleTransform>按鈕<xref:System.Windows.UIElement.RenderTransform%2A>屬性。  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![水平翻轉的按鈕&#40;0，0&#41;](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")  
以後 scaletransform 縮放按鈕  
  
## <a name="example"></a>範例  
 您可以從上圖中看到，已翻轉的按鈕，但它也已移動。 這是因為從其左上角已翻轉的按鈕。 若要就地翻轉的按鈕，您要套用<xref:System.Windows.Media.ScaleTransform>到其中心時，不是其邊角。 輕鬆地套用<xref:System.Windows.Media.ScaleTransform>中心是設定按鈕的按鈕<xref:System.Windows.UIElement.RenderTransformOrigin%2A>屬性為 0.5，0.5。  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![對其中心水平翻轉的按鈕](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")  
按鈕的 RenderTransformOrigin 為 0.5，0.5  
  
## <a name="example"></a>範例  
 若要垂直翻轉的按鈕，設定<xref:System.Windows.Media.ScaleTransform>物件的<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性而非其<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>屬性。  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![對其中心垂直翻轉的按鈕](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")  
垂直翻轉的按鈕  
  
## <a name="see-also"></a>另請參閱  
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
