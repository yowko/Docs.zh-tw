---
title: "如何：以程式設計的方式將項目插入文字"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Text Animation sample [WPF]
- elements [WPF], inserting into text
- inserting elements into text [WPF]
- TextPointer objects [WPF]
- text [WPF], inserting elements
ms.assetid: 97bd950a-25ac-4e42-a311-94b6420d4136
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b200489c4b7fb06f2eb98c0ec9c84da42f18a395
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-insert-an-element-into-text-programmatically"></a><span data-ttu-id="c52dc-102">如何：以程式設計的方式將項目插入文字</span><span class="sxs-lookup"><span data-stu-id="c52dc-102">How to: Insert an Element Into Text Programmatically</span></span>
<span data-ttu-id="c52dc-103">下列範例示範如何使用兩個<xref:System.Windows.Documents.TextPointer>物件，指定要套用的文字內的範圍<xref:System.Windows.Documents.Span>項目。</span><span class="sxs-lookup"><span data-stu-id="c52dc-103">The following example shows how to use two <xref:System.Windows.Documents.TextPointer> objects to specify a range within text to apply a <xref:System.Windows.Documents.Span> element to.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c52dc-104">範例</span><span class="sxs-lookup"><span data-stu-id="c52dc-104">Example</span></span>  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 <span data-ttu-id="c52dc-105">下圖顯示此範例的外觀。</span><span class="sxs-lookup"><span data-stu-id="c52dc-105">The illustration below shows what this example looks like.</span></span>  
  
 <span data-ttu-id="c52dc-106">![已套用至某一文字範圍的 Span 項目](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span><span class="sxs-lookup"><span data-stu-id="c52dc-106">![A Span element applied to a range of text](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52dc-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="c52dc-107">See Also</span></span>  
 [<span data-ttu-id="c52dc-108">非固定格式文件概觀</span><span class="sxs-lookup"><span data-stu-id="c52dc-108">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
