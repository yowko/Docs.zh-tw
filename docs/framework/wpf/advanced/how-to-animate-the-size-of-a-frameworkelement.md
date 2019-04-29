---
title: HOW TO：建立 FrameworkElement 大小的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
ms.openlocfilehash: d1995deec5ab2c9bf405911af43b4d242d599119
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776905"
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a><span data-ttu-id="e89bf-102">HOW TO：建立 FrameworkElement 大小的動畫</span><span class="sxs-lookup"><span data-stu-id="e89bf-102">How to: Animate the Size of a FrameworkElement</span></span>
<span data-ttu-id="e89bf-103">若要動畫顯示的大小<xref:System.Windows.FrameworkElement>，您可能可以動畫顯示其<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>屬性或使用動畫的<xref:System.Windows.Media.ScaleTransform>。</span><span class="sxs-lookup"><span data-stu-id="e89bf-103">To animate the size of a <xref:System.Windows.FrameworkElement>, you can either animate its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties or use an animated <xref:System.Windows.Media.ScaleTransform>.</span></span>  
  
 <span data-ttu-id="e89bf-104">在下列範例會展示動畫使用這兩種方法的兩個按鈕的大小。</span><span class="sxs-lookup"><span data-stu-id="e89bf-104">In the following example animates the size of two buttons using these two approaches.</span></span> <span data-ttu-id="e89bf-105">一個按鈕會調整大小以動畫顯示其<xref:System.Windows.FrameworkElement.Width%2A>屬性，而另一個會調整大小的動畫<xref:System.Windows.Media.ScaleTransform>套用至其<xref:System.Windows.UIElement.RenderTransform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e89bf-105">One button is resized by animating its <xref:System.Windows.FrameworkElement.Width%2A> property and another is resized by animating a <xref:System.Windows.Media.ScaleTransform> applied to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span> <span data-ttu-id="e89bf-106">每個按鈕都包含一些文字。</span><span class="sxs-lookup"><span data-stu-id="e89bf-106">Each button contains some text.</span></span> <span data-ttu-id="e89bf-107">一開始，文字會出現相同的兩個按鈕，但是按鈕會調整大小時，在第二個按鈕的文字會變成扭曲的程度。</span><span class="sxs-lookup"><span data-stu-id="e89bf-107">Initially, the text appears the same in both buttons, but as the buttons are resized, the text in the second button becomes distorted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e89bf-108">範例</span><span class="sxs-lookup"><span data-stu-id="e89bf-108">Example</span></span>  
 [!code-xaml[transformanimations_snip#1](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 <span data-ttu-id="e89bf-109">當您轉換的項目時，會轉換整個項目和其內容。</span><span class="sxs-lookup"><span data-stu-id="e89bf-109">When you transform an element, the entire element and its contents are transformed.</span></span> <span data-ttu-id="e89bf-110">當您直接改變大小的項目，第一個按鈕，為例項目的內容是不會改變，除非其大小和位置取決於其父項目的大小。</span><span class="sxs-lookup"><span data-stu-id="e89bf-110">When you directly alter the size of an element, as in the case of the first button, the element's contents are not resized unless their size and position depend on the size of their parent element.</span></span>  
  
 <span data-ttu-id="e89bf-111">建立項目大小的動畫套用動畫的轉換，以其<xref:System.Windows.UIElement.RenderTransform%2A>屬性會提供更佳的效能比以動畫顯示其<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>直接，因為<xref:System.Windows.UIElement.RenderTransform%2A>屬性不會觸發版面配置階段。</span><span class="sxs-lookup"><span data-stu-id="e89bf-111">Animating the size of an element by applying an animated transform to its <xref:System.Windows.UIElement.RenderTransform%2A> property provides better performance than animated its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> directly, because the <xref:System.Windows.UIElement.RenderTransform%2A> property does not trigger a layout pass.</span></span>  
  
 <span data-ttu-id="e89bf-112">如需有關如何以動畫顯示屬性的詳細資訊，請參閱 <<c0> [ 動畫概觀](../graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e89bf-112">For more information about animating properties, see the [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="e89bf-113">如需有關轉換的詳細資訊，請參閱 <<c0> [ 轉換概觀](../graphics-multimedia/transforms-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e89bf-113">For more information about transforms, see the [Transforms Overview](../graphics-multimedia/transforms-overview.md).</span></span>
