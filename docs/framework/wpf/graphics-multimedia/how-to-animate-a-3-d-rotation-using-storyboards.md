---
title: HOW TO：使用分鏡腳本建立立體旋轉的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 03b01205f1a31426a01b09533b350682c384df4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146194"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a><span data-ttu-id="95907-102">HOW TO：使用分鏡腳本建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="95907-102">How to: Animate a 3-D Rotation Using Storyboards</span></span>
<span data-ttu-id="95907-103">下列範例示範如何進行旋轉時它 「 wobbles 」 以動畫顯示 3D 物件<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>並<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>的屬性<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>物件。</span><span class="sxs-lookup"><span data-stu-id="95907-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="95907-104">這<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>物件會指定旋轉轉換的 3D 物件，並因此以動畫顯示其屬性建立的渴望旋轉的效果。</span><span class="sxs-lookup"><span data-stu-id="95907-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="95907-105">分鏡腳本，內<xref:System.Windows.Media.Animation.DoubleAnimation>用來建立動畫<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>屬性時<xref:System.Windows.Media.Animation.Vector3DAnimation>用來以動畫顯示<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="95907-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95907-106">範例</span><span class="sxs-lookup"><span data-stu-id="95907-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="95907-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95907-107">See also</span></span>

- [<span data-ttu-id="95907-108">使用 Rotation3DAnimation 建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="95907-108">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="95907-109">使用主要畫面格建立立體旋轉的動畫 (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="95907-109">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="95907-110">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="95907-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="95907-111">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="95907-111">Storyboards Overview</span></span>](storyboards-overview.md)
