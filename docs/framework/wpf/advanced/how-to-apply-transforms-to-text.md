---
title: 如何：對文字套用轉換
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: 867f39e3df8493014d8601530e91310c3bbbeeb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141610"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="746ae-102">如何：對文字套用轉換</span><span class="sxs-lookup"><span data-stu-id="746ae-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="746ae-103">轉換可以變更應用程式中文字的顯示。</span><span class="sxs-lookup"><span data-stu-id="746ae-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="746ae-104">以下示例使用不同類型的呈現轉換來影響<xref:System.Windows.Controls.TextBlock>控制項中文本的顯示。</span><span class="sxs-lookup"><span data-stu-id="746ae-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="746ae-105">範例</span><span class="sxs-lookup"><span data-stu-id="746ae-105">Example</span></span>  
 <span data-ttu-id="746ae-106">下列範例示範二維 x-y 平面的指定點所旋轉的文字。</span><span class="sxs-lookup"><span data-stu-id="746ae-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 ![使用 RotateTransform 旋轉的文字](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 <span data-ttu-id="746ae-108">以下代碼示例使用 旋轉<xref:System.Windows.Media.RotateTransform>文本。</span><span class="sxs-lookup"><span data-stu-id="746ae-108">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="746ae-109"><xref:System.Windows.Media.RotateTransform.Angle%2A>值 90 順時針旋轉元素 90 度。</span><span class="sxs-lookup"><span data-stu-id="746ae-109">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="746ae-110">下列範例示範沿著 X 軸縮放 150% 的第二行文字，以及沿著 Y 軸縮放 150% 的第三行文字。</span><span class="sxs-lookup"><span data-stu-id="746ae-110">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 ![使用 ScaleTransform 縮放的文字](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg)
  
 <span data-ttu-id="746ae-112">以下代碼示例使用<xref:System.Windows.Media.ScaleTransform>縮放文本從其原始大小。</span><span class="sxs-lookup"><span data-stu-id="746ae-112">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> <span data-ttu-id="746ae-113">縮放文字與增加文字字型大小不同。</span><span class="sxs-lookup"><span data-stu-id="746ae-113">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="746ae-114">字型大小會彼此獨立計算，以提供不同大小的最佳解析度。</span><span class="sxs-lookup"><span data-stu-id="746ae-114">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="746ae-115">在另一方面，縮放的文字會保留原始大小文字的比例。</span><span class="sxs-lookup"><span data-stu-id="746ae-115">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="746ae-116">下列範例顯示沿著 X 軸扭曲的文字。</span><span class="sxs-lookup"><span data-stu-id="746ae-116">The following example shows text skewed along the x-axis.</span></span>  
  
 ![使用 SkewTransform 傾斜的文字](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)

 <span data-ttu-id="746ae-118">以下代碼示例使用 扭曲<xref:System.Windows.Media.SkewTransform>文本。</span><span class="sxs-lookup"><span data-stu-id="746ae-118">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="746ae-119">扭曲也稱為傾斜，這種轉換會以非一致的方式延伸座標空間。</span><span class="sxs-lookup"><span data-stu-id="746ae-119">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="746ae-120">在此範例中，這兩個文字字串會沿著 X 座標扭曲 -30° 和 30°。</span><span class="sxs-lookup"><span data-stu-id="746ae-120">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="746ae-121">下列範例顯示沿著 X 和 Y 軸平移或移動的文字。</span><span class="sxs-lookup"><span data-stu-id="746ae-121">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 ![使用 TranslateTransform 的文字位移](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 <span data-ttu-id="746ae-123">以下代碼示例使用 偏移<xref:System.Windows.Media.TranslateTransform>文本。</span><span class="sxs-lookup"><span data-stu-id="746ae-123">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="746ae-124">在此範例中，主要文字下方文字的略微位移複本會建立陰影效果。</span><span class="sxs-lookup"><span data-stu-id="746ae-124">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> <span data-ttu-id="746ae-125">提供了<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>一組豐富的功能，用於提供陰影效果。</span><span class="sxs-lookup"><span data-stu-id="746ae-125">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="746ae-126">有關詳細資訊，請參閱[使用陰影創建文本](how-to-create-text-with-a-shadow.md)。</span><span class="sxs-lookup"><span data-stu-id="746ae-126">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="746ae-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="746ae-127">See also</span></span>

- [<span data-ttu-id="746ae-128">對文字套用動畫</span><span class="sxs-lookup"><span data-stu-id="746ae-128">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
