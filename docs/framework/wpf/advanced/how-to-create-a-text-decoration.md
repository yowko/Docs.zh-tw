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
ms.openlocfilehash: cf3b3c3bcb75153a0be4f7ced03b38134b79a930
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185928"
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="35578-102">如何：建立文字裝飾</span><span class="sxs-lookup"><span data-stu-id="35578-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="35578-103">物件<xref:System.Windows.TextDecoration>是可以添加到文本的視覺修飾。</span><span class="sxs-lookup"><span data-stu-id="35578-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="35578-104">有四種類型的文本修飾：底線、基線、擊穿和過線。</span><span class="sxs-lookup"><span data-stu-id="35578-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="35578-105">下面的示例顯示文本修飾相對於文本的位置。</span><span class="sxs-lookup"><span data-stu-id="35578-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 ![文本修飾類型圖](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 <span data-ttu-id="35578-107">要向文本添加文本修飾，請創建物件<xref:System.Windows.TextDecoration>並修改其屬性。</span><span class="sxs-lookup"><span data-stu-id="35578-107">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="35578-108">使用<xref:System.Windows.TextDecoration.Location%2A>屬性指定文本修飾的顯示位置，如底線。</span><span class="sxs-lookup"><span data-stu-id="35578-108">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="35578-109">使用<xref:System.Windows.TextDecoration.Pen%2A>屬性指定文本修飾的外觀，如實心填充或漸變顏色。</span><span class="sxs-lookup"><span data-stu-id="35578-109">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="35578-110">如果不為<xref:System.Windows.TextDecoration.Pen%2A>屬性指定值，則修飾預設為與文本相同的顏色。</span><span class="sxs-lookup"><span data-stu-id="35578-110">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="35578-111">定義物件<xref:System.Windows.TextDecoration>後，將其添加到所需文本物件<xref:System.Windows.TextDecorations>的集合中。</span><span class="sxs-lookup"><span data-stu-id="35578-111">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="35578-112">下面的示例顯示了使用線性漸層畫筆和虛線筆進行樣式設置的文本修飾。</span><span class="sxs-lookup"><span data-stu-id="35578-112">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 ![具有線性漸層底線的文字裝飾](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 <span data-ttu-id="35578-114">該<xref:System.Windows.Documents.Hyperlink>物件是一個內聯級流內容元素，允許您在流內容中託管超連結。</span><span class="sxs-lookup"><span data-stu-id="35578-114">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="35578-115">預設情況下，<xref:System.Windows.Documents.Hyperlink>使用<xref:System.Windows.TextDecoration>物件顯示底線。</span><span class="sxs-lookup"><span data-stu-id="35578-115">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="35578-116"><xref:System.Windows.TextDecoration>物件可以執行密集型具現化，尤其是在有許多<xref:System.Windows.Documents.Hyperlink>物件時。</span><span class="sxs-lookup"><span data-stu-id="35578-116"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="35578-117">如果廣泛使用<xref:System.Windows.Documents.Hyperlink>元素，則可能需要考慮僅在觸發事件（如<xref:System.Windows.ContentElement.MouseEnter>事件）時顯示底線。</span><span class="sxs-lookup"><span data-stu-id="35578-117">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="35578-118">在下面的示例中，"我的 MSN"連結的底線是動態的 ，它僅在觸發<xref:System.Windows.ContentElement.MouseEnter>事件時才出現。</span><span class="sxs-lookup"><span data-stu-id="35578-118">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 ![顯示 TextDecoration 的超連結](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  

 <span data-ttu-id="35578-120">如需詳細資訊，請參閱[指定超連結是否要加上底線](how-to-specify-whether-a-hyperlink-is-underlined.md)。</span><span class="sxs-lookup"><span data-stu-id="35578-120">For more information, see [Specify Whether a Hyperlink is Underlined](how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35578-121">範例</span><span class="sxs-lookup"><span data-stu-id="35578-121">Example</span></span>  
 <span data-ttu-id="35578-122">在下面的代碼示例中，底線文本修飾使用預設字型值。</span><span class="sxs-lookup"><span data-stu-id="35578-122">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="35578-123">在下面的代碼示例中，使用筆的單色筆刷創建底線文本修飾。</span><span class="sxs-lookup"><span data-stu-id="35578-123">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="35578-124">在下面的代碼示例中，使用虛線筆的線性漸層畫筆創建底線文本修飾。</span><span class="sxs-lookup"><span data-stu-id="35578-124">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="35578-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35578-125">See also</span></span>

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="35578-126">指定超連結是否加上底線</span><span class="sxs-lookup"><span data-stu-id="35578-126">Specify Whether a Hyperlink is Underlined</span></span>](how-to-specify-whether-a-hyperlink-is-underlined.md)
