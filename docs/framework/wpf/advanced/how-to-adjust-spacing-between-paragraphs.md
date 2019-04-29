---
title: HOW TO：調整段落的間距
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: e2a6ba34e3ab15eb316671fef7c11bea03d53c73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777009"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a><span data-ttu-id="9253b-102">HOW TO：調整段落的間距</span><span class="sxs-lookup"><span data-stu-id="9253b-102">How to: Adjust Spacing Between Paragraphs</span></span>
<span data-ttu-id="9253b-103">此範例示範如何調整或排除在非固定格式內容中的段落之間的間距。</span><span class="sxs-lookup"><span data-stu-id="9253b-103">This example shows how to adjust or eliminate spacing between paragraphs in flow content.</span></span>  
  
 <span data-ttu-id="9253b-104">在非固定格式內容中顯示段落之間的額外空間是這些段落; 上設定的邊界的結果因此，可以藉由調整邊界的段落控制段落之間的間距。</span><span class="sxs-lookup"><span data-stu-id="9253b-104">In flow content, extra space that appears between paragraphs is the result of margins set on these paragraphs; thus, the spacing between paragraphs can be controlled by adjusting the margins on those paragraphs.</span></span>  <span data-ttu-id="9253b-105">若要完全排除這兩個段落的額外間距，設定 針對至段落的邊界**0**。</span><span class="sxs-lookup"><span data-stu-id="9253b-105">To eliminate extra spacing between two paragraphs altogether, set the margins for the paragraphs to **0**.</span></span>  <span data-ttu-id="9253b-106">若要達到統一整個段落之間的間距<xref:System.Windows.Documents.FlowDocument>，使用設為統一的邊界值中的所有段落的樣式<xref:System.Windows.Documents.FlowDocument>。</span><span class="sxs-lookup"><span data-stu-id="9253b-106">To achieve uniform spacing between paragraphs throughout an entire <xref:System.Windows.Documents.FlowDocument>, use styling to set a uniform margin value for all paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="9253b-107">請務必注意，兩個相鄰的段落的邊界會 「 摺疊 」 到較大的兩個邊界，而非向上加倍。</span><span class="sxs-lookup"><span data-stu-id="9253b-107">It is important to note that the margins for two adjacent paragraphs will "collapse" to the larger of the two margins, rather than doubling up.</span></span> <span data-ttu-id="9253b-108">因此，如果兩個相鄰的段落會分別有 20 個像素和 40 像素的邊界，段落之間產生的空間會是 40 像素，較大的兩個邊界值。</span><span class="sxs-lookup"><span data-stu-id="9253b-108">So, if two adjacent paragraphs have margins of 20 pixels and 40 pixels respectively, the resulting space between the paragraphs is 40 pixels, the larger of the two margin values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9253b-109">範例</span><span class="sxs-lookup"><span data-stu-id="9253b-109">Example</span></span>  
 <span data-ttu-id="9253b-110">下列範例會使用樣式來設定所有邊界<xref:System.Windows.Documents.Paragraph>中的項目<xref:System.Windows.Documents.FlowDocument>要**0**，這便能有效去除在段落之間的額外間距<xref:System.Windows.Documents.FlowDocument>。</span><span class="sxs-lookup"><span data-stu-id="9253b-110">The following example uses styling to set the margin for all <xref:System.Windows.Documents.Paragraph> elements in a <xref:System.Windows.Documents.FlowDocument> to **0**, which effectively eliminates extra spacing between paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
