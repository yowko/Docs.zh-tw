---
title: HOW TO：使用 FlowDocument 資料行分隔屬性
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 27491b21da587fa198061ba52d8daed5d3f28de3
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410897"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>HOW TO：使用 FlowDocument 資料行分隔屬性
此範例示範如何使用的資料行分隔功能<xref:System.Windows.Documents.FlowDocument>。  
  
## <a name="example"></a>範例  
 下列範例會定義<xref:System.Windows.Documents.FlowDocument>，並設定<xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>， <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>，和<xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A>屬性。  <xref:System.Windows.Documents.FlowDocument>包含單一段落的範例內容。  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 下圖顯示的效果<xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>， <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>，並<xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A>中呈現的屬性<xref:System.Windows.Documents.FlowDocument>。  
  
 ![如果螢幕擷取畫面顯示的 FlowDocument Intra 屬性。](./media/how-to-use-flowdocument-column-separating-attributes/flowdocument-intra-column.png)
