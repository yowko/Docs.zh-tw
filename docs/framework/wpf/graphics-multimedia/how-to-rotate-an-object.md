---
title: HOW TO：旋轉物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: 49de419f22980ab9101c388079e0348b4c1113f4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360364"
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="be563-102">HOW TO：旋轉物件</span><span class="sxs-lookup"><span data-stu-id="be563-102">How to: Rotate an Object</span></span>
<span data-ttu-id="be563-103">此範例會顯示如何旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="be563-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="be563-104">此範例會先建立<xref:System.Windows.Media.RotateTransform>，然後指定其<xref:System.Windows.Media.RotateTransform.Angle%2A>以度為單位。</span><span class="sxs-lookup"><span data-stu-id="be563-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="be563-105">下列範例會旋轉<xref:System.Windows.Shapes.Polyline>物件繞其左上角的 45 度。</span><span class="sxs-lookup"><span data-stu-id="be563-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be563-106">範例</span><span class="sxs-lookup"><span data-stu-id="be563-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="be563-107"><xref:System.Windows.Media.RotateTransform.CenterX%2A>並<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性的<xref:System.Windows.Media.RotateTransform>指定哪些物件會旋轉的點。</span><span class="sxs-lookup"><span data-stu-id="be563-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="be563-108">此中心點是以要轉換之元素的座標空間來表示。</span><span class="sxs-lookup"><span data-stu-id="be563-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="be563-109">根據預設，旋轉會套用到 (0,0)，這是要轉換之物件的左上角。</span><span class="sxs-lookup"><span data-stu-id="be563-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="be563-110">下列範例會<xref:System.Windows.Shapes.Polyline>物件的點 (25，50) 順時針旋轉 45 度。</span><span class="sxs-lookup"><span data-stu-id="be563-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="be563-111">下圖顯示將套用的結果<xref:System.Windows.Media.Transform>兩個物件。</span><span class="sxs-lookup"><span data-stu-id="be563-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="be563-112">![不同中心點的 45 度旋轉](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="be563-112">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="be563-113">繞不同旋轉中心旋轉 45 度的兩個物件</span><span class="sxs-lookup"><span data-stu-id="be563-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="be563-114"><xref:System.Windows.Shapes.Polyline>先前的範例中是<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="be563-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="be563-115">當您套用<xref:System.Windows.Media.Transform>來<xref:System.Windows.UIElement.RenderTransform%2A>屬性<xref:System.Windows.UIElement>，您可以使用<xref:System.Windows.UIElement.RenderTransformOrigin%2A>屬性，以指定的原始主機每<xref:System.Windows.Media.Transform>套用至項目。</span><span class="sxs-lookup"><span data-stu-id="be563-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="be563-116">因為<xref:System.Windows.UIElement.RenderTransformOrigin%2A>屬性使用相對座標表示，您可以將轉換套用至項目的中心，即使您不知道它的大小。</span><span class="sxs-lookup"><span data-stu-id="be563-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="be563-117">如需詳細資訊，以及如需範例，請參閱[指定使用相對值轉換的原點](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md)。</span><span class="sxs-lookup"><span data-stu-id="be563-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="be563-118">如需完整範例，請參閱 [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。</span><span class="sxs-lookup"><span data-stu-id="be563-118">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be563-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be563-119">See also</span></span>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="be563-120">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="be563-120">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="be563-121">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="be563-121">How-to Topics</span></span>](transformations-how-to-topics.md)
