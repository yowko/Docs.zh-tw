---
title: HOW TO：使用分鏡腳本建立屬性的動畫後對該屬性進行設定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: 2e1389392c6465ed56b2c71e53b2e3c1947acbe2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188307"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a><span data-ttu-id="97d58-102">HOW TO：使用分鏡腳本建立屬性的動畫後對該屬性進行設定</span><span class="sxs-lookup"><span data-stu-id="97d58-102">How to: Set a Property After Animating It with a Storyboard</span></span>
<span data-ttu-id="97d58-103">在某些情況下，它可能會出現，您就無法變更屬性的值之後已顯示動畫。</span><span class="sxs-lookup"><span data-stu-id="97d58-103">In some cases, it might appear that you can't change the value of a property after it has been animated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97d58-104">範例</span><span class="sxs-lookup"><span data-stu-id="97d58-104">Example</span></span>  
 <span data-ttu-id="97d58-105">在下列範例中，<xref:System.Windows.Media.Animation.Storyboard>用來以動畫顯示的色彩<xref:System.Windows.Media.SolidColorBrush>。</span><span class="sxs-lookup"><span data-stu-id="97d58-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> is used to animate the color of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="97d58-106">按一下按鈕時，就會觸發將分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="97d58-106">The storyboard is triggered when the button is clicked.</span></span> <span data-ttu-id="97d58-107"><xref:System.Windows.Media.Animation.Timeline.Completed>如此，程式會收到通知，處理事件時<xref:System.Windows.Media.Animation.ColorAnimation>完成。</span><span class="sxs-lookup"><span data-stu-id="97d58-107">The <xref:System.Windows.Media.Animation.Timeline.Completed> event is handled so that the program is notified when the <xref:System.Windows.Media.Animation.ColorAnimation> completes.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a><span data-ttu-id="97d58-108">範例</span><span class="sxs-lookup"><span data-stu-id="97d58-108">Example</span></span>  
 <span data-ttu-id="97d58-109">之後<xref:System.Windows.Media.Animation.ColorAnimation>完成時，程式嘗試變更為藍色的筆刷的色彩。</span><span class="sxs-lookup"><span data-stu-id="97d58-109">After the <xref:System.Windows.Media.Animation.ColorAnimation> completes, the program attempts to change the brush's color to blue.</span></span>  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 <span data-ttu-id="97d58-110">先前的程式碼不採取任何動作會出現： 所提供的筆刷維持黃色，也就是值<xref:System.Windows.Media.Animation.ColorAnimation>，以動畫顯示筆刷。</span><span class="sxs-lookup"><span data-stu-id="97d58-110">The previous code doesn't appear to do anything: the brush remains yellow, which is the value supplied by the <xref:System.Windows.Media.Animation.ColorAnimation> that animated the brush.</span></span> <span data-ttu-id="97d58-111">基礎的屬性值 （基底值） 會實際變更為藍色。</span><span class="sxs-lookup"><span data-stu-id="97d58-111">The underlying property value (the base value) is actually changed to blue.</span></span> <span data-ttu-id="97d58-112">不過，有效，或最新狀態，值仍然維持黃色因為<xref:System.Windows.Media.Animation.ColorAnimation>仍然在覆寫基底值。</span><span class="sxs-lookup"><span data-stu-id="97d58-112">However, the effective, or current, value remains yellow because the <xref:System.Windows.Media.Animation.ColorAnimation> is still overriding the base value.</span></span> <span data-ttu-id="97d58-113">如果您想要再次變成有效的值的基底值，您必須停止的動畫屬性的影響。</span><span class="sxs-lookup"><span data-stu-id="97d58-113">If you want the base value to become the effective value again, you must stop the animation from influencing the property.</span></span> <span data-ttu-id="97d58-114">有三種方式，若要使用分鏡腳本動畫：</span><span class="sxs-lookup"><span data-stu-id="97d58-114">There are three ways to do this with storyboard animations:</span></span>  
  
-   <span data-ttu-id="97d58-115">設定動畫的<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性</span><span class="sxs-lookup"><span data-stu-id="97d58-115">Set the animation's <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property to</span></span> <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   <span data-ttu-id="97d58-116">移除整個分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="97d58-116">Remove the entire Storyboard.</span></span>  
  
-   <span data-ttu-id="97d58-117">移除個別屬性的動畫。</span><span class="sxs-lookup"><span data-stu-id="97d58-117">Remove the animation from the individual property.</span></span>  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a><span data-ttu-id="97d58-118">設定為 停止的動畫的 FillBehavior 屬性</span><span class="sxs-lookup"><span data-stu-id="97d58-118">Set the animation's FillBehavior property to Stop</span></span>  
 <span data-ttu-id="97d58-119">藉由設定<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>至<xref:System.Windows.Media.Animation.FillBehavior.Stop>，告訴停止作用期結束後，會影響其目標屬性的動畫。</span><span class="sxs-lookup"><span data-stu-id="97d58-119">By setting <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, you tell the animation to stop affecting its target property after it reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a><span data-ttu-id="97d58-120">移除整個分鏡腳本</span><span class="sxs-lookup"><span data-stu-id="97d58-120">Remove the entire storyboard</span></span>  
 <span data-ttu-id="97d58-121">藉由使用<xref:System.Windows.Media.Animation.RemoveStoryboard>觸發程序或<xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>方法中，您告訴停止影響其目標屬性的分鏡腳本動畫。</span><span class="sxs-lookup"><span data-stu-id="97d58-121">By using a <xref:System.Windows.Media.Animation.RemoveStoryboard> trigger or the <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> method, you tell the storyboard animations to stop affecting their target properties.</span></span> <span data-ttu-id="97d58-122">這個方法和設定之間的差異<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性是您可以移除分鏡腳本在任何時候，雖然<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性只有在當動畫到達其使用中週期結尾時。</span><span class="sxs-lookup"><span data-stu-id="97d58-122">The difference between this approach and setting the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property is that you can remove the storyboard at anytime, while the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property only has an effect when the animation reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a><span data-ttu-id="97d58-123">移除個別屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="97d58-123">Remove an animation from an individual property</span></span>  
 <span data-ttu-id="97d58-124">若要停止從影響屬性動畫的另一個方法是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>展示動畫之物件的方法。</span><span class="sxs-lookup"><span data-stu-id="97d58-124">Another technique to stop an animation from affecting a property is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> method of the object being animated.</span></span> <span data-ttu-id="97d58-125">指定要繪製的第一個參數之屬性和`null`作為第二個。</span><span class="sxs-lookup"><span data-stu-id="97d58-125">Specify the property being animated as the first parameter and `null` as the second.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 <span data-ttu-id="97d58-126">這項技術也適用於非分鏡腳本動畫中。</span><span class="sxs-lookup"><span data-stu-id="97d58-126">This technique also works for non-storyboard animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d58-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97d58-127">See also</span></span>

- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.Animation.RemoveStoryboard>
- [<span data-ttu-id="97d58-128">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="97d58-128">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="97d58-129">屬性動畫技術概觀</span><span class="sxs-lookup"><span data-stu-id="97d58-129">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
