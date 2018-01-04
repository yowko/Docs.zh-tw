---
title: "如何：建立 FrameworkElement 大小的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf31fa1a10748c3c2f6d239d041c72c57a148e1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a><span data-ttu-id="be84f-102">如何：建立 FrameworkElement 大小的動畫</span><span class="sxs-lookup"><span data-stu-id="be84f-102">How to: Animate the Size of a FrameworkElement</span></span>
<span data-ttu-id="be84f-103">若要建立動畫的大小<xref:System.Windows.FrameworkElement>，您可能可以動畫顯示其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性或使用動畫的<xref:System.Windows.Media.ScaleTransform>。</span><span class="sxs-lookup"><span data-stu-id="be84f-103">To animate the size of a <xref:System.Windows.FrameworkElement>, you can either animate its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties or use an animated <xref:System.Windows.Media.ScaleTransform>.</span></span>  
  
 <span data-ttu-id="be84f-104">在下列範例以動畫方式顯示使用這兩種方法的兩個按鈕的大小。</span><span class="sxs-lookup"><span data-stu-id="be84f-104">In the following example animates the size of two buttons using these two approaches.</span></span> <span data-ttu-id="be84f-105">其中一個按鈕重新調整大小的動畫，以其<xref:System.Windows.FrameworkElement.Width%2A>屬性，而另一個會調整大小的動畫<xref:System.Windows.Media.ScaleTransform>套用至其<xref:System.Windows.UIElement.RenderTransform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="be84f-105">One button is resized by animating its <xref:System.Windows.FrameworkElement.Width%2A> property and another is resized by animating a <xref:System.Windows.Media.ScaleTransform> applied to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span> <span data-ttu-id="be84f-106">每個按鈕包含一些文字。</span><span class="sxs-lookup"><span data-stu-id="be84f-106">Each button contains some text.</span></span> <span data-ttu-id="be84f-107">一開始，文字會出現相同的兩個按鈕，但是調整按鈕的大小，因為在第二個按鈕的文字會失真。</span><span class="sxs-lookup"><span data-stu-id="be84f-107">Initially, the text appears the same in both buttons, but as the buttons are resized, the text in the second button becomes distorted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be84f-108">範例</span><span class="sxs-lookup"><span data-stu-id="be84f-108">Example</span></span>  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 <span data-ttu-id="be84f-109">當您轉換的項目時，會轉換整個項目和其內容。</span><span class="sxs-lookup"><span data-stu-id="be84f-109">When you transform an element, the entire element and its contents are transformed.</span></span> <span data-ttu-id="be84f-110">當您直接改變的項目，如同第一個按鈕，情況大小項目的內容會不調整大小，除非其大小和位置取決於其父項目的大小。</span><span class="sxs-lookup"><span data-stu-id="be84f-110">When you directly alter the size of an element, as in the case of the first button, the element's contents are not resized unless their size and position depend on the size of their parent element.</span></span>  
  
 <span data-ttu-id="be84f-111">藉由套用至動畫的轉換動畫項目的大小其<xref:System.Windows.UIElement.RenderTransform%2A>屬性可提供更佳的效能比動畫顯示其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>直接管理，因為<xref:System.Windows.UIElement.RenderTransform%2A>屬性不會觸發配置傳遞。</span><span class="sxs-lookup"><span data-stu-id="be84f-111">Animating the size of an element by applying an animated transform to its <xref:System.Windows.UIElement.RenderTransform%2A> property provides better performance than animated its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> directly, because the <xref:System.Windows.UIElement.RenderTransform%2A> property does not trigger a layout pass.</span></span>  
  
 <span data-ttu-id="be84f-112">如需建立屬性動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="be84f-112">For more information about animating properties, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="be84f-113">如需有關轉換的詳細資訊，請參閱[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="be84f-113">For more information about transforms, see the [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>
