---
title: "如何：使用主要畫面格建立矩陣的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8c67b5c8e179485083a40aa8a196fbee3e0fc24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="6d9eb-102">如何：使用主要畫面格建立矩陣的動畫</span><span class="sxs-lookup"><span data-stu-id="6d9eb-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="6d9eb-103">此範例示範如何以動畫方式顯示<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>所使用的主要畫面格。</span><span class="sxs-lookup"><span data-stu-id="6d9eb-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d9eb-104">範例</span><span class="sxs-lookup"><span data-stu-id="6d9eb-104">Example</span></span>  
 <span data-ttu-id="6d9eb-105">下列範例會使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>。</span><span class="sxs-lookup"><span data-stu-id="6d9eb-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="6d9eb-106">此範例會使用<xref:System.Windows.Media.MatrixTransform>要轉換的外觀和位置物件<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="6d9eb-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="6d9eb-107">這個動畫使用<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>類別來建立兩個主要畫面格，並會與其下列：</span><span class="sxs-lookup"><span data-stu-id="6d9eb-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1.  <span data-ttu-id="6d9eb-108">以動畫方式顯示第一個<xref:System.Windows.Media.Matrix>的第一個 0.2 秒數內。</span><span class="sxs-lookup"><span data-stu-id="6d9eb-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="6d9eb-109">範例會變更<xref:System.Windows.Media.Matrix.M11%2A>和<xref:System.Windows.Media.Matrix.M12%2A>屬性<xref:System.Windows.Media.Matrix>。</span><span class="sxs-lookup"><span data-stu-id="6d9eb-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="6d9eb-110">這項變更會使按鈕自動縮放，並會扭曲。</span><span class="sxs-lookup"><span data-stu-id="6d9eb-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="6d9eb-111">此範例也會變更<xref:System.Windows.Media.Matrix.OffsetX%2A>和<xref:System.Windows.Media.Matrix.OffsetY%2A>屬性，讓按鈕將變更位置。</span><span class="sxs-lookup"><span data-stu-id="6d9eb-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2.  <span data-ttu-id="6d9eb-112">以動畫方式顯示第二個<xref:System.Windows.Media.Matrix>在 1.0 秒。</span><span class="sxs-lookup"><span data-stu-id="6d9eb-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="6d9eb-113">雖然不會再扭曲或自動縮放 按鈕，按鈕會移到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="6d9eb-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3.  <span data-ttu-id="6d9eb-114">無限期地重複動畫。</span><span class="sxs-lookup"><span data-stu-id="6d9eb-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d9eb-115">主要畫面衍生自<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>物件建立值之間的突然跳躍點，也就是不穩定的動畫移動。</span><span class="sxs-lookup"><span data-stu-id="6d9eb-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="6d9eb-116">如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="6d9eb-116">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d9eb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d9eb-117">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [<span data-ttu-id="6d9eb-118">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="6d9eb-118">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="6d9eb-119">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="6d9eb-119">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
