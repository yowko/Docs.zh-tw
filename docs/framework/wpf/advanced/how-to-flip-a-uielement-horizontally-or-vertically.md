---
title: "如何：水平或垂直翻轉 UIElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 84d1360246141cfa565d669fff108e3e4db3ce33
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a><span data-ttu-id="54f4d-102">如何：水平或垂直翻轉 UIElement</span><span class="sxs-lookup"><span data-stu-id="54f4d-102">How to: Flip a UIElement Horizontally or Vertically</span></span>
<span data-ttu-id="54f4d-103">這個範例示範如何使用<xref:System.Windows.Media.ScaleTransform>翻轉<xref:System.Windows.UIElement>水平或垂直。</span><span class="sxs-lookup"><span data-stu-id="54f4d-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to flip a <xref:System.Windows.UIElement> horizontally or vertically.</span></span> <span data-ttu-id="54f4d-104">在此範例中，<xref:System.Windows.Controls.Button>控制項 (一種<xref:System.Windows.UIElement>) 翻轉藉由套用<xref:System.Windows.Media.ScaleTransform>至其<xref:System.Windows.UIElement.RenderTransform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="54f4d-104">In this example, a <xref:System.Windows.Controls.Button> control (a type of <xref:System.Windows.UIElement>) is flipped by applying a <xref:System.Windows.Media.ScaleTransform> to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54f4d-105">範例</span><span class="sxs-lookup"><span data-stu-id="54f4d-105">Example</span></span>  
 <span data-ttu-id="54f4d-106">下圖顯示要翻轉的按鈕。</span><span class="sxs-lookup"><span data-stu-id="54f4d-106">The following illustration shows the button to flip.</span></span>  
  
 <span data-ttu-id="54f4d-107">![不含轉換的按鈕](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span><span class="sxs-lookup"><span data-stu-id="54f4d-107">![A button with no transform](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span></span>  
<span data-ttu-id="54f4d-108">若要翻轉 UIElement</span><span class="sxs-lookup"><span data-stu-id="54f4d-108">The UIElement to flip</span></span>  
  
 <span data-ttu-id="54f4d-109">以下顯示的程式碼，建立按鈕。</span><span class="sxs-lookup"><span data-stu-id="54f4d-109">The following shows the code that creates the button.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a><span data-ttu-id="54f4d-110">範例</span><span class="sxs-lookup"><span data-stu-id="54f4d-110">Example</span></span>  
 <span data-ttu-id="54f4d-111">若要水平翻轉的按鈕，建立<xref:System.Windows.Media.ScaleTransform>並設定其<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>屬性設為-1。</span><span class="sxs-lookup"><span data-stu-id="54f4d-111">To flip the button horizontally, create a <xref:System.Windows.Media.ScaleTransform> and set its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property to -1.</span></span> <span data-ttu-id="54f4d-112">套用<xref:System.Windows.Media.ScaleTransform>按鈕<xref:System.Windows.UIElement.RenderTransform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="54f4d-112">Apply the <xref:System.Windows.Media.ScaleTransform> to the button's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 <span data-ttu-id="54f4d-113">![水平翻轉的按鈕 &#40; 0，0 &#41;] (../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span><span class="sxs-lookup"><span data-stu-id="54f4d-113">![A button flipped horizontally about &#40;0,0&#41;](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span></span>  
<span data-ttu-id="54f4d-114">以後 scaletransform 縮放按鈕</span><span class="sxs-lookup"><span data-stu-id="54f4d-114">The button after applying the ScaleTransform</span></span>  
  
## <a name="example"></a><span data-ttu-id="54f4d-115">範例</span><span class="sxs-lookup"><span data-stu-id="54f4d-115">Example</span></span>  
 <span data-ttu-id="54f4d-116">您可以從上圖中看到，已翻轉的按鈕，但它也已移動。</span><span class="sxs-lookup"><span data-stu-id="54f4d-116">As you can see from the previous illustration, the button was flipped, but it was also moved.</span></span> <span data-ttu-id="54f4d-117">這是因為從其左上角已翻轉的按鈕。</span><span class="sxs-lookup"><span data-stu-id="54f4d-117">That's because the button was flipped from its top left corner.</span></span> <span data-ttu-id="54f4d-118">若要就地翻轉的按鈕，您要套用<xref:System.Windows.Media.ScaleTransform>到其中心時，不是其邊角。</span><span class="sxs-lookup"><span data-stu-id="54f4d-118">To flip the button in place, you want to apply the <xref:System.Windows.Media.ScaleTransform> to its center, not its corner.</span></span> <span data-ttu-id="54f4d-119">輕鬆地套用<xref:System.Windows.Media.ScaleTransform>中心是設定按鈕的按鈕<xref:System.Windows.UIElement.RenderTransformOrigin%2A>屬性為 0.5，0.5。</span><span class="sxs-lookup"><span data-stu-id="54f4d-119">An easy way to apply the <xref:System.Windows.Media.ScaleTransform> to the buttons center is to set the button's <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to 0.5, 0.5.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 <span data-ttu-id="54f4d-120">![對其中心水平翻轉的按鈕](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="54f4d-120">![A button flipped horizontally about its center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span></span>  
<span data-ttu-id="54f4d-121">按鈕的 RenderTransformOrigin 為 0.5，0.5</span><span class="sxs-lookup"><span data-stu-id="54f4d-121">The button with a RenderTransformOrigin of 0.5, 0.5</span></span>  
  
## <a name="example"></a><span data-ttu-id="54f4d-122">範例</span><span class="sxs-lookup"><span data-stu-id="54f4d-122">Example</span></span>  
 <span data-ttu-id="54f4d-123">若要垂直翻轉的按鈕，設定<xref:System.Windows.Media.ScaleTransform>物件的<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性而非其<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="54f4d-123">To flip the button vertically, set the <xref:System.Windows.Media.ScaleTransform> object's <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> property instead of its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 <span data-ttu-id="54f4d-124">![對其中心垂直翻轉的按鈕](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="54f4d-124">![A button flipped vertically about its center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span></span>  
<span data-ttu-id="54f4d-125">垂直翻轉的按鈕</span><span class="sxs-lookup"><span data-stu-id="54f4d-125">The vertically flipped button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54f4d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54f4d-126">See Also</span></span>  
 [<span data-ttu-id="54f4d-127">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="54f4d-127">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
