---
title: 如何在樣式中建立動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: 0b29648bf15f0046adcdee610f9565f7deb24972
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744887"
---
# <a name="how-to-animate-in-a-style"></a><span data-ttu-id="7351e-102">如何在樣式中建立動畫</span><span class="sxs-lookup"><span data-stu-id="7351e-102">How to animate in a style</span></span>

<span data-ttu-id="7351e-103">這個範例示範如何以動畫顯示樣式中的屬性。</span><span class="sxs-lookup"><span data-stu-id="7351e-103">This example shows how to animate properties within a style.</span></span> <span data-ttu-id="7351e-104">在樣式中建立動畫時，只有定義樣式的 framework 元素可以直接作為目標。</span><span class="sxs-lookup"><span data-stu-id="7351e-104">When animating within a style, only the framework element for which the style is defined can be targeted directly.</span></span> <span data-ttu-id="7351e-105">若要以可凍結的物件為目標，您必須從樣式專案的屬性「向下點」。</span><span class="sxs-lookup"><span data-stu-id="7351e-105">To target a freezable object, you must "dot down" from a property of the styled element.</span></span>

<span data-ttu-id="7351e-106">在下列範例中，會在樣式內定義數個動畫，並套用至 <xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="7351e-106">In the following example, several animations are defined within a style and applied to a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="7351e-107">當使用者將滑鼠指標移至按鈕上方時，會重複地從不透明漸淡到部分半透明，然後再次回復。</span><span class="sxs-lookup"><span data-stu-id="7351e-107">When the user moves the mouse over the button, it fades from opaque to partially translucent and back again, repeatedly.</span></span> <span data-ttu-id="7351e-108">當使用者將滑鼠移開按鈕時，它會變成完全不透明。</span><span class="sxs-lookup"><span data-stu-id="7351e-108">When the user moves the mouse off the button, it becomes completely opaque.</span></span> <span data-ttu-id="7351e-109">當按下按鈕時，其背景色彩會從橙色變更為白色，然後再返回一次。</span><span class="sxs-lookup"><span data-stu-id="7351e-109">When the button is clicked, its background color changes from orange to white and back again.</span></span> <span data-ttu-id="7351e-110">因為用來繪製按鈕的 <xref:System.Windows.Media.SolidColorBrush> 無法直接設為目標，所以可以從按鈕的 <xref:System.Windows.Controls.Control.Background%2A> 屬性中向下將來存取它。</span><span class="sxs-lookup"><span data-stu-id="7351e-110">Because the <xref:System.Windows.Media.SolidColorBrush> used to paint the button can't be targeted directly, it is accessed by dotting down from the button's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="7351e-111">範例</span><span class="sxs-lookup"><span data-stu-id="7351e-111">Example</span></span>

[!code-xaml[timingbehaviors_snip#21](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

<span data-ttu-id="7351e-112">請注意，當您在樣式中建立動畫時，可能會以不存在的物件為目標。</span><span class="sxs-lookup"><span data-stu-id="7351e-112">Note that when animating within a style, it's possible to target objects that don't exist.</span></span> <span data-ttu-id="7351e-113">例如，假設您的樣式使用 <xref:System.Windows.Media.SolidColorBrush> 來設定按鈕的 background 屬性，但在某個時間點，會覆寫樣式，而按鈕的背景則是以 <xref:System.Windows.Media.LinearGradientBrush>設定。</span><span class="sxs-lookup"><span data-stu-id="7351e-113">For example, suppose your style uses a <xref:System.Windows.Media.SolidColorBrush> to set a Button's background property, but at some point the style is overridden and the button's background is set with a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="7351e-114">嘗試以動畫顯示 <xref:System.Windows.Media.SolidColorBrush> 不會擲回例外狀況;動畫只會以無訊息模式失敗。</span><span class="sxs-lookup"><span data-stu-id="7351e-114">Trying to animate the <xref:System.Windows.Media.SolidColorBrush> won't throw an exception; the animation will simply fail silently.</span></span>

<span data-ttu-id="7351e-115">如需有關分鏡腳本目標語法的詳細資訊，請參閱分鏡腳本[總覽](storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="7351e-115">For more information about storyboard targeting syntax, see the [Storyboards Overview](storyboards-overview.md).</span></span> <span data-ttu-id="7351e-116">如需動畫的詳細資訊，請參閱[動畫總覽](animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="7351e-116">For more information about animation, see the [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="7351e-117">如需樣式的詳細資訊，請參閱[樣式設定和範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="7351e-117">For more information about styles, see the [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>
