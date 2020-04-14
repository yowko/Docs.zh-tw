---
title: 如何：建立外框文字
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
ms.openlocfilehash: 86bfa396a2aa44eb511c014687501d60e170a396
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278921"
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="22282-102">如何:建立大綱文字</span><span class="sxs-lookup"><span data-stu-id="22282-102">How to: Create outlined text</span></span>

<span data-ttu-id="22282-103">在大多數情況下,當您在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式中向文字字串添加修飾時,您將使用文本作為離散字元或字形的集合。</span><span class="sxs-lookup"><span data-stu-id="22282-103">In most cases, when you're adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="22282-104">例如,您可以創建線性漸變畫筆並將其應用於<xref:System.Windows.Controls.Control.Foreground%2A><xref:System.Windows.Controls.TextBox>物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="22282-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="22282-105">顯示或編輯文字框時,線性漸變畫筆將自動應用於文字字串中的當前字元集。</span><span class="sxs-lookup"><span data-stu-id="22282-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 ![以線性漸層筆刷顯示的文字](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 <span data-ttu-id="22282-107">但是,您還可以將文本轉換為<xref:System.Windows.Media.Geometry>對象,從而創建其他類型的視覺豐富的文本。</span><span class="sxs-lookup"><span data-stu-id="22282-107">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="22282-108">例如,可以基於文本字串的<xref:System.Windows.Media.Geometry>輪廓創建物件。</span><span class="sxs-lookup"><span data-stu-id="22282-108">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 ![以線性漸層筆刷繪製外框的文字](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 <span data-ttu-id="22282-110">將文字轉換為物件時<xref:System.Windows.Media.Geometry>,它不再是字元的集合,無法修改文本字串中的字元。</span><span class="sxs-lookup"><span data-stu-id="22282-110">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="22282-111">不過，您可以修改其筆劃與填滿屬性來影響轉換文字的外觀。</span><span class="sxs-lookup"><span data-stu-id="22282-111">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="22282-112">筆劃是指轉換文字的外框，填滿是指轉換文字外框內的區域。</span><span class="sxs-lookup"><span data-stu-id="22282-112">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="22282-113">以下範例說明了透過修改描邊和填充轉換文本來創建視覺效果的幾種方法。</span><span class="sxs-lookup"><span data-stu-id="22282-113">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 ![使用不同填色和筆觸色彩的文字](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![影像筆刷套用至筆觸的文字](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 <span data-ttu-id="22282-116">還可以修改轉換文本的邊界框矩形或高光。</span><span class="sxs-lookup"><span data-stu-id="22282-116">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="22282-117">下面的範例說明了透過修改轉換文本的描邊和高光來創建視覺效果的方法。</span><span class="sxs-lookup"><span data-stu-id="22282-117">The following example illustrates a way to create visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 ![套用影像筆刷描邊和高光的文字](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a><span data-ttu-id="22282-119">範例</span><span class="sxs-lookup"><span data-stu-id="22282-119">Example</span></span>  
 <span data-ttu-id="22282-120">將文字轉換為<xref:System.Windows.Media.Geometry>對象的鍵是<xref:System.Windows.Media.FormattedText>使用該 物件。</span><span class="sxs-lookup"><span data-stu-id="22282-120">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="22282-121">建立此物件後,可以使用<xref:System.Windows.Media.FormattedText.BuildGeometry%2A>和<xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A>方法將文本轉換為<xref:System.Windows.Media.Geometry>物件。</span><span class="sxs-lookup"><span data-stu-id="22282-121">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="22282-122">第一種方法返回格式化文本的幾何體;第二種方法返回格式化文本的邊界框的幾何體。</span><span class="sxs-lookup"><span data-stu-id="22282-122">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="22282-123">以下代碼示例演示如何創建<xref:System.Windows.Media.FormattedText>對象並檢索格式化文本及其邊界框的幾何體。</span><span class="sxs-lookup"><span data-stu-id="22282-123">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="22282-124">為了顯示檢索到<xref:System.Windows.Media.Geometry>的物件,您需要存<xref:System.Windows.Media.DrawingContext>取 顯示轉換文本的物件。</span><span class="sxs-lookup"><span data-stu-id="22282-124">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that's displaying the converted text.</span></span> <span data-ttu-id="22282-125">在這些代碼示例中,通過創建從支援使用者定義的呈現的類派生的自定義控制項物件來實現此訪問。</span><span class="sxs-lookup"><span data-stu-id="22282-125">In these code examples, this access is achieved by creating a custom control object that's derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="22282-126">要在<xref:System.Windows.Media.Geometry>自定義控制項中顯示物件,請<xref:System.Windows.UIElement.OnRender%2A>為方法提供重寫。</span><span class="sxs-lookup"><span data-stu-id="22282-126">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="22282-127">重寫的方法應使用<xref:System.Windows.Media.DrawingContext.DrawGeometry%2A>方法<xref:System.Windows.Media.Geometry>繪製 物件。</span><span class="sxs-lookup"><span data-stu-id="22282-127">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  <span data-ttu-id="22282-128">有關範例自定義使用者控制件物件的源,請參閱[C# 和](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs)[大綱文本控制.vb 的 OutlineTextControl.cs。](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb)</span><span class="sxs-lookup"><span data-stu-id="22282-128">For the source of the example custom user control object, see [OutlineTextControl.cs for C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) and [OutlineTextControl.vb for Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="22282-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22282-129">See also</span></span>

- [<span data-ttu-id="22282-130">繪製格式化的文字</span><span class="sxs-lookup"><span data-stu-id="22282-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
