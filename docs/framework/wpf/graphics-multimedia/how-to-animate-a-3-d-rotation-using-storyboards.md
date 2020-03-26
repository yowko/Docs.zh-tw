---
title: 如何：使用分鏡腳本為 3D 旋轉設置動畫
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 088f1a33cfc73a706ffed55ffff6494adaf8fca4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112206"
---
# <a name="how-to-animate-a-3d-rotation-using-storyboards"></a><span data-ttu-id="23fdd-102">如何：使用分鏡腳本為 3D 旋轉設置動畫</span><span class="sxs-lookup"><span data-stu-id="23fdd-102">How to: Animate a 3D Rotation Using Storyboards</span></span>
<span data-ttu-id="23fdd-103">下面的示例演示如何通過對<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A><xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A><xref:System.Windows.Media.Media3D.AxisAngleRotation3D>物件的 和 屬性進行動畫處理，使其在"擺動"時旋轉。</span><span class="sxs-lookup"><span data-stu-id="23fdd-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="23fdd-104">此<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>物件指定 3D 物件的旋轉變換，因此對其屬性進行動畫處理可創建欲望旋轉效果。</span><span class="sxs-lookup"><span data-stu-id="23fdd-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="23fdd-105">在分鏡腳本中<xref:System.Windows.Media.Animation.DoubleAnimation>，用於為<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>屬性設置動畫，<xref:System.Windows.Media.Animation.Vector3DAnimation>同時用於為<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>屬性設置動畫。</span><span class="sxs-lookup"><span data-stu-id="23fdd-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23fdd-106">範例</span><span class="sxs-lookup"><span data-stu-id="23fdd-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="23fdd-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23fdd-107">See also</span></span>

- [<span data-ttu-id="23fdd-108">使用旋轉3D動畫為 3D 旋轉設置動畫</span><span class="sxs-lookup"><span data-stu-id="23fdd-108">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="23fdd-109">使用關鍵幀為 3D 旋轉設置動畫（旋轉3D動畫使用關鍵幀）</span><span class="sxs-lookup"><span data-stu-id="23fdd-109">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="23fdd-110">3D 圖形概述</span><span class="sxs-lookup"><span data-stu-id="23fdd-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="23fdd-111">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="23fdd-111">Storyboards Overview</span></span>](storyboards-overview.md)
