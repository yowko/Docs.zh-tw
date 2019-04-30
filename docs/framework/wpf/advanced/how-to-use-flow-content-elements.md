---
title: HOW TO：使用動態內容項目
ms.date: 03/30/2017
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
ms.openlocfilehash: df591304736adf1725b2b4235149bd426fe15216
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052348"
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="8821b-102">HOW TO：使用動態內容項目</span><span class="sxs-lookup"><span data-stu-id="8821b-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="8821b-103">下列範例示範各種非固定格式內容項目和關聯屬性的宣告式使用方式。</span><span class="sxs-lookup"><span data-stu-id="8821b-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="8821b-104">示範的項目和屬性包括：</span><span class="sxs-lookup"><span data-stu-id="8821b-104">Elements and attributes demonstrated include:</span></span>  
  
- <span data-ttu-id="8821b-105"><xref:System.Windows.Documents.Bold> 項目</span><span class="sxs-lookup"><span data-stu-id="8821b-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
- <span data-ttu-id="8821b-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="8821b-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
- <span data-ttu-id="8821b-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="8821b-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
- <span data-ttu-id="8821b-108"><xref:System.Windows.Documents.Italic> 項目</span><span class="sxs-lookup"><span data-stu-id="8821b-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
- <span data-ttu-id="8821b-109"><xref:System.Windows.Documents.LineBreak> 項目</span><span class="sxs-lookup"><span data-stu-id="8821b-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
- <span data-ttu-id="8821b-110"><xref:System.Windows.Documents.List> 項目</span><span class="sxs-lookup"><span data-stu-id="8821b-110"><xref:System.Windows.Documents.List> element</span></span>  
  
- <span data-ttu-id="8821b-111"><xref:System.Windows.Documents.ListItem> 項目</span><span class="sxs-lookup"><span data-stu-id="8821b-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
- <span data-ttu-id="8821b-112"><xref:System.Windows.Documents.Paragraph> 項目</span><span class="sxs-lookup"><span data-stu-id="8821b-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
- <span data-ttu-id="8821b-113"><xref:System.Windows.Documents.Run> 項目</span><span class="sxs-lookup"><span data-stu-id="8821b-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
- <span data-ttu-id="8821b-114"><xref:System.Windows.Documents.Section> 項目</span><span class="sxs-lookup"><span data-stu-id="8821b-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
- <span data-ttu-id="8821b-115"><xref:System.Windows.Documents.Span> 項目</span><span class="sxs-lookup"><span data-stu-id="8821b-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
- <span data-ttu-id="8821b-116"><xref:System.Windows.Documents.Typography.Variants%2A> 屬性 （上標和下標）</span><span class="sxs-lookup"><span data-stu-id="8821b-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
- <span data-ttu-id="8821b-117"><xref:System.Windows.Documents.Underline> 項目</span><span class="sxs-lookup"><span data-stu-id="8821b-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="8821b-118">範例</span><span class="sxs-lookup"><span data-stu-id="8821b-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]
