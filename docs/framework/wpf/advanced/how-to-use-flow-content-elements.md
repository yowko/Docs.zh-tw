---
title: "如何：使用非固定格式項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e637e114187d0864afe4211a45c346c1e5a449b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="60e89-102">如何：使用非固定格式項目</span><span class="sxs-lookup"><span data-stu-id="60e89-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="60e89-103">下列範例示範各種非固定格式內容項目和關聯屬性的宣告式使用方式。</span><span class="sxs-lookup"><span data-stu-id="60e89-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="60e89-104">示範的項目和屬性包括：</span><span class="sxs-lookup"><span data-stu-id="60e89-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="60e89-105"><xref:System.Windows.Documents.Bold> 項目</span><span class="sxs-lookup"><span data-stu-id="60e89-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="60e89-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="60e89-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="60e89-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="60e89-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="60e89-108"><xref:System.Windows.Documents.Italic> 項目</span><span class="sxs-lookup"><span data-stu-id="60e89-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="60e89-109"><xref:System.Windows.Documents.LineBreak> 項目</span><span class="sxs-lookup"><span data-stu-id="60e89-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="60e89-110"><xref:System.Windows.Documents.List> 項目</span><span class="sxs-lookup"><span data-stu-id="60e89-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="60e89-111"><xref:System.Windows.Documents.ListItem> 項目</span><span class="sxs-lookup"><span data-stu-id="60e89-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="60e89-112"><xref:System.Windows.Documents.Paragraph> 項目</span><span class="sxs-lookup"><span data-stu-id="60e89-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="60e89-113"><xref:System.Windows.Documents.Run> 項目</span><span class="sxs-lookup"><span data-stu-id="60e89-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="60e89-114"><xref:System.Windows.Documents.Section> 項目</span><span class="sxs-lookup"><span data-stu-id="60e89-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="60e89-115"><xref:System.Windows.Documents.Span> 項目</span><span class="sxs-lookup"><span data-stu-id="60e89-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="60e89-116"><xref:System.Windows.Documents.Typography.Variants%2A>屬性 （上標和下標）</span><span class="sxs-lookup"><span data-stu-id="60e89-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="60e89-117"><xref:System.Windows.Documents.Underline> 項目</span><span class="sxs-lookup"><span data-stu-id="60e89-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="60e89-118">範例</span><span class="sxs-lookup"><span data-stu-id="60e89-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]
