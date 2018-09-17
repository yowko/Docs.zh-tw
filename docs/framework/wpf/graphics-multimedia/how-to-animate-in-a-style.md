---
title: 如何以動畫顯示樣式 (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: a455bbfb9defbcf83f7e490f60031917a3b41779
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45742345"
---
# <a name="how-to-animate-in-a-style"></a><span data-ttu-id="99b46-102">如何在樣式中建立動畫</span><span class="sxs-lookup"><span data-stu-id="99b46-102">How to animate in a style</span></span>

<span data-ttu-id="99b46-103">此範例示範如何以動畫顯示樣式內的屬性。</span><span class="sxs-lookup"><span data-stu-id="99b46-103">This example shows how to animate properties within a style.</span></span> <span data-ttu-id="99b46-104">當動畫樣式內，可以直接當做目標只有架構元素可定義樣式。</span><span class="sxs-lookup"><span data-stu-id="99b46-104">When animating within a style, only the framework element for which the style is defined can be targeted directly.</span></span> <span data-ttu-id="99b46-105">若要以 freezable 物件為目標，您必須 「 點向下 」 從該樣式的元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="99b46-105">To target a freezable object, you must "dot down" from a property of the styled element.</span></span>

<span data-ttu-id="99b46-106">在下列範例中，數個動畫的定義於樣式中，並套用至<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="99b46-106">In the following example, several animations are defined within a style and applied to a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="99b46-107">當使用者將滑鼠移至按鈕時，它會逐漸淡化的不透明為半透明再後重複。</span><span class="sxs-lookup"><span data-stu-id="99b46-107">When the user moves the mouse over the button, it fades from opaque to partially translucent and back again, repeatedly.</span></span> <span data-ttu-id="99b46-108">當使用者移出按鈕的滑鼠時，它會變成完全不透明。</span><span class="sxs-lookup"><span data-stu-id="99b46-108">When the user moves the mouse off the button, it becomes completely opaque.</span></span> <span data-ttu-id="99b46-109">按一下按鈕時，則會在從橙色到白色，並再次變更它的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="99b46-109">When the button is clicked, its background color changes from orange to white and back again.</span></span> <span data-ttu-id="99b46-110">因為<xref:System.Windows.Media.SolidColorBrush>用來繪製按鈕無法直接作為目標，存取從按鈕的向下將<xref:System.Windows.Controls.Control.Background%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="99b46-110">Because the <xref:System.Windows.Media.SolidColorBrush> used to paint the button can't be targeted directly, it is accessed by dotting down from the button's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="99b46-111">範例</span><span class="sxs-lookup"><span data-stu-id="99b46-111">Example</span></span>

[!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

<span data-ttu-id="99b46-112">請注意，當動畫樣式內，它可能不存在的目標物件。</span><span class="sxs-lookup"><span data-stu-id="99b46-112">Note that when animating within a style, it's possible to target objects that don't exist.</span></span> <span data-ttu-id="99b46-113">例如，假設會使用您的風格<xref:System.Windows.Media.SolidColorBrush>來設定按鈕的 background 屬性，但在某處的樣式會覆寫，並設定按鈕的背景<xref:System.Windows.Media.LinearGradientBrush>。</span><span class="sxs-lookup"><span data-stu-id="99b46-113">For example, suppose your style uses a <xref:System.Windows.Media.SolidColorBrush> to set a Button's background property, but at some point the style is overridden and the button's background is set with a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="99b46-114">嘗試以動畫顯示<xref:System.Windows.Media.SolidColorBrush>不會擲回例外狀況; 動畫將會以無訊息模式失敗。</span><span class="sxs-lookup"><span data-stu-id="99b46-114">Trying to animate the <xref:System.Windows.Media.SolidColorBrush> won't throw an exception; the animation will simply fail silently.</span></span>

<span data-ttu-id="99b46-115">如需有關分鏡腳本目標語法的詳細資訊，請參閱 <<c0> [ 分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="99b46-115">For more information about storyboard targeting syntax, see the [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span> <span data-ttu-id="99b46-116">如需動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="99b46-116">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="99b46-117">如需有關樣式的詳細資訊，請參閱 <<c0> [ 設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。</span><span class="sxs-lookup"><span data-stu-id="99b46-117">For more information about styles, see the [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>
