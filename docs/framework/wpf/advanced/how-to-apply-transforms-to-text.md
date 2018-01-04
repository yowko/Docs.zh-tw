---
title: "如何：對文字套用轉換"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c1e26b31907e7794492b88ea3a696d3db4d37d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="0ea61-102">如何：對文字套用轉換</span><span class="sxs-lookup"><span data-stu-id="0ea61-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="0ea61-103">轉換可以變更應用程式中文字的顯示。</span><span class="sxs-lookup"><span data-stu-id="0ea61-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="0ea61-104">下列範例會使用不同類型的呈現轉換來影響的文字顯示<xref:System.Windows.Controls.TextBlock>控制項。</span><span class="sxs-lookup"><span data-stu-id="0ea61-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ea61-105">範例</span><span class="sxs-lookup"><span data-stu-id="0ea61-105">Example</span></span>  
 <span data-ttu-id="0ea61-106">下列範例示範二維 x-y 平面的指定點所旋轉的文字。</span><span class="sxs-lookup"><span data-stu-id="0ea61-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 <span data-ttu-id="0ea61-107">![使用 rotatetransform 旋轉的文字](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")</span><span class="sxs-lookup"><span data-stu-id="0ea61-107">![Text rotated using a RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")</span></span>  
<span data-ttu-id="0ea61-108">旋轉 90 度的文字範例</span><span class="sxs-lookup"><span data-stu-id="0ea61-108">Example of text rotated 90 degrees</span></span>  
  
 <span data-ttu-id="0ea61-109">下列程式碼範例使用<xref:System.Windows.Media.RotateTransform>旋轉文字。</span><span class="sxs-lookup"><span data-stu-id="0ea61-109">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="0ea61-110"><xref:System.Windows.Media.RotateTransform.Angle%2A>值 90 旋轉元素順時針旋轉 90 度。</span><span class="sxs-lookup"><span data-stu-id="0ea61-110">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="0ea61-111">下列範例示範沿著 X 軸縮放 150% 的第二行文字，以及沿著 Y 軸縮放 150% 的第三行文字。</span><span class="sxs-lookup"><span data-stu-id="0ea61-111">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 <span data-ttu-id="0ea61-112">![使用 scaletransform 縮放的文字](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")</span><span class="sxs-lookup"><span data-stu-id="0ea61-112">![Text scaled using a ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")</span></span>  
<span data-ttu-id="0ea61-113">縮放文字範例</span><span class="sxs-lookup"><span data-stu-id="0ea61-113">Example of scaled text</span></span>  
  
 <span data-ttu-id="0ea61-114">下列程式碼範例使用<xref:System.Windows.Media.ScaleTransform>從其原始大小的小數位數文字。</span><span class="sxs-lookup"><span data-stu-id="0ea61-114">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  <span data-ttu-id="0ea61-115">縮放文字與增加文字字型大小不同。</span><span class="sxs-lookup"><span data-stu-id="0ea61-115">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="0ea61-116">字型大小會彼此獨立計算，以提供不同大小的最佳解析度。</span><span class="sxs-lookup"><span data-stu-id="0ea61-116">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="0ea61-117">在另一方面，縮放的文字會保留原始大小文字的比例。</span><span class="sxs-lookup"><span data-stu-id="0ea61-117">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="0ea61-118">下列範例示範沿著 X 軸傾斜的文字。</span><span class="sxs-lookup"><span data-stu-id="0ea61-118">The following example shows text skewed along the x-axis.</span></span>  
  
 <span data-ttu-id="0ea61-119">![使用 skewtransform 傾斜的文字](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")</span><span class="sxs-lookup"><span data-stu-id="0ea61-119">![Text skewed using a SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")</span></span>  
<span data-ttu-id="0ea61-120">扭曲文字範例</span><span class="sxs-lookup"><span data-stu-id="0ea61-120">Example of skewed text</span></span>  
  
 <span data-ttu-id="0ea61-121">下列程式碼範例使用<xref:System.Windows.Media.SkewTransform>扭曲文字。</span><span class="sxs-lookup"><span data-stu-id="0ea61-121">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="0ea61-122">扭曲也稱為傾斜，這種轉換會以非一致的方式延伸座標空間。</span><span class="sxs-lookup"><span data-stu-id="0ea61-122">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="0ea61-123">在此範例中，這兩個文字字串會沿著 X 座標扭曲 -30° 和 30°。</span><span class="sxs-lookup"><span data-stu-id="0ea61-123">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="0ea61-124">下列範例顯示沿著 X 和 Y 軸平移或移動的文字。</span><span class="sxs-lookup"><span data-stu-id="0ea61-124">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 <span data-ttu-id="0ea61-125">![位移使用 translatetransform 的文字](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")</span><span class="sxs-lookup"><span data-stu-id="0ea61-125">![Text offset using a TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")</span></span>  
<span data-ttu-id="0ea61-126">平移文字範例</span><span class="sxs-lookup"><span data-stu-id="0ea61-126">Example of translated text</span></span>  
  
 <span data-ttu-id="0ea61-127">下列程式碼範例使用<xref:System.Windows.Media.TranslateTransform>位移文字。</span><span class="sxs-lookup"><span data-stu-id="0ea61-127">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="0ea61-128">在此範例中，主要文字下方文字的略微位移複本會建立陰影效果。</span><span class="sxs-lookup"><span data-stu-id="0ea61-128">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <span data-ttu-id="0ea61-129"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect>提供一組豐富的功能提供陰影效果。</span><span class="sxs-lookup"><span data-stu-id="0ea61-129">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="0ea61-130">如需詳細資訊，請參閱[建立文字陰影](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md)。</span><span class="sxs-lookup"><span data-stu-id="0ea61-130">For more information, see [Create Text with a Shadow](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea61-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ea61-131">See Also</span></span>  
 [<span data-ttu-id="0ea61-132">對文字套用動畫</span><span class="sxs-lookup"><span data-stu-id="0ea61-132">Apply Animations to Text</span></span>](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
