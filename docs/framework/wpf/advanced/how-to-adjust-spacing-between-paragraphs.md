---
title: "如何：調整段落之間的間距"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b2d02e1513a0d8a3c31e4a13c9599666a4122a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a><span data-ttu-id="6e49c-102">如何：調整段落之間的間距</span><span class="sxs-lookup"><span data-stu-id="6e49c-102">How to: Adjust Spacing Between Paragraphs</span></span>
<span data-ttu-id="6e49c-103">此範例顯示如何調整或排除段落中非固定格式內容之間的間距。</span><span class="sxs-lookup"><span data-stu-id="6e49c-103">This example shows how to adjust or eliminate spacing between paragraphs in flow content.</span></span>  
  
 <span data-ttu-id="6e49c-104">在非固定格式內容的段落之間會出現額外空間是這些段落; 上設定的邊界的結果因此，可以控制段落間距調整邊界的段落。</span><span class="sxs-lookup"><span data-stu-id="6e49c-104">In flow content, extra space that appears between paragraphs is the result of margins set on these paragraphs; thus, the spacing between paragraphs can be controlled by adjusting the margins on those paragraphs.</span></span>  <span data-ttu-id="6e49c-105">若要完全消除兩個段落的額外間距，設定的邊界的段落**0**。</span><span class="sxs-lookup"><span data-stu-id="6e49c-105">To eliminate extra spacing between two paragraphs altogether, set the margins for the paragraphs to **0**.</span></span>  <span data-ttu-id="6e49c-106">若要達到整個段落的統一間距<xref:System.Windows.Documents.FlowDocument>，使用樣式設定來設定所有段落中的統一的邊界值<xref:System.Windows.Documents.FlowDocument>。</span><span class="sxs-lookup"><span data-stu-id="6e49c-106">To achieve uniform spacing between paragraphs throughout an entire <xref:System.Windows.Documents.FlowDocument>, use styling to set a uniform margin value for all paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="6e49c-107">請務必注意，兩個相鄰的段落的邊界會 「 摺疊 」 到較大的兩個邊界，而非倍。</span><span class="sxs-lookup"><span data-stu-id="6e49c-107">It is important to note that the margins for two adjacent paragraphs will "collapse" to the larger of the two margins, rather than doubling up.</span></span> <span data-ttu-id="6e49c-108">因此，如果兩個相鄰的段落分別有 20 像素和 40 像素的邊界，段落產生間距是 40 像素，較大的兩個邊界值。</span><span class="sxs-lookup"><span data-stu-id="6e49c-108">So, if two adjacent paragraphs have margins of 20 pixels and 40 pixels respectively, the resulting space between the paragraphs is 40 pixels, the larger of the two margin values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e49c-109">範例</span><span class="sxs-lookup"><span data-stu-id="6e49c-109">Example</span></span>  
 <span data-ttu-id="6e49c-110">下列範例會使用樣式將邊界設定所有<xref:System.Windows.Documents.Paragraph>中的項目<xref:System.Windows.Documents.FlowDocument>至**0**，其有效地排除段落中的額外間距<xref:System.Windows.Documents.FlowDocument>。</span><span class="sxs-lookup"><span data-stu-id="6e49c-110">The following example uses styling to set the margin for all <xref:System.Windows.Documents.Paragraph> elements in a <xref:System.Windows.Documents.FlowDocument> to **0**, which effectively eliminates extra spacing between paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
