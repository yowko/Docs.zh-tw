---
title: 如何：在立體場景中建立鏡頭位置和方向的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3D scenes
- camera direction [WPF], animating in 3D scenes
- 3D scenes [WPF], animating camera position
- 3D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3D scenes
- animation [WPF], camera direction in 3D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: 5ce94e154cd5aa29b59260f893ec2b63a08db0fc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112204"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a><span data-ttu-id="0bf22-102">如何：在立體場景中建立鏡頭位置和方向的動畫</span><span class="sxs-lookup"><span data-stu-id="0bf22-102">How to: Animate Camera Position and Direction in a 3D Scene</span></span>
<span data-ttu-id="0bf22-103">下面的示例演示如何為攝像機的位置設置動畫，並為它在 3D 場景中指向的方向設置動畫。</span><span class="sxs-lookup"><span data-stu-id="0bf22-103">The following example shows how to animate the position of a camera and animate the direction it is pointing in a 3D scene.</span></span> <span data-ttu-id="0bf22-104">這是通過使用<xref:System.Windows.Media.Animation.Point3DAnimation>和<xref:System.Windows.Media.Animation.Vector3DAnimation>分別為<xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A>和<xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A>屬性設置動畫來完成<xref:System.Windows.Media.Media3D.PerspectiveCamera>的。</span><span class="sxs-lookup"><span data-stu-id="0bf22-104">This is done by using <xref:System.Windows.Media.Animation.Point3DAnimation> and <xref:System.Windows.Media.Animation.Vector3DAnimation> to animate the <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> and <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> properties respectively of the <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="0bf22-105">您可以使用這樣的動畫來更改旁觀者對場景的視圖，以回應事件。</span><span class="sxs-lookup"><span data-stu-id="0bf22-105">You might use an animation like this to change the onlooker's view of a scene in response to an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bf22-106">範例</span><span class="sxs-lookup"><span data-stu-id="0bf22-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="0bf22-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bf22-107">See also</span></span>

- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [<span data-ttu-id="0bf22-108">使用主要畫面格建立鏡頭位置和方向的動畫</span><span class="sxs-lookup"><span data-stu-id="0bf22-108">Animate Camera Position and Direction Using Key Frames</span></span>](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [<span data-ttu-id="0bf22-109">3D 圖形概述</span><span class="sxs-lookup"><span data-stu-id="0bf22-109">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
