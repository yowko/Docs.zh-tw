---
title: 如何：建立項目或筆刷不透明效果的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: 549d3eab0d6d75403e962eeb146be8d7995cc931
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421798"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a><span data-ttu-id="6eaa5-102">如何：建立項目或筆刷不透明效果的動畫</span><span class="sxs-lookup"><span data-stu-id="6eaa5-102">How to: Animate the Opacity of an Element or Brush</span></span>
<span data-ttu-id="6eaa5-103">若要讓架構元素淡出畫面，您可以以動畫顯示其<xref:System.Windows.UIElement.Opacity%2A>屬性，或者您可以建立動畫<xref:System.Windows.Media.Brush.Opacity%2A>屬性<xref:System.Windows.Media.Brush>（或筆刷） 用來繪製它。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-103">To make a framework element fade in and out of view, you can animate its <xref:System.Windows.UIElement.Opacity%2A> property or you can animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Brush> (or brushes) used to paint it.</span></span> <span data-ttu-id="6eaa5-104">建立的項目不透明度動畫可讓和其子系淡出畫面，但以動畫顯示筆刷，用來繪製項目可讓您更謹慎選擇哪些項目的部分淡。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-104">Animating the element's opacity makes it and its children fade in and out of view, but animating the brush used to paint the element enables you to be more selective about which portion of the element fades.</span></span> <span data-ttu-id="6eaa5-105">例如，您無法以動畫顯示用來繪製按鈕背景的筆刷的不透明度。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-105">For example, you could animate the opacity of a brush used to paint a button's background.</span></span> <span data-ttu-id="6eaa5-106">這會導致按鈕的背景淡出放大檢視，同時保留它的文字完全不透明。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-106">This would cause the button's background to fade in and out of view, while leaving its text fully opaque.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6eaa5-107">建立動畫<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.Brush>透過以動畫顯示的效能優點<xref:System.Windows.UIElement.Opacity%2A>元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-107">Animating the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.Brush> provides performance benefits over animating the <xref:System.Windows.UIElement.Opacity%2A> property of an element.</span></span>  
  
 <span data-ttu-id="6eaa5-108">在下列範例中，兩個按鈕會使它們淡動畫效果。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-108">In the following example, two buttons are animated so that they fade in and out of view.</span></span> <span data-ttu-id="6eaa5-109">第一個的不透明度<xref:System.Windows.Controls.Button>從以動畫顯示`1.0`要`0.0`透過<xref:System.Windows.Media.Animation.Timeline.Duration%2A>五秒。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-109">The Opacity of the first <xref:System.Windows.Controls.Button> is animated from `1.0` to `0.0` over a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> of five seconds.</span></span> <span data-ttu-id="6eaa5-110">第二個按鈕也以動畫顯示，但 SolidColorBrush 的不透明度會用來繪製其<xref:System.Windows.Controls.Control.Background%2A>動畫而不是整個按鈕的不透明度。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-110">The second button is also animated, but the Opacity of the SolidColorBrush used to paint its <xref:System.Windows.Controls.Control.Background%2A> is animated rather than the opacity of the entire button.</span></span> <span data-ttu-id="6eaa5-111">執行範例時，第一個按鈕完全淡，而第二個按鈕的背景淡。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-111">When the example is run, the first button completely fades in and out of view, while only the background of the second button fades in and out of view.</span></span> <span data-ttu-id="6eaa5-112">其文字和框線保持完全不透明。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-112">Its text and border remain fully opaque.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6eaa5-113">範例</span><span class="sxs-lookup"><span data-stu-id="6eaa5-113">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 <span data-ttu-id="6eaa5-114">此範例中，已省略的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-114">Code has been omitted from this example.</span></span> <span data-ttu-id="6eaa5-115">完整的範例也會示範如何以動畫顯示的不透明度<xref:System.Windows.Media.Color>內<xref:System.Windows.Media.LinearGradientBrush>。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-115">The full sample also shows how to animate the opacity of a <xref:System.Windows.Media.Color> within a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="6eaa5-116">如需完整的範例，請參閱[建立項目範例的不透明度動畫](https://go.microsoft.com/fwlink/?LinkID=159968)。</span><span class="sxs-lookup"><span data-stu-id="6eaa5-116">For the full sample, see the [Animating the Opacity of an Element Sample](https://go.microsoft.com/fwlink/?LinkID=159968).</span></span>
