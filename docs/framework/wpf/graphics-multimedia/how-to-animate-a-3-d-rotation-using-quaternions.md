---
title: HOW TO：使用四元數建立立體旋轉的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 079358ec12da803c8aa497bce1c272fa51f1c3b5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368567"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a><span data-ttu-id="b7421-102">HOW TO：使用四元數建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="b7421-102">How to: Animate a 3-D Rotation Using Quaternions</span></span>
<span data-ttu-id="b7421-103">此範例示範如何以動畫顯示 3d 物件使用四元數旋轉。</span><span class="sxs-lookup"><span data-stu-id="b7421-103">This example shows how to animate a rotation of a 3-D object using quaternions.</span></span>  
  
 <span data-ttu-id="b7421-104">以下顯示的程式碼<xref:System.Windows.Media.Media3D.QuaternionRotation3D>做為值<xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>屬性<xref:System.Windows.Media.Media3D.RotateTransform3D>。</span><span class="sxs-lookup"><span data-stu-id="b7421-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="b7421-105">這<xref:System.Windows.Media.Media3D.QuaternionRotation3D>以動畫顯示與<xref:System.Windows.Media.Animation.QuaternionAnimation>內<xref:System.Windows.Media.Animation.Storyboard>使用下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="b7421-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="b7421-106">範例</span><span class="sxs-lookup"><span data-stu-id="b7421-106">Example</span></span>  
 <span data-ttu-id="b7421-107">下列程式碼顯示整個範例。</span><span class="sxs-lookup"><span data-stu-id="b7421-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b7421-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7421-108">See also</span></span>
- [<span data-ttu-id="b7421-109">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="b7421-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="b7421-110">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="b7421-110">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="b7421-111">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="b7421-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="b7421-112">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="b7421-112">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="b7421-113">使用分鏡腳本建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="b7421-113">Animate a 3-D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="b7421-114">使用 Rotation3DAnimation 建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="b7421-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
