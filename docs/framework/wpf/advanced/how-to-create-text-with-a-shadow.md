---
title: 如何：建立含陰影的文字
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: c3e8135372ce4a092552c812cd971cb70bc49bf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186854"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="84d28-102">如何：建立含陰影的文字</span><span class="sxs-lookup"><span data-stu-id="84d28-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="84d28-103">本節中的範例示範如何建立所顯示文字的陰影效果。</span><span class="sxs-lookup"><span data-stu-id="84d28-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84d28-104">範例</span><span class="sxs-lookup"><span data-stu-id="84d28-104">Example</span></span>  
 <span data-ttu-id="84d28-105">該<xref:System.Windows.Media.Effects.DropShadowEffect>物件允許您為[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]物件創建各種投影效果。</span><span class="sxs-lookup"><span data-stu-id="84d28-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="84d28-106">下列範例示範套用至文字的延伸陰影效果。</span><span class="sxs-lookup"><span data-stu-id="84d28-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="84d28-107">在此情況下，陰影是柔邊陰影，表示陰影色彩模糊。</span><span class="sxs-lookup"><span data-stu-id="84d28-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![具有柔和度&#61; 0.25 的文本陰影](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg)
  
 <span data-ttu-id="84d28-109">您可以通過設置<xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A>屬性來控制陰影的寬度。</span><span class="sxs-lookup"><span data-stu-id="84d28-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="84d28-110">的值`4.0`表示陰影寬度為 4 圖元。</span><span class="sxs-lookup"><span data-stu-id="84d28-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="84d28-111">您可以通過修改<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>屬性來控制陰影的柔和度或模糊性。</span><span class="sxs-lookup"><span data-stu-id="84d28-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="84d28-112">的值`0.0`表示沒有模糊。</span><span class="sxs-lookup"><span data-stu-id="84d28-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="84d28-113">下列程式碼範例示範如何建立柔邊陰影。</span><span class="sxs-lookup"><span data-stu-id="84d28-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> <span data-ttu-id="84d28-114">這些陰影效果不會通過[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]文本呈現管道。</span><span class="sxs-lookup"><span data-stu-id="84d28-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="84d28-115">因此，使用這些效果時，會停用 ClearType。</span><span class="sxs-lookup"><span data-stu-id="84d28-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="84d28-116">下列範例示範套用至文字的實色延伸陰影效果。</span><span class="sxs-lookup"><span data-stu-id="84d28-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="84d28-117">在此情況下，陰影不會模糊。</span><span class="sxs-lookup"><span data-stu-id="84d28-117">In this case, the shadow is not blurred.</span></span>  
  
 ![具有柔和性&#61; 0 的文本陰影](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg)
  
 <span data-ttu-id="84d28-119">通過將<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>屬性設置為`0.0`（）來創建硬陰影，該屬性指示不使用模糊。</span><span class="sxs-lookup"><span data-stu-id="84d28-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="84d28-120">您可以通過修改<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>屬性來控制陰影的方向。</span><span class="sxs-lookup"><span data-stu-id="84d28-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="84d28-121">將此屬性的方向值設置為 和`0``360`之間的程度。</span><span class="sxs-lookup"><span data-stu-id="84d28-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="84d28-122">下圖顯示了屬性設置的方向<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>值。</span><span class="sxs-lookup"><span data-stu-id="84d28-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![陰影的 DropShadow 程度設定](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="84d28-124">下列程式碼範例示範如何建立強烈陰影。</span><span class="sxs-lookup"><span data-stu-id="84d28-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="84d28-125">使用模糊效果</span><span class="sxs-lookup"><span data-stu-id="84d28-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="84d28-126"><xref:System.Windows.Media.Effects.BlurBitmapEffect>可用於創建可放置在文本物件後面的類似陰影的效果。</span><span class="sxs-lookup"><span data-stu-id="84d28-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="84d28-127">套用至文字的模糊點陣圖效果會讓文字所有方向都平均模糊。</span><span class="sxs-lookup"><span data-stu-id="84d28-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="84d28-128">下列範例示範套用至文字的模糊效果。</span><span class="sxs-lookup"><span data-stu-id="84d28-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![使用 BlurBitmapEffect 的文字陰影](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="84d28-130">下列程式碼範例示範如何建立模糊效果。</span><span class="sxs-lookup"><span data-stu-id="84d28-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="84d28-131">使用平移轉換</span><span class="sxs-lookup"><span data-stu-id="84d28-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="84d28-132"><xref:System.Windows.Media.TranslateTransform>可用於創建可放置在文本物件後面的類似陰影的效果。</span><span class="sxs-lookup"><span data-stu-id="84d28-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="84d28-133">以下代碼示例使用 偏移<xref:System.Windows.Media.TranslateTransform>文本。</span><span class="sxs-lookup"><span data-stu-id="84d28-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="84d28-134">在此範例中，主要文字下方文字的略微位移複本會建立陰影效果。</span><span class="sxs-lookup"><span data-stu-id="84d28-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![使用 TranslateTransform 的文字陰影](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)
  
 <span data-ttu-id="84d28-136">下列程式碼範例示範如何建立陰影效果的轉換。</span><span class="sxs-lookup"><span data-stu-id="84d28-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
