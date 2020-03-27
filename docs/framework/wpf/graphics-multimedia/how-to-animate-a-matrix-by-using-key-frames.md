---
title: 如何：使用主要畫面格建立矩陣的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344912"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="045fc-102">如何：使用主要畫面格建立矩陣的動畫</span><span class="sxs-lookup"><span data-stu-id="045fc-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="045fc-103">此示例演示如何使用關鍵幀對<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>進行動畫處理。</span><span class="sxs-lookup"><span data-stu-id="045fc-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="045fc-104">範例</span><span class="sxs-lookup"><span data-stu-id="045fc-104">Example</span></span>  
 <span data-ttu-id="045fc-105">下面的示例使用 類<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>為 屬性<xref:System.Windows.Media.MatrixTransform>設置<xref:System.Windows.Media.MatrixTransform.Matrix%2A>動畫。</span><span class="sxs-lookup"><span data-stu-id="045fc-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="045fc-106">該示例使用<xref:System.Windows.Media.MatrixTransform>物件轉換 的外觀<xref:System.Windows.Controls.Button>和位置。</span><span class="sxs-lookup"><span data-stu-id="045fc-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="045fc-107">此動畫使用<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>類創建兩個關鍵幀，並對其進行以下操作：</span><span class="sxs-lookup"><span data-stu-id="045fc-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="045fc-108">在前 0.2 秒內為第一個<xref:System.Windows.Media.Matrix>進行動畫處理。</span><span class="sxs-lookup"><span data-stu-id="045fc-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="045fc-109">該示例更改<xref:System.Windows.Media.Matrix.M11%2A>的<xref:System.Windows.Media.Matrix.M12%2A>和<xref:System.Windows.Media.Matrix>屬性。</span><span class="sxs-lookup"><span data-stu-id="045fc-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="045fc-110">此更改會導致按鈕拉伸並變得傾斜。</span><span class="sxs-lookup"><span data-stu-id="045fc-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="045fc-111">該示例還更改<xref:System.Windows.Media.Matrix.OffsetX%2A>和<xref:System.Windows.Media.Matrix.OffsetY%2A>屬性，以便按鈕更改位置。</span><span class="sxs-lookup"><span data-stu-id="045fc-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="045fc-112">在 1.0 秒內為第二個<xref:System.Windows.Media.Matrix>設置動畫。</span><span class="sxs-lookup"><span data-stu-id="045fc-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="045fc-113">當按鈕不再傾斜或拉伸時，按鈕將移動到其他位置。</span><span class="sxs-lookup"><span data-stu-id="045fc-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="045fc-114">無限期重複動畫。</span><span class="sxs-lookup"><span data-stu-id="045fc-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="045fc-115">從<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>物件派生的關鍵幀在值之間創建突然跳轉，也就是說，動畫的移動是抖動的。</span><span class="sxs-lookup"><span data-stu-id="045fc-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="045fc-116">如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。</span><span class="sxs-lookup"><span data-stu-id="045fc-116">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045fc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="045fc-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="045fc-118">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="045fc-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="045fc-119">關於主要畫面格操作說明的主題</span><span class="sxs-lookup"><span data-stu-id="045fc-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
