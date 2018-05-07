---
title: 如何：建立 FrameworkElement 大小的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
ms.openlocfilehash: 148e3d592e129984bd2f7ac062340c5169e48d30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a>如何：建立 FrameworkElement 大小的動畫
若要建立動畫的大小<xref:System.Windows.FrameworkElement>，您可能可以動畫顯示其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性或使用動畫的<xref:System.Windows.Media.ScaleTransform>。  
  
 在下列範例以動畫方式顯示使用這兩種方法的兩個按鈕的大小。 其中一個按鈕重新調整大小的動畫，以其<xref:System.Windows.FrameworkElement.Width%2A>屬性，而另一個會調整大小的動畫<xref:System.Windows.Media.ScaleTransform>套用至其<xref:System.Windows.UIElement.RenderTransform%2A>屬性。 每個按鈕包含一些文字。 一開始，文字會出現相同的兩個按鈕，但是調整按鈕的大小，因為在第二個按鈕的文字會失真。  
  
## <a name="example"></a>範例  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 當您轉換的項目時，會轉換整個項目和其內容。 當您直接改變的項目，如同第一個按鈕，情況大小項目的內容會不調整大小，除非其大小和位置取決於其父項目的大小。  
  
 藉由套用至動畫的轉換動畫項目的大小其<xref:System.Windows.UIElement.RenderTransform%2A>屬性可提供更佳的效能比動畫顯示其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>直接管理，因為<xref:System.Windows.UIElement.RenderTransform%2A>屬性不會觸發配置傳遞。  
  
 如需建立屬性動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。 如需有關轉換的詳細資訊，請參閱[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)。
