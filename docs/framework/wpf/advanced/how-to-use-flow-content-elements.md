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
ms.openlocfilehash: c1350a380e97631ac290e57de64fec696535fecc
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="60a9f-102">如何：使用非固定格式項目</span><span class="sxs-lookup"><span data-stu-id="60a9f-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="60a9f-103">下列範例示範各種非固定格式內容項目和關聯屬性的宣告式使用方式。</span><span class="sxs-lookup"><span data-stu-id="60a9f-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="60a9f-104">示範的項目和屬性包括：</span><span class="sxs-lookup"><span data-stu-id="60a9f-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="60a9f-105"><xref:System.Windows.Documents.Bold> 項目</span><span class="sxs-lookup"><span data-stu-id="60a9f-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="60a9f-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="60a9f-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="60a9f-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="60a9f-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="60a9f-108"><xref:System.Windows.Documents.Italic> 項目</span><span class="sxs-lookup"><span data-stu-id="60a9f-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="60a9f-109"><xref:System.Windows.Documents.LineBreak> 項目</span><span class="sxs-lookup"><span data-stu-id="60a9f-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="60a9f-110"><xref:System.Windows.Documents.List> 項目</span><span class="sxs-lookup"><span data-stu-id="60a9f-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="60a9f-111"><xref:System.Windows.Documents.ListItem> 項目</span><span class="sxs-lookup"><span data-stu-id="60a9f-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="60a9f-112"><xref:System.Windows.Documents.Paragraph> 項目</span><span class="sxs-lookup"><span data-stu-id="60a9f-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="60a9f-113"><xref:System.Windows.Documents.Run> 項目</span><span class="sxs-lookup"><span data-stu-id="60a9f-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="60a9f-114"><xref:System.Windows.Documents.Section> 項目</span><span class="sxs-lookup"><span data-stu-id="60a9f-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="60a9f-115"><xref:System.Windows.Documents.Span> 項目</span><span class="sxs-lookup"><span data-stu-id="60a9f-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="60a9f-116"><xref:System.Windows.Documents.Typography.Variants%2A>屬性 （上標和下標）</span><span class="sxs-lookup"><span data-stu-id="60a9f-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="60a9f-117"><xref:System.Windows.Documents.Underline> 項目</span><span class="sxs-lookup"><span data-stu-id="60a9f-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="60a9f-118">範例</span><span class="sxs-lookup"><span data-stu-id="60a9f-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]
