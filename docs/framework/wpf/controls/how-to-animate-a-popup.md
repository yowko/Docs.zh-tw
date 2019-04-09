---
title: HOW TO：建立 Popup 的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: b70d9c4cb1bca26a6c77d3a7c50add517ca8ef92
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150107"
---
# <a name="how-to-animate-a-popup"></a>HOW TO：建立 Popup 的動畫
此範例示範兩種方式來以動畫顯示<xref:System.Windows.Controls.Primitives.Popup>控制項。  
  
## <a name="example"></a>範例  
 下列範例會設定<xref:System.Windows.Controls.Primitives.PopupAnimation>屬性的值<xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>，會造成<xref:System.Windows.Controls.Primitives.Popup>為"投影片-in"出現時。  
  
 才可輪<xref:System.Windows.Controls.Primitives.Popup>，這個範例會將<xref:System.Windows.Media.RotateTransform>要<xref:System.Windows.UIElement.RenderTransform%2A>上的屬性<xref:System.Windows.Controls.Canvas>，這是子項目<xref:System.Windows.Controls.Primitives.Popup>。  
  
 必須設定才能正確轉換範例<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>屬性設`true`。 颾魤 ㄛ<xref:System.Windows.FrameworkElement.Margin%2A>上<xref:System.Windows.Controls.Canvas>內容必須指定足夠的空間<xref:System.Windows.Controls.Primitives.Popup>旋轉。  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 下列範例示範如何<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件，就會發生這個事件時<xref:System.Windows.Controls.Button>按一下時，觸發程序<xref:System.Windows.Media.Animation.Storyboard>開始動畫。  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Controls.Primitives.BulletDecorator>
- <xref:System.Windows.Media.RotateTransform>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Controls.Primitives.Popup>
- [HOW TO 主題](popup-how-to-topics.md)
- [快顯功能表概觀](popup-overview.md)
