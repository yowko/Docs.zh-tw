---
title: HOW TO：使用四元數建立立體旋轉的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: df51db324bffc038bc585b6d977a82d54feefb3b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550925"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a><span data-ttu-id="36f1b-102">HOW TO：使用四元數建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="36f1b-102">How to: Animate a 3-D Rotation Using Quaternions</span></span>
<span data-ttu-id="36f1b-103">此範例示範如何以動畫顯示 3d 物件使用四元數旋轉。</span><span class="sxs-lookup"><span data-stu-id="36f1b-103">This example shows how to animate a rotation of a 3-D object using quaternions.</span></span>  
  
 <span data-ttu-id="36f1b-104">以下顯示的程式碼<xref:System.Windows.Media.Media3D.QuaternionRotation3D>做為值<xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>屬性<xref:System.Windows.Media.Media3D.RotateTransform3D>。</span><span class="sxs-lookup"><span data-stu-id="36f1b-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="36f1b-105">這<xref:System.Windows.Media.Media3D.QuaternionRotation3D>以動畫顯示與<xref:System.Windows.Media.Animation.QuaternionAnimation>內<xref:System.Windows.Media.Animation.Storyboard>使用下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="36f1b-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="36f1b-106">範例</span><span class="sxs-lookup"><span data-stu-id="36f1b-106">Example</span></span>  
 <span data-ttu-id="36f1b-107">下列程式碼顯示整個範例。</span><span class="sxs-lookup"><span data-stu-id="36f1b-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="36f1b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36f1b-108">See also</span></span>
- [<span data-ttu-id="36f1b-109">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="36f1b-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="36f1b-110">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="36f1b-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="36f1b-111">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="36f1b-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [<span data-ttu-id="36f1b-112">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="36f1b-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [<span data-ttu-id="36f1b-113">使用分鏡腳本建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="36f1b-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="36f1b-114">使用 Rotation3DAnimation 建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="36f1b-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
