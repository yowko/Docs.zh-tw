---
title: 如何：建立文字裝飾
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: c16073dd2413c1258f4875ac4118e0656d29b171
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545405"
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="27ea7-102">如何：建立文字裝飾</span><span class="sxs-lookup"><span data-stu-id="27ea7-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="27ea7-103">A<xref:System.Windows.TextDecoration>物件是視覺裝飾，您可以加入文字。</span><span class="sxs-lookup"><span data-stu-id="27ea7-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="27ea7-104">文字裝飾的四種類型： 底線、 基準、 刪除線和頂線。</span><span class="sxs-lookup"><span data-stu-id="27ea7-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="27ea7-105">下列範例顯示相對於文字的文字裝飾的位置。</span><span class="sxs-lookup"><span data-stu-id="27ea7-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 <span data-ttu-id="27ea7-106">![文字裝飾位置的圖表](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span><span class="sxs-lookup"><span data-stu-id="27ea7-106">![Diagram of text decoration locations](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span></span>  
<span data-ttu-id="27ea7-107">文字裝飾類型的範例</span><span class="sxs-lookup"><span data-stu-id="27ea7-107">Example of text decoration types</span></span>  
  
 <span data-ttu-id="27ea7-108">若要加入文字的文字裝飾，請建立<xref:System.Windows.TextDecoration>物件，並修改其屬性。</span><span class="sxs-lookup"><span data-stu-id="27ea7-108">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="27ea7-109">使用<xref:System.Windows.TextDecoration.Location%2A>屬性來指定文字裝飾的出現位置，例如底線。</span><span class="sxs-lookup"><span data-stu-id="27ea7-109">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="27ea7-110">使用<xref:System.Windows.TextDecoration.Pen%2A>屬性來指定文字裝飾，例如純色填滿或漸層色彩的外觀。</span><span class="sxs-lookup"><span data-stu-id="27ea7-110">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="27ea7-111">如果您未指定的值<xref:System.Windows.TextDecoration.Pen%2A>屬性，為相同的色彩做為文字的裝飾預設值。</span><span class="sxs-lookup"><span data-stu-id="27ea7-111">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="27ea7-112">一旦定義了<xref:System.Windows.TextDecoration>物件、 將它加入<xref:System.Windows.TextDecorations>想要的文字之物件的集合。</span><span class="sxs-lookup"><span data-stu-id="27ea7-112">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="27ea7-113">下列範例示範設定線性漸層筆刷與虛線的畫筆樣式的文字裝飾。</span><span class="sxs-lookup"><span data-stu-id="27ea7-113">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 <span data-ttu-id="27ea7-114">![線性漸層底線的文字裝飾](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span><span class="sxs-lookup"><span data-stu-id="27ea7-114">![Text decoration with linear gradient underline](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span></span>  
<span data-ttu-id="27ea7-115">範例中的底線樣式以線性漸層筆刷和虛線的畫筆</span><span class="sxs-lookup"><span data-stu-id="27ea7-115">Example of an underline styled with a linear gradient brush and dashed pen</span></span>  
  
 <span data-ttu-id="27ea7-116"><xref:System.Windows.Documents.Hyperlink>物件是可讓您將主機動態內容內的超連結的內嵌層級流動內容項目。</span><span class="sxs-lookup"><span data-stu-id="27ea7-116">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="27ea7-117">根據預設，<xref:System.Windows.Documents.Hyperlink>使用<xref:System.Windows.TextDecoration>物件，以顯示底線。</span><span class="sxs-lookup"><span data-stu-id="27ea7-117">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="27ea7-118"><xref:System.Windows.TextDecoration> 物件可以是具現化，耗用的效能，特別是如果您有許多<xref:System.Windows.Documents.Hyperlink>物件。</span><span class="sxs-lookup"><span data-stu-id="27ea7-118"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="27ea7-119">若要大量使用<xref:System.Windows.Documents.Hyperlink>項目，您可能要考慮這類觸發事件時，才顯示底線<xref:System.Windows.ContentElement.MouseEnter>事件。</span><span class="sxs-lookup"><span data-stu-id="27ea7-119">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="27ea7-120">在下列範例中，"My MSN 」 連結的底線是動態的它只會<xref:System.Windows.ContentElement.MouseEnter>觸發事件。</span><span class="sxs-lookup"><span data-stu-id="27ea7-120">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="27ea7-121">![顯示 Textdecoration 的超連結](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="27ea7-121">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="27ea7-122">定義與 Textdecoration 的超連結</span><span class="sxs-lookup"><span data-stu-id="27ea7-122">Hyperlinks defined with TextDecorations</span></span>  
  
 <span data-ttu-id="27ea7-123">如需詳細資訊，請參閱[指定超連結是否要加上底線](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)。</span><span class="sxs-lookup"><span data-stu-id="27ea7-123">For more information, see [Specify Whether a Hyperlink is Underlined](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27ea7-124">範例</span><span class="sxs-lookup"><span data-stu-id="27ea7-124">Example</span></span>  
 <span data-ttu-id="27ea7-125">在下列程式碼範例中，底線文字裝飾會使用預設字型值。</span><span class="sxs-lookup"><span data-stu-id="27ea7-125">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="27ea7-126">在下列程式碼範例中，使用畫筆的單色筆刷建立底線文字裝飾。</span><span class="sxs-lookup"><span data-stu-id="27ea7-126">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="27ea7-127">在下列程式碼範例中，底線文字裝飾會建立與虛線畫筆線性漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="27ea7-127">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="27ea7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27ea7-128">See Also</span></span>  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [<span data-ttu-id="27ea7-129">指定超連結是否要加上底線</span><span class="sxs-lookup"><span data-stu-id="27ea7-129">Specify Whether a Hyperlink is Underlined</span></span>](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
