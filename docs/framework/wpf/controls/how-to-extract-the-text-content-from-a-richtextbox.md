---
title: 如何：擷取 RichTextBox 的文字內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], extracting
- RichTextBox control [WPF], extracting text content
- content [WPF], extracting
- extracting text content [WPF]
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
ms.openlocfilehash: 309fe15c76c17a79e11341f3a50c0bf5a7a2cc21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a>如何：擷取 RichTextBox 的文字內容
這個範例示範如何擷取的內容<xref:System.Windows.Controls.RichTextBox>以純文字。  
  
## <a name="example"></a>範例  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]程式碼說明具名<xref:System.Windows.Controls.RichTextBox>具有簡單內容的控制項。  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a>範例  
 下列程式碼會實作的方法會接受<xref:System.Windows.Controls.RichTextBox>做為引數，並傳回字串，代表純文字內容<xref:System.Windows.Controls.RichTextBox>。  
  
 此方法會建立新<xref:System.Windows.Documents.TextRange>的內容從<xref:System.Windows.Controls.RichTextBox>，並使用<xref:System.Windows.Documents.FlowDocument.ContentStart%2A>和<xref:System.Windows.Documents.FlowDocument.ContentEnd%2A>，表示要擷取的內容的範圍。  <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> 和<xref:System.Windows.Documents.FlowDocument.ContentEnd%2A>每個屬性會傳回<xref:System.Windows.Documents.TextPointer>，而且可以存取上的內容表示基礎 FlowDocument <xref:System.Windows.Controls.RichTextBox>。  <xref:System.Windows.Documents.TextRange> 提供文字屬性，傳回的純文字部分<xref:System.Windows.Documents.TextRange>做為字串。  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a>另請參閱  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)
