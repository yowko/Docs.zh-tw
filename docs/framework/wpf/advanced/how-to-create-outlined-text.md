---
title: HOW TO：建立外框文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: a06ef9adbd5740fee74be2e9d8d13a8a5bdc5b95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521474"
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="97395-102">HOW TO：建立外框文字</span><span class="sxs-lookup"><span data-stu-id="97395-102">How to: Create Outlined Text</span></span>
<span data-ttu-id="97395-103">在大部分情況下，當您要新增到文字字串中的裝飾您[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式中，您使用的以不連續的字元或圖像 （glyph） 的集合的文字。</span><span class="sxs-lookup"><span data-stu-id="97395-103">In most cases, when you are adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="97395-104">例如，您可以建立線形漸層筆刷，並將它套用至<xref:System.Windows.Controls.Control.Foreground%2A>屬性<xref:System.Windows.Controls.TextBox>物件。</span><span class="sxs-lookup"><span data-stu-id="97395-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="97395-105">當您顯示或編輯文字方塊中時，線性漸層筆刷會自動套用至目前集合中的文字字串的字元。</span><span class="sxs-lookup"><span data-stu-id="97395-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 <span data-ttu-id="97395-106">![以線性漸層筆刷顯示的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span><span class="sxs-lookup"><span data-stu-id="97395-106">![Text displayed with a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span></span>  
<span data-ttu-id="97395-107">線性漸層筆刷套用至文字方塊中的範例</span><span class="sxs-lookup"><span data-stu-id="97395-107">Example of a linear gradient brush applied to a text box</span></span>  
  
 <span data-ttu-id="97395-108">不過，您也可以轉換成文字<xref:System.Windows.Media.Geometry>物件，可讓您建立其他類型的視覺效果豐富的文字。</span><span class="sxs-lookup"><span data-stu-id="97395-108">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="97395-109">例如，您可以在其中建立<xref:System.Windows.Media.Geometry>物件根據文字字串的外框。</span><span class="sxs-lookup"><span data-stu-id="97395-109">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 <span data-ttu-id="97395-110">![以線性漸層筆刷繪製外框的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span><span class="sxs-lookup"><span data-stu-id="97395-110">![Text outline using a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span></span>  
<span data-ttu-id="97395-111">線性漸層筆刷套用至文字的外框幾何的範例</span><span class="sxs-lookup"><span data-stu-id="97395-111">Example of a linear gradient brush applied to the outline geometry of text</span></span>  
  
 <span data-ttu-id="97395-112">當文字轉換成<xref:System.Windows.Media.Geometry>物件時，它不再是字元集合，您無法修改文字字串中的字元。</span><span class="sxs-lookup"><span data-stu-id="97395-112">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="97395-113">不過，您可以修改其筆劃與填滿屬性來影響轉換文字的外觀。</span><span class="sxs-lookup"><span data-stu-id="97395-113">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="97395-114">筆劃是指轉換文字的外框，填滿是指轉換文字外框內的區域。</span><span class="sxs-lookup"><span data-stu-id="97395-114">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="97395-115">下列範例說明幾個方法可透過修改筆劃並填滿轉換的文字建立視覺效果。</span><span class="sxs-lookup"><span data-stu-id="97395-115">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 <span data-ttu-id="97395-116">![以不同的色彩填滿和筆劃的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span><span class="sxs-lookup"><span data-stu-id="97395-116">![Text with different colors for fill and stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span></span>  
<span data-ttu-id="97395-117">設定筆劃並填滿不同色彩的範例</span><span class="sxs-lookup"><span data-stu-id="97395-117">Example of setting stroke and fill to different colors</span></span>  
  
 <span data-ttu-id="97395-118">![影像筆刷套用至筆觸的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span><span class="sxs-lookup"><span data-stu-id="97395-118">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span></span>  
<span data-ttu-id="97395-119">影像筆刷套用至筆劃的範例</span><span class="sxs-lookup"><span data-stu-id="97395-119">Example of an image brush applied to the stroke</span></span>  
  
 <span data-ttu-id="97395-120">它也可修改的週框方塊矩形或反白顯示轉換的文字。</span><span class="sxs-lookup"><span data-stu-id="97395-120">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="97395-121">下列範例會說明建立視覺效果的方式，透過修改筆劃並反白顯示轉換的文字。</span><span class="sxs-lookup"><span data-stu-id="97395-121">The following example illustrates a way to creating visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 <span data-ttu-id="97395-122">![影像筆刷套用至筆觸的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span><span class="sxs-lookup"><span data-stu-id="97395-122">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span></span>  
<span data-ttu-id="97395-123">影像筆刷套用至筆劃並反白顯示的範例</span><span class="sxs-lookup"><span data-stu-id="97395-123">Example of an image brush applied to the stroke and highlight</span></span>  
  
## <a name="example"></a><span data-ttu-id="97395-124">範例</span><span class="sxs-lookup"><span data-stu-id="97395-124">Example</span></span>  
 <span data-ttu-id="97395-125">要轉換文字的索引鍵<xref:System.Windows.Media.Geometry>物件是使用<xref:System.Windows.Media.FormattedText>物件。</span><span class="sxs-lookup"><span data-stu-id="97395-125">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="97395-126">當您建立此物件之後時，您可以使用<xref:System.Windows.Media.FormattedText.BuildGeometry%2A>並<xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A>方法，以將文字轉換成<xref:System.Windows.Media.Geometry>物件。</span><span class="sxs-lookup"><span data-stu-id="97395-126">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="97395-127">第一種方法會傳回格式化文字; geometry第二個方法會傳回之幾何的格式化文字的週框方塊。</span><span class="sxs-lookup"><span data-stu-id="97395-127">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="97395-128">下列程式碼範例示範如何建立<xref:System.Windows.Media.FormattedText>物件並擷取格式化的文字和其週框方塊的幾何。</span><span class="sxs-lookup"><span data-stu-id="97395-128">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="97395-129">若要顯示所擷取<xref:System.Windows.Media.Geometry>物件，您需要存取<xref:System.Windows.Media.DrawingContext>顯示轉換的文字的物件。</span><span class="sxs-lookup"><span data-stu-id="97395-129">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that is displaying the converted text.</span></span> <span data-ttu-id="97395-130">在這些程式碼範例中，這是由建立衍生自的類別，以支援使用者定義轉換的自訂控制項物件。</span><span class="sxs-lookup"><span data-stu-id="97395-130">In these code examples, this is done by creating a custom control object that is derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="97395-131">若要顯示<xref:System.Windows.Media.Geometry>在自訂控制項中，物件所提供的覆寫<xref:System.Windows.UIElement.OnRender%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="97395-131">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="97395-132">覆寫的方法應該使用<xref:System.Windows.Media.DrawingContext.DrawGeometry%2A>方法來繪製<xref:System.Windows.Media.Geometry>物件。</span><span class="sxs-lookup"><span data-stu-id="97395-132">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  <span data-ttu-id="97395-133">範例自訂使用者控制項物件的來源，請參閱[OutlineTextControl.cs 的C#](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs)並[OutlineTextControl.vb Visual basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb)。</span><span class="sxs-lookup"><span data-stu-id="97395-133">For the source of the example custom user control object, see [OutlineTextControl.cs for C#](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) and [OutlineTextControl.vb for Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="97395-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97395-134">See also</span></span>
- [<span data-ttu-id="97395-135">繪製格式化的文字</span><span class="sxs-lookup"><span data-stu-id="97395-135">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
