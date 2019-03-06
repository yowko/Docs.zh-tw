---
title: HOW TO：水平或垂直翻轉 UIElement
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 3dd9a8e2a94acf62973701094e8966c8ebff15c9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356347"
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a><span data-ttu-id="9ccde-102">HOW TO：水平或垂直翻轉 UIElement</span><span class="sxs-lookup"><span data-stu-id="9ccde-102">How to: Flip a UIElement Horizontally or Vertically</span></span>
<span data-ttu-id="9ccde-103">此範例示範如何使用<xref:System.Windows.Media.ScaleTransform>翻轉<xref:System.Windows.UIElement>水平或垂直。</span><span class="sxs-lookup"><span data-stu-id="9ccde-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to flip a <xref:System.Windows.UIElement> horizontally or vertically.</span></span> <span data-ttu-id="9ccde-104">在此範例中，<xref:System.Windows.Controls.Button>控制項 (一種<xref:System.Windows.UIElement>) 已藉由套用翻轉<xref:System.Windows.Media.ScaleTransform>至其<xref:System.Windows.UIElement.RenderTransform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="9ccde-104">In this example, a <xref:System.Windows.Controls.Button> control (a type of <xref:System.Windows.UIElement>) is flipped by applying a <xref:System.Windows.Media.ScaleTransform> to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ccde-105">範例</span><span class="sxs-lookup"><span data-stu-id="9ccde-105">Example</span></span>  
 <span data-ttu-id="9ccde-106">下圖顯示翻轉的按鈕。</span><span class="sxs-lookup"><span data-stu-id="9ccde-106">The following illustration shows the button to flip.</span></span>  
  
 <span data-ttu-id="9ccde-107">![不含轉換的按鈕](./media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span><span class="sxs-lookup"><span data-stu-id="9ccde-107">![A button with no transform](./media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span></span>  
<span data-ttu-id="9ccde-108">若要翻轉 UIElement</span><span class="sxs-lookup"><span data-stu-id="9ccde-108">The UIElement to flip</span></span>  
  
 <span data-ttu-id="9ccde-109">下面顯示建立按鈕的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9ccde-109">The following shows the code that creates the button.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a><span data-ttu-id="9ccde-110">範例</span><span class="sxs-lookup"><span data-stu-id="9ccde-110">Example</span></span>  
 <span data-ttu-id="9ccde-111">若要水平翻轉的按鈕，建立<xref:System.Windows.Media.ScaleTransform>並設定其<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>屬性為-1。</span><span class="sxs-lookup"><span data-stu-id="9ccde-111">To flip the button horizontally, create a <xref:System.Windows.Media.ScaleTransform> and set its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property to -1.</span></span> <span data-ttu-id="9ccde-112">適用於<xref:System.Windows.Media.ScaleTransform>至按鈕的<xref:System.Windows.UIElement.RenderTransform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="9ccde-112">Apply the <xref:System.Windows.Media.ScaleTransform> to the button's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 <span data-ttu-id="9ccde-113">![翻轉的按鈕水平&#40;0，0&#41;](./media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span><span class="sxs-lookup"><span data-stu-id="9ccde-113">![A button flipped horizontally about &#40;0,0&#41;](./media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span></span>  
<span data-ttu-id="9ccde-114">套用 ScaleTransform 後按鈕</span><span class="sxs-lookup"><span data-stu-id="9ccde-114">The button after applying the ScaleTransform</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ccde-115">範例</span><span class="sxs-lookup"><span data-stu-id="9ccde-115">Example</span></span>  
 <span data-ttu-id="9ccde-116">您可以看到從上圖中，已翻轉的按鈕，但它也已移動。</span><span class="sxs-lookup"><span data-stu-id="9ccde-116">As you can see from the previous illustration, the button was flipped, but it was also moved.</span></span> <span data-ttu-id="9ccde-117">這是因為從其左上角已翻轉的按鈕。</span><span class="sxs-lookup"><span data-stu-id="9ccde-117">That's because the button was flipped from its top left corner.</span></span> <span data-ttu-id="9ccde-118">若要就地翻轉的按鈕，您要套用<xref:System.Windows.Media.ScaleTransform>到其中心，而不是其邊角。</span><span class="sxs-lookup"><span data-stu-id="9ccde-118">To flip the button in place, you want to apply the <xref:System.Windows.Media.ScaleTransform> to its center, not its corner.</span></span> <span data-ttu-id="9ccde-119">輕鬆地套用<xref:System.Windows.Media.ScaleTransform>中心 」 是設定按鈕的按鈕<xref:System.Windows.UIElement.RenderTransformOrigin%2A>屬性為 0.5，0.5。</span><span class="sxs-lookup"><span data-stu-id="9ccde-119">An easy way to apply the <xref:System.Windows.Media.ScaleTransform> to the buttons center is to set the button's <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to 0.5, 0.5.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 <span data-ttu-id="9ccde-120">![對其中心水平翻轉的按鈕](./media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="9ccde-120">![A button flipped horizontally about its center](./media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span></span>  
<span data-ttu-id="9ccde-121">按鈕的 RenderTransformOrigin 0.5，0.5</span><span class="sxs-lookup"><span data-stu-id="9ccde-121">The button with a RenderTransformOrigin of 0.5, 0.5</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ccde-122">範例</span><span class="sxs-lookup"><span data-stu-id="9ccde-122">Example</span></span>  
 <span data-ttu-id="9ccde-123">若要垂直翻轉的按鈕，將<xref:System.Windows.Media.ScaleTransform>物件的<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性，而不是其<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="9ccde-123">To flip the button vertically, set the <xref:System.Windows.Media.ScaleTransform> object's <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> property instead of its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 <span data-ttu-id="9ccde-124">![對其中心垂直翻轉的按鈕](./media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="9ccde-124">![A button flipped vertically about its center](./media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span></span>  
<span data-ttu-id="9ccde-125">垂直翻轉的按鈕</span><span class="sxs-lookup"><span data-stu-id="9ccde-125">The vertically flipped button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ccde-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ccde-126">See also</span></span>
- [<span data-ttu-id="9ccde-127">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="9ccde-127">Transforms Overview</span></span>](../graphics-multimedia/transforms-overview.md)
