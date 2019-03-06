---
title: HOW TO：使用腳本建立立體旋轉的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 20f5bf565ded624e4ea7e1e615f09b4c698526bd
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357218"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a><span data-ttu-id="b4ac9-102">HOW TO：使用腳本建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="b4ac9-102">How to: Animate a 3-D Rotation Using Storyboards</span></span>
<span data-ttu-id="b4ac9-103">下列範例示範如何進行旋轉時它 「 wobbles 」 以動畫顯示 3D 物件<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>並<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>的屬性<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>物件。</span><span class="sxs-lookup"><span data-stu-id="b4ac9-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="b4ac9-104">這<xref:System.Windows.Media.Media3D.AxisAngleRotation3D>物件會指定旋轉轉換的 3D 物件，並因此以動畫顯示其屬性建立的渴望旋轉的效果。</span><span class="sxs-lookup"><span data-stu-id="b4ac9-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="b4ac9-105">分鏡腳本，內<xref:System.Windows.Media.Animation.DoubleAnimation>用來建立動畫<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>屬性時<xref:System.Windows.Media.Animation.Vector3DAnimation>用來以動畫顯示<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b4ac9-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4ac9-106">範例</span><span class="sxs-lookup"><span data-stu-id="b4ac9-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b4ac9-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4ac9-107">See also</span></span>
- [<span data-ttu-id="b4ac9-108">使用 Rotation3DAnimation 建立立體旋轉的動畫</span><span class="sxs-lookup"><span data-stu-id="b4ac9-108">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="b4ac9-109">使用主要畫面格建立立體旋轉的動畫 (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="b4ac9-109">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="b4ac9-110">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="b4ac9-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="b4ac9-111">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="b4ac9-111">Storyboards Overview</span></span>](storyboards-overview.md)
