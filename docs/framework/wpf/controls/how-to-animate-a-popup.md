---
title: "如何：建立快顯功能表的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 276c1a54cfdddcde84c0702f4e84f1dc6174bbda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-popup"></a><span data-ttu-id="354a6-102">如何：建立快顯功能表的動畫</span><span class="sxs-lookup"><span data-stu-id="354a6-102">How to: Animate a Popup</span></span>
<span data-ttu-id="354a6-103">此範例示範兩種方式以動畫方式顯示<xref:System.Windows.Controls.Primitives.Popup>控制項。</span><span class="sxs-lookup"><span data-stu-id="354a6-103">This example shows two ways to animate a <xref:System.Windows.Controls.Primitives.Popup> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="354a6-104">範例</span><span class="sxs-lookup"><span data-stu-id="354a6-104">Example</span></span>  
 <span data-ttu-id="354a6-105">下列範例會設定<xref:System.Windows.Controls.Primitives.PopupAnimation>屬性的值<xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>，這會導致<xref:System.Windows.Controls.Primitives.Popup>"投影片單元 」 時出現。</span><span class="sxs-lookup"><span data-stu-id="354a6-105">The following example sets the <xref:System.Windows.Controls.Primitives.PopupAnimation> property to a value of <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, which causes the <xref:System.Windows.Controls.Primitives.Popup> to "slide-in" when it appears.</span></span>  
  
 <span data-ttu-id="354a6-106">若要旋轉<xref:System.Windows.Controls.Primitives.Popup>，這個範例會將<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>屬性<xref:System.Windows.Controls.Canvas>，這是元素的子元素<xref:System.Windows.Controls.Primitives.Popup>。</span><span class="sxs-lookup"><span data-stu-id="354a6-106">In order to rotate the <xref:System.Windows.Controls.Primitives.Popup>, this example assigns a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property on the <xref:System.Windows.Controls.Canvas>, which is the child element of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  
  
 <span data-ttu-id="354a6-107">正常運作的轉換，則必須設定<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="354a6-107">For the transform to work correctly, the example must set the <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> property to `true`.</span></span> <span data-ttu-id="354a6-108">此外，<xref:System.Windows.FrameworkElement.Margin%2A>上<xref:System.Windows.Controls.Canvas>內容必須指定足夠的空間<xref:System.Windows.Controls.Primitives.Popup>旋轉。</span><span class="sxs-lookup"><span data-stu-id="354a6-108">In addition, the <xref:System.Windows.FrameworkElement.Margin%2A> on the <xref:System.Windows.Controls.Canvas> content must specify enough space for the <xref:System.Windows.Controls.Primitives.Popup> to rotate.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <span data-ttu-id="354a6-109">下列範例會示範如何<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件，就會發生此事件時<xref:System.Windows.Controls.Button>按一下時，觸發程序<xref:System.Windows.Media.Animation.Storyboard>啟動動畫。</span><span class="sxs-lookup"><span data-stu-id="354a6-109">The following example shows how a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which occurs when a <xref:System.Windows.Controls.Button> is clicked, triggers the <xref:System.Windows.Media.Animation.Storyboard> that starts the animation.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a><span data-ttu-id="354a6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="354a6-110">See Also</span></span>  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="354a6-111">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="354a6-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [<span data-ttu-id="354a6-112">快顯功能表概觀</span><span class="sxs-lookup"><span data-stu-id="354a6-112">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)
