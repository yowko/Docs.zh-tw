---
title: 作法：使用主要畫面格建立矩陣的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 6aa3e27cdfda7597c9b6acbf2980a2774f2b667b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963030"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="daa9b-102">作法：使用主要畫面格建立矩陣的動畫</span><span class="sxs-lookup"><span data-stu-id="daa9b-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="daa9b-103">這個範例示範如何使用主要畫面<xref:System.Windows.Media.MatrixTransform.Matrix%2A>格, 以<xref:System.Windows.Media.MatrixTransform>動畫顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="daa9b-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="daa9b-104">範例</span><span class="sxs-lookup"><span data-stu-id="daa9b-104">Example</span></span>  
 <span data-ttu-id="daa9b-105">下列範例會使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>類別來建立<xref:System.Windows.Media.MatrixTransform>的<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性的動畫。</span><span class="sxs-lookup"><span data-stu-id="daa9b-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="daa9b-106">這個範例會使用<xref:System.Windows.Media.MatrixTransform>物件來轉換的外觀和位置。 <xref:System.Windows.Controls.Button></span><span class="sxs-lookup"><span data-stu-id="daa9b-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="daa9b-107">這個動畫會使用<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>類別來建立兩個主要畫面格, 並對它們執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="daa9b-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="daa9b-108">在前 0.2 <xref:System.Windows.Media.Matrix>秒繪製第一個動畫。</span><span class="sxs-lookup"><span data-stu-id="daa9b-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="daa9b-109">此範例會變更<xref:System.Windows.Media.Matrix.M11%2A>的<xref:System.Windows.Media.Matrix.M12%2A>和屬性<xref:System.Windows.Media.Matrix>。</span><span class="sxs-lookup"><span data-stu-id="daa9b-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="daa9b-110">這種變更會使按鈕變得扭曲, 並變為扭曲。</span><span class="sxs-lookup"><span data-stu-id="daa9b-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="daa9b-111">此範例也會變更<xref:System.Windows.Media.Matrix.OffsetX%2A>和<xref:System.Windows.Media.Matrix.OffsetY%2A>屬性, 讓按鈕變更位置。</span><span class="sxs-lookup"><span data-stu-id="daa9b-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="daa9b-112">在1.0 秒<xref:System.Windows.Media.Matrix>繪製第二個動畫。</span><span class="sxs-lookup"><span data-stu-id="daa9b-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="daa9b-113">按鈕會移到另一個位置, 而按鈕則不會再扭曲或伸展。</span><span class="sxs-lookup"><span data-stu-id="daa9b-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="daa9b-114">無限期地重複動畫。</span><span class="sxs-lookup"><span data-stu-id="daa9b-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="daa9b-115">衍生自<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>物件的主要畫面格會建立值之間的突然跳躍, 也就是說, 動畫的移動會使其無法停用。</span><span class="sxs-lookup"><span data-stu-id="daa9b-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="daa9b-116">如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。</span><span class="sxs-lookup"><span data-stu-id="daa9b-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa9b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="daa9b-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="daa9b-118">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="daa9b-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="daa9b-119">主要畫面格操作說明主題</span><span class="sxs-lookup"><span data-stu-id="daa9b-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
