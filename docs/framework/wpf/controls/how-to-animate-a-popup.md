---
title: 如何：建立快顯功能表的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: 05b84eea7fe983340ebb8c5cdb20ff39eb2f0858
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553750"
---
# <a name="how-to-animate-a-popup"></a>如何：建立快顯功能表的動畫
此範例示範兩種方式以動畫方式顯示<xref:System.Windows.Controls.Primitives.Popup>控制項。  
  
## <a name="example"></a>範例  
 下列範例會設定<xref:System.Windows.Controls.Primitives.PopupAnimation>屬性的值<xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>，這會導致<xref:System.Windows.Controls.Primitives.Popup>"投影片單元 」 時出現。  
  
 若要旋轉<xref:System.Windows.Controls.Primitives.Popup>，這個範例會將<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>屬性<xref:System.Windows.Controls.Canvas>，這是元素的子元素<xref:System.Windows.Controls.Primitives.Popup>。  
  
 正常運作的轉換，則必須設定<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>屬性`true`。 此外，<xref:System.Windows.FrameworkElement.Margin%2A>上<xref:System.Windows.Controls.Canvas>內容必須指定足夠的空間<xref:System.Windows.Controls.Primitives.Popup>旋轉。  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 下列範例會示範如何<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件，就會發生此事件時<xref:System.Windows.Controls.Button>按一下時，觸發程序<xref:System.Windows.Media.Animation.Storyboard>啟動動畫。  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [快顯功能表概觀](../../../../docs/framework/wpf/controls/popup-overview.md)
