---
title: HOW TO：建立含陰影的文字
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 4d200aa980e8f2e6d22291669dfb07db54a5f0c0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370668"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="88dd6-102">HOW TO：建立含陰影的文字</span><span class="sxs-lookup"><span data-stu-id="88dd6-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="88dd6-103">本節中的範例示範如何建立所顯示文字的陰影效果。</span><span class="sxs-lookup"><span data-stu-id="88dd6-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88dd6-104">範例</span><span class="sxs-lookup"><span data-stu-id="88dd6-104">Example</span></span>  
 <span data-ttu-id="88dd6-105"><xref:System.Windows.Media.Effects.DropShadowEffect>物件可讓您建立各種不同的下拉式陰影效果[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="88dd6-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="88dd6-106">下列範例示範套用至文字的延伸陰影效果。</span><span class="sxs-lookup"><span data-stu-id="88dd6-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="88dd6-107">在此情況下，陰影是柔邊陰影，表示陰影色彩模糊。</span><span class="sxs-lookup"><span data-stu-id="88dd6-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 <span data-ttu-id="88dd6-108">![文字陰影濃淡&#61;0.25](./media/shadowtext01.jpg "ShadowText01")</span><span class="sxs-lookup"><span data-stu-id="88dd6-108">![Text shadow with Softness &#61; 0.25](./media/shadowtext01.jpg "ShadowText01")</span></span>  
<span data-ttu-id="88dd6-109">含柔邊陰影的文字範例</span><span class="sxs-lookup"><span data-stu-id="88dd6-109">Example of text with a soft shadow</span></span>  
  
 <span data-ttu-id="88dd6-110">您可以設定來控制陰影寬度<xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="88dd6-110">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="88dd6-111">值為`4.0`表示陰影寬度 4 像素。</span><span class="sxs-lookup"><span data-stu-id="88dd6-111">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="88dd6-112">您可以控制的柔和度，或藉由修改陰影模糊<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="88dd6-112">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="88dd6-113">值為`0.0`表示不模糊。</span><span class="sxs-lookup"><span data-stu-id="88dd6-113">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="88dd6-114">下列程式碼範例示範如何建立柔邊陰影。</span><span class="sxs-lookup"><span data-stu-id="88dd6-114">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="88dd6-115">這些陰影效果不會通過[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]文字轉譯管線。</span><span class="sxs-lookup"><span data-stu-id="88dd6-115">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="88dd6-116">因此，使用這些效果時，會停用 ClearType。</span><span class="sxs-lookup"><span data-stu-id="88dd6-116">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="88dd6-117">下列範例示範套用至文字的實色延伸陰影效果。</span><span class="sxs-lookup"><span data-stu-id="88dd6-117">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="88dd6-118">在此情況下，陰影不會模糊。</span><span class="sxs-lookup"><span data-stu-id="88dd6-118">In this case, the shadow is not blurred.</span></span>  
  
 <span data-ttu-id="88dd6-119">![文字陰影濃淡&#61;0](./media/shadowtext02.jpg "ShadowText02")</span><span class="sxs-lookup"><span data-stu-id="88dd6-119">![Text shadow with Softness &#61; 0](./media/shadowtext02.jpg "ShadowText02")</span></span>  
<span data-ttu-id="88dd6-120">含強烈陰影的文字範例</span><span class="sxs-lookup"><span data-stu-id="88dd6-120">Example of text with a hard shadow</span></span>  
  
 <span data-ttu-id="88dd6-121">您可以設定來建立強烈陰影<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>屬性設`0.0`，這表示，不使用模糊的。</span><span class="sxs-lookup"><span data-stu-id="88dd6-121">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="88dd6-122">您可以修改來控制陰影的方向<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="88dd6-122">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="88dd6-123">設定這個屬性的方向值之間的度數`0`和`360`。</span><span class="sxs-lookup"><span data-stu-id="88dd6-123">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="88dd6-124">下圖顯示的方向值<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>屬性設定。</span><span class="sxs-lookup"><span data-stu-id="88dd6-124">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 <span data-ttu-id="88dd6-125">![陰影的 DropShadow 程度設定](./media/shadowtext08.png "ShadowText08")</span><span class="sxs-lookup"><span data-stu-id="88dd6-125">![DropShadow degree setting of shadow](./media/shadowtext08.png "ShadowText08")</span></span>  
<span data-ttu-id="88dd6-126">DropShadow 方向圖</span><span class="sxs-lookup"><span data-stu-id="88dd6-126">DropShadow Direction diagram</span></span>  
  
 <span data-ttu-id="88dd6-127">下列程式碼範例示範如何建立強烈陰影。</span><span class="sxs-lookup"><span data-stu-id="88dd6-127">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="88dd6-128">使用模糊效果</span><span class="sxs-lookup"><span data-stu-id="88dd6-128">Using a Blur Effect</span></span>  
 <span data-ttu-id="88dd6-129">A<xref:System.Windows.Media.Effects.BlurBitmapEffect>可用來建立可以放在文字物件後面的類似陰影效果。</span><span class="sxs-lookup"><span data-stu-id="88dd6-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="88dd6-130">套用至文字的模糊點陣圖效果會讓文字所有方向都平均模糊。</span><span class="sxs-lookup"><span data-stu-id="88dd6-130">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="88dd6-131">下列範例示範套用至文字的模糊效果。</span><span class="sxs-lookup"><span data-stu-id="88dd6-131">The following example shows a blur effect applied to text.</span></span>  
  
 <span data-ttu-id="88dd6-132">![使用 BlurBitmapEffect 的文字陰影](./media/shadowtext06.jpg "ShadowText06")</span><span class="sxs-lookup"><span data-stu-id="88dd6-132">![Text shadow using a BlurBitmapEffect](./media/shadowtext06.jpg "ShadowText06")</span></span>  
<span data-ttu-id="88dd6-133">含模糊效果的文字範例</span><span class="sxs-lookup"><span data-stu-id="88dd6-133">Example of text with a blur effect</span></span>  
  
 <span data-ttu-id="88dd6-134">下列程式碼範例示範如何建立模糊效果。</span><span class="sxs-lookup"><span data-stu-id="88dd6-134">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="88dd6-135">使用平移轉換</span><span class="sxs-lookup"><span data-stu-id="88dd6-135">Using a Translate Transform</span></span>  
 <span data-ttu-id="88dd6-136">A<xref:System.Windows.Media.TranslateTransform>可用來建立可以放在文字物件後面的類似陰影效果。</span><span class="sxs-lookup"><span data-stu-id="88dd6-136">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="88dd6-137">下列程式碼範例使用<xref:System.Windows.Media.TranslateTransform>來位移文字。</span><span class="sxs-lookup"><span data-stu-id="88dd6-137">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="88dd6-138">在此範例中，主要文字下方文字的略微位移複本會建立陰影效果。</span><span class="sxs-lookup"><span data-stu-id="88dd6-138">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 <span data-ttu-id="88dd6-139">![使用 TranslateTransform 的文字陰影](./media/shadowtext07.jpg "ShadowText07")</span><span class="sxs-lookup"><span data-stu-id="88dd6-139">![Text shadow using a TranslateTransform](./media/shadowtext07.jpg "ShadowText07")</span></span>  
<span data-ttu-id="88dd6-140">使用陰影效果轉換的文字範例</span><span class="sxs-lookup"><span data-stu-id="88dd6-140">Example of text using a transform for a shadow effect</span></span>  
  
 <span data-ttu-id="88dd6-141">下列程式碼範例示範如何建立陰影效果的轉換。</span><span class="sxs-lookup"><span data-stu-id="88dd6-141">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
