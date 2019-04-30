---
title: HOW TO：使用 FlowDocument 資料行分隔屬性
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 27491b21da587fa198061ba52d8daed5d3f28de3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032031"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a><span data-ttu-id="1ab7a-102">HOW TO：使用 FlowDocument 資料行分隔屬性</span><span class="sxs-lookup"><span data-stu-id="1ab7a-102">How to: Use FlowDocument Column-Separating Attributes</span></span>
<span data-ttu-id="1ab7a-103">此範例示範如何使用的資料行分隔功能<xref:System.Windows.Documents.FlowDocument>。</span><span class="sxs-lookup"><span data-stu-id="1ab7a-103">This example shows how to use the column-separating features of a <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ab7a-104">範例</span><span class="sxs-lookup"><span data-stu-id="1ab7a-104">Example</span></span>  
 <span data-ttu-id="1ab7a-105">下列範例會定義<xref:System.Windows.Documents.FlowDocument>，並設定<xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>， <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>，和<xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="1ab7a-105">The following example defines a <xref:System.Windows.Documents.FlowDocument>, and sets the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes.</span></span>  <span data-ttu-id="1ab7a-106"><xref:System.Windows.Documents.FlowDocument>包含單一段落的範例內容。</span><span class="sxs-lookup"><span data-stu-id="1ab7a-106">The <xref:System.Windows.Documents.FlowDocument> contains a single paragraph of sample content.</span></span>  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 <span data-ttu-id="1ab7a-107">下圖顯示的效果<xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>， <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>，並<xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A>中呈現的屬性<xref:System.Windows.Documents.FlowDocument>。</span><span class="sxs-lookup"><span data-stu-id="1ab7a-107">The following figure shows the effects of the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes in a rendered <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 ![如果螢幕擷取畫面顯示的 FlowDocument Intra 屬性。](./media/how-to-use-flowdocument-column-separating-attributes/flowdocument-intra-column.png)
