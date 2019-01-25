---
title: HOW TO：在立體場景中建立鏡頭位置和方向的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: 18941f32de02b6e281df6c2c54c6c666dae63197
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564168"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a><span data-ttu-id="916ae-102">HOW TO：在立體場景中建立鏡頭位置和方向的動畫</span><span class="sxs-lookup"><span data-stu-id="916ae-102">How to: Animate Camera Position and Direction in a 3D Scene</span></span>
<span data-ttu-id="916ae-103">下列範例示範如何以動畫顯示觀景窗的位置，並以動畫顯示其為 3D 場景中所指的方向。</span><span class="sxs-lookup"><span data-stu-id="916ae-103">The following example shows how to animate the position of a camera and animate the direction it is pointing in a 3D scene.</span></span> <span data-ttu-id="916ae-104">這是藉由使用<xref:System.Windows.Media.Animation.Point3DAnimation>並<xref:System.Windows.Media.Animation.Vector3DAnimation>來以動畫顯示<xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A>並<xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A>屬性，分別是<xref:System.Windows.Media.Media3D.PerspectiveCamera>。</span><span class="sxs-lookup"><span data-stu-id="916ae-104">This is done by using <xref:System.Windows.Media.Animation.Point3DAnimation> and <xref:System.Windows.Media.Animation.Vector3DAnimation> to animate the <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> and <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> properties respectively of the <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="916ae-105">若要變更旁觀者的檢視，以回應事件場景的您可以使用這類動畫。</span><span class="sxs-lookup"><span data-stu-id="916ae-105">You might use an animation like this to change the onlooker's view of a scene in response to an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="916ae-106">範例</span><span class="sxs-lookup"><span data-stu-id="916ae-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="916ae-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="916ae-107">See also</span></span>
- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [<span data-ttu-id="916ae-108">使用主要畫面格建立鏡頭位置和方向的動畫</span><span class="sxs-lookup"><span data-stu-id="916ae-108">Animate Camera Position and Direction Using Key Frames</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)
- [<span data-ttu-id="916ae-109">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="916ae-109">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
