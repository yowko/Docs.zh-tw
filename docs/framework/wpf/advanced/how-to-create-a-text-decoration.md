---
title: HOW TO：建立文字裝飾
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
ms.openlocfilehash: a142604fdb36ec6f85e9411b37077bfffff587d4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363913"
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="6642d-102">HOW TO：建立文字裝飾</span><span class="sxs-lookup"><span data-stu-id="6642d-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="6642d-103">A<xref:System.Windows.TextDecoration>物件是您可以新增至文字的視覺裝飾。</span><span class="sxs-lookup"><span data-stu-id="6642d-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="6642d-104">有四種類型的文字裝飾： 底線、 基準、 刪除線和頂線。</span><span class="sxs-lookup"><span data-stu-id="6642d-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="6642d-105">下列範例顯示的文字裝飾，相對於文字的位置。</span><span class="sxs-lookup"><span data-stu-id="6642d-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 <span data-ttu-id="6642d-106">![文字裝飾位置的圖表](./media/textdecoration01.gif "TextDecoration01")</span><span class="sxs-lookup"><span data-stu-id="6642d-106">![Diagram of text decoration locations](./media/textdecoration01.gif "TextDecoration01")</span></span>  
<span data-ttu-id="6642d-107">文字裝飾型別的範例</span><span class="sxs-lookup"><span data-stu-id="6642d-107">Example of text decoration types</span></span>  
  
 <span data-ttu-id="6642d-108">若要加入文字裝飾的文字，建立<xref:System.Windows.TextDecoration>物件，並修改其屬性。</span><span class="sxs-lookup"><span data-stu-id="6642d-108">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="6642d-109">使用<xref:System.Windows.TextDecoration.Location%2A>屬性來指定文字裝飾的出現位置，例如底線。</span><span class="sxs-lookup"><span data-stu-id="6642d-109">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="6642d-110">使用<xref:System.Windows.TextDecoration.Pen%2A>屬性來指定文字裝飾，例如純色填滿或漸層色彩的外觀。</span><span class="sxs-lookup"><span data-stu-id="6642d-110">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="6642d-111">如果您未指定的值<xref:System.Windows.TextDecoration.Pen%2A>屬性，則裝飾會預設為相同的文字色彩。</span><span class="sxs-lookup"><span data-stu-id="6642d-111">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="6642d-112">一旦您已定義<xref:System.Windows.TextDecoration>物件，將它新增至<xref:System.Windows.TextDecorations>想要的文字物件的集合。</span><span class="sxs-lookup"><span data-stu-id="6642d-112">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="6642d-113">下列範例顯示線性漸層筆刷與虛線的畫筆設定樣式的文字裝飾。</span><span class="sxs-lookup"><span data-stu-id="6642d-113">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 <span data-ttu-id="6642d-114">![使用線性漸層底線的文字裝飾](./media/textdecoration02.png "TextDecoration02")</span><span class="sxs-lookup"><span data-stu-id="6642d-114">![Text decoration with linear gradient underline](./media/textdecoration02.png "TextDecoration02")</span></span>  
<span data-ttu-id="6642d-115">範例中的底線樣式線性漸層筆刷和虛線的畫筆</span><span class="sxs-lookup"><span data-stu-id="6642d-115">Example of an underline styled with a linear gradient brush and dashed pen</span></span>  
  
 <span data-ttu-id="6642d-116"><xref:System.Windows.Documents.Hyperlink>物件是內嵌層級非固定格式內容項目，可讓您將非固定格式內容內超連結。</span><span class="sxs-lookup"><span data-stu-id="6642d-116">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="6642d-117">根據預設，<xref:System.Windows.Documents.Hyperlink>使用<xref:System.Windows.TextDecoration>物件，以顯示底線。</span><span class="sxs-lookup"><span data-stu-id="6642d-117">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="6642d-118"><xref:System.Windows.TextDecoration> 物件可以具現化，需要大量的效能，特別是如果您有許多<xref:System.Windows.Documents.Hyperlink>物件。</span><span class="sxs-lookup"><span data-stu-id="6642d-118"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="6642d-119">若要大量使用<xref:System.Windows.Documents.Hyperlink>項目，您可能要考慮這類觸發事件時，才顯示底線<xref:System.Windows.ContentElement.MouseEnter>事件。</span><span class="sxs-lookup"><span data-stu-id="6642d-119">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="6642d-120">在下列範例中，「 我的 MSN 」 連結，底線是動態的它才會出現<xref:System.Windows.ContentElement.MouseEnter>觸發事件。</span><span class="sxs-lookup"><span data-stu-id="6642d-120">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="6642d-121">![顯示 Textdecoration 的超](./media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="6642d-121">![Hyperlinks displaying TextDecorations](./media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="6642d-122">定義與 Textdecoration 的超連結</span><span class="sxs-lookup"><span data-stu-id="6642d-122">Hyperlinks defined with TextDecorations</span></span>  
  
 <span data-ttu-id="6642d-123">如需詳細資訊，請參閱[指定超連結是否要加上底線](how-to-specify-whether-a-hyperlink-is-underlined.md)。</span><span class="sxs-lookup"><span data-stu-id="6642d-123">For more information, see [Specify Whether a Hyperlink is Underlined](how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6642d-124">範例</span><span class="sxs-lookup"><span data-stu-id="6642d-124">Example</span></span>  
 <span data-ttu-id="6642d-125">在下列程式碼範例中，底線文字裝飾會使用預設字型值。</span><span class="sxs-lookup"><span data-stu-id="6642d-125">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="6642d-126">在下列程式碼範例中，底線文字裝飾會使用畫筆的單色筆刷。</span><span class="sxs-lookup"><span data-stu-id="6642d-126">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="6642d-127">在下列程式碼範例中，底線文字裝飾會以虛線的畫筆線性漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="6642d-127">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="6642d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6642d-128">See also</span></span>
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="6642d-129">指定超連結是否要加上底線</span><span class="sxs-lookup"><span data-stu-id="6642d-129">Specify Whether a Hyperlink is Underlined</span></span>](how-to-specify-whether-a-hyperlink-is-underlined.md)
