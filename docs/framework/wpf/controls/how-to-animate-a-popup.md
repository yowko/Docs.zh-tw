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
# <a name="how-to-animate-a-popup"></a><span data-ttu-id="7f5ec-102">HOW TO：建立 Popup 的動畫</span><span class="sxs-lookup"><span data-stu-id="7f5ec-102">How to: Animate a Popup</span></span>
<span data-ttu-id="7f5ec-103">此範例示範兩種方式來以動畫顯示<xref:System.Windows.Controls.Primitives.Popup>控制項。</span><span class="sxs-lookup"><span data-stu-id="7f5ec-103">This example shows two ways to animate a <xref:System.Windows.Controls.Primitives.Popup> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f5ec-104">範例</span><span class="sxs-lookup"><span data-stu-id="7f5ec-104">Example</span></span>  
 <span data-ttu-id="7f5ec-105">下列範例會設定<xref:System.Windows.Controls.Primitives.PopupAnimation>屬性的值<xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>，會造成<xref:System.Windows.Controls.Primitives.Popup>為"投影片-in"出現時。</span><span class="sxs-lookup"><span data-stu-id="7f5ec-105">The following example sets the <xref:System.Windows.Controls.Primitives.PopupAnimation> property to a value of <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, which causes the <xref:System.Windows.Controls.Primitives.Popup> to "slide-in" when it appears.</span></span>  
  
 <span data-ttu-id="7f5ec-106">才可輪<xref:System.Windows.Controls.Primitives.Popup>，這個範例會將<xref:System.Windows.Media.RotateTransform>要<xref:System.Windows.UIElement.RenderTransform%2A>上的屬性<xref:System.Windows.Controls.Canvas>，這是子項目<xref:System.Windows.Controls.Primitives.Popup>。</span><span class="sxs-lookup"><span data-stu-id="7f5ec-106">In order to rotate the <xref:System.Windows.Controls.Primitives.Popup>, this example assigns a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property on the <xref:System.Windows.Controls.Canvas>, which is the child element of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  
  
 <span data-ttu-id="7f5ec-107">必須設定才能正確轉換範例<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="7f5ec-107">For the transform to work correctly, the example must set the <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> property to `true`.</span></span> <span data-ttu-id="7f5ec-108">颾魤 ㄛ<xref:System.Windows.FrameworkElement.Margin%2A>上<xref:System.Windows.Controls.Canvas>內容必須指定足夠的空間<xref:System.Windows.Controls.Primitives.Popup>旋轉。</span><span class="sxs-lookup"><span data-stu-id="7f5ec-108">In addition, the <xref:System.Windows.FrameworkElement.Margin%2A> on the <xref:System.Windows.Controls.Canvas> content must specify enough space for the <xref:System.Windows.Controls.Primitives.Popup> to rotate.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <span data-ttu-id="7f5ec-109">下列範例示範如何<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件，就會發生這個事件時<xref:System.Windows.Controls.Button>按一下時，觸發程序<xref:System.Windows.Media.Animation.Storyboard>開始動畫。</span><span class="sxs-lookup"><span data-stu-id="7f5ec-109">The following example shows how a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which occurs when a <xref:System.Windows.Controls.Button> is clicked, triggers the <xref:System.Windows.Media.Animation.Storyboard> that starts the animation.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a><span data-ttu-id="7f5ec-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f5ec-110">See also</span></span>

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Controls.Primitives.BulletDecorator>
- <xref:System.Windows.Media.RotateTransform>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="7f5ec-111">HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="7f5ec-111">How-to Topics</span></span>](popup-how-to-topics.md)
- [<span data-ttu-id="7f5ec-112">快顯功能表概觀</span><span class="sxs-lookup"><span data-stu-id="7f5ec-112">Popup Overview</span></span>](popup-overview.md)
