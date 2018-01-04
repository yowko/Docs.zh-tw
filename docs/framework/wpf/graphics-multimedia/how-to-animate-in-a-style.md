---
title: "如何：在樣式中建立動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2aabe24b77a9016b5b8119646c80ea84eb73acb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-in-a-style"></a><span data-ttu-id="1adc2-102">如何：在樣式中建立動畫</span><span class="sxs-lookup"><span data-stu-id="1adc2-102">How to: Animate in a Style</span></span>
<span data-ttu-id="1adc2-103">這個範例示範如何建立於樣式中的屬性的動畫。</span><span class="sxs-lookup"><span data-stu-id="1adc2-103">This example shows how to animate properties within a style.</span></span> <span data-ttu-id="1adc2-104">建立動畫時於樣式中，可以直接目標只定義樣式的 framework 元素。</span><span class="sxs-lookup"><span data-stu-id="1adc2-104">When animating within a style, only the framework element for which the style is defined can be targeted directly.</span></span> <span data-ttu-id="1adc2-105">若要凍結的物件，您必須 「 點向下 」 從已設定樣式的元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="1adc2-105">To target a freezable object, you must "dot down" from a property of the styled element.</span></span>  
  
 <span data-ttu-id="1adc2-106">在下列範例中，數個動畫會定義於樣式中，並套用到<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="1adc2-106">In the following example, several animations are defined within a style and applied to a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="1adc2-107">當使用者將滑鼠停留在按鈕時，它從不透明的淡半透明再回復到重複。</span><span class="sxs-lookup"><span data-stu-id="1adc2-107">When the user moves the mouse over the button, it fades from opaque to partially translucent and back again, repeatedly.</span></span> <span data-ttu-id="1adc2-108">當使用者移出按鈕的滑鼠時，它會變成完全不透明。</span><span class="sxs-lookup"><span data-stu-id="1adc2-108">When the user moves the mouse off the button, it becomes completely opaque.</span></span> <span data-ttu-id="1adc2-109">按一下按鈕時，它的背景色彩會從橙色白色並再次變更。</span><span class="sxs-lookup"><span data-stu-id="1adc2-109">When the button is clicked, its background color changes from orange to white and back again.</span></span> <span data-ttu-id="1adc2-110">因為<xref:System.Windows.Media.SolidColorBrush>用來繪製不可直接針對目標 按鈕，存取它從按鈕的向下 dotting<xref:System.Windows.Controls.Control.Background%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="1adc2-110">Because the <xref:System.Windows.Media.SolidColorBrush> used to paint the button can't be targeted directly, it is accessed by dotting down from the button's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1adc2-111">範例</span><span class="sxs-lookup"><span data-stu-id="1adc2-111">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 <span data-ttu-id="1adc2-112">請注意，當動畫樣式，則可能不存在於目標物件。</span><span class="sxs-lookup"><span data-stu-id="1adc2-112">Note that when animating within a style, it's possible to target objects that don't exist.</span></span> <span data-ttu-id="1adc2-113">例如，假設您的風格使用<xref:System.Windows.Media.SolidColorBrush>設定按鈕的背景屬性，但處的樣式會覆寫和按鈕的背景設定<xref:System.Windows.Media.LinearGradientBrush>。</span><span class="sxs-lookup"><span data-stu-id="1adc2-113">For example, suppose your style uses a <xref:System.Windows.Media.SolidColorBrush> to set a Button's background property, but at some point the style is overridden and the button's background is set with a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="1adc2-114">嘗試以動畫顯示<xref:System.Windows.Media.SolidColorBrush>不會擲回的例外狀況，動畫會以無訊息模式失敗。</span><span class="sxs-lookup"><span data-stu-id="1adc2-114">Trying to animate the <xref:System.Windows.Media.SolidColorBrush> won't throw an exception; the animation will simply fail silently.</span></span>  
  
 <span data-ttu-id="1adc2-115">如需有關分鏡腳本目標語法的詳細資訊，請參閱[概觀腳本](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1adc2-115">Fore more information about storyboard targeting syntax, see the [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span> <span data-ttu-id="1adc2-116">如需動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1adc2-116">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="1adc2-117">如需有關樣式的詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。</span><span class="sxs-lookup"><span data-stu-id="1adc2-117">For more information about styles, see the [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>
