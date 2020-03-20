---
title: 操作說明：旋轉物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: 02d8144c28b7a4e54fb86fea5abb694cf7af34af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185958"
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="f5b5d-102">操作說明：旋轉物件</span><span class="sxs-lookup"><span data-stu-id="f5b5d-102">How to: Rotate an Object</span></span>
<span data-ttu-id="f5b5d-103">此範例會顯示如何旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="f5b5d-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="f5b5d-104">該示例首先創建<xref:System.Windows.Media.RotateTransform>a，然後指定<xref:System.Windows.Media.RotateTransform.Angle%2A>其以度表示。</span><span class="sxs-lookup"><span data-stu-id="f5b5d-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="f5b5d-105">下面的示例圍繞<xref:System.Windows.Shapes.Polyline>其左上角旋轉物件 45 度。</span><span class="sxs-lookup"><span data-stu-id="f5b5d-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5b5d-106">範例</span><span class="sxs-lookup"><span data-stu-id="f5b5d-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="f5b5d-107">的<xref:System.Windows.Media.RotateTransform.CenterX%2A><xref:System.Windows.Media.RotateTransform.CenterY%2A>和 屬性<xref:System.Windows.Media.RotateTransform>指定物件旋轉的點。</span><span class="sxs-lookup"><span data-stu-id="f5b5d-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="f5b5d-108">此中心點是以要轉換之元素的座標空間來表示。</span><span class="sxs-lookup"><span data-stu-id="f5b5d-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="f5b5d-109">根據預設，旋轉會套用到 (0,0)，這是要轉換之物件的左上角。</span><span class="sxs-lookup"><span data-stu-id="f5b5d-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="f5b5d-110">下一<xref:System.Windows.Shapes.Polyline>個示例沿點 （25，50） 順時針旋轉物件 45 度。</span><span class="sxs-lookup"><span data-stu-id="f5b5d-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="f5b5d-111">下圖顯示了對兩個物件應用 的結果<xref:System.Windows.Media.Transform>。</span><span class="sxs-lookup"><span data-stu-id="f5b5d-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="f5b5d-112">![採用不同中心點的 45 度旋轉](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="f5b5d-112">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="f5b5d-113">繞不同旋轉中心旋轉 45 度的兩個物件</span><span class="sxs-lookup"><span data-stu-id="f5b5d-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="f5b5d-114">前面的<xref:System.Windows.Shapes.Polyline>示例中是 。 <xref:System.Windows.UIElement></span><span class="sxs-lookup"><span data-stu-id="f5b5d-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="f5b5d-115">將 應用<xref:System.Windows.Media.Transform>到<xref:System.Windows.UIElement.RenderTransform%2A>的屬性時<xref:System.Windows.UIElement>，可以使用 屬性<xref:System.Windows.UIElement.RenderTransformOrigin%2A>為應用於元素的每個<xref:System.Windows.Media.Transform>屬性指定原點。</span><span class="sxs-lookup"><span data-stu-id="f5b5d-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="f5b5d-116">由於屬性<xref:System.Windows.UIElement.RenderTransformOrigin%2A>使用相對座標，因此即使不知道元素的大小，也可以對元素的中心應用變換。</span><span class="sxs-lookup"><span data-stu-id="f5b5d-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="f5b5d-117">有關詳細資訊，請參閱[使用相對值指定變換的原點](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md)。</span><span class="sxs-lookup"><span data-stu-id="f5b5d-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="f5b5d-118">如需完整範例，請參閱 [2D 轉換範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)。</span><span class="sxs-lookup"><span data-stu-id="f5b5d-118">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b5d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5b5d-119">See also</span></span>

- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="f5b5d-120">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="f5b5d-120">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="f5b5d-121">如何使用主題</span><span class="sxs-lookup"><span data-stu-id="f5b5d-121">How-to Topics</span></span>](transformations-how-to-topics.md)
