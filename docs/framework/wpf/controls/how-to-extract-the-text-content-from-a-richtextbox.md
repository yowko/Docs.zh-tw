---
title: HOW TO：擷取 RichTextBox 的文字內容
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
ms.openlocfilehash: 220da59ec893528c99014e9ec95fb185c461b291
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086113"
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a><span data-ttu-id="08b37-102">HOW TO：擷取 RichTextBox 的文字內容</span><span class="sxs-lookup"><span data-stu-id="08b37-102">How to: Extract the Text Content from a RichTextBox</span></span>
<span data-ttu-id="08b37-103">此範例示範如何擷取的內容<xref:System.Windows.Controls.RichTextBox>以純文字。</span><span class="sxs-lookup"><span data-stu-id="08b37-103">This example shows how to extract the contents of a <xref:System.Windows.Controls.RichTextBox> as plain text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08b37-104">範例</span><span class="sxs-lookup"><span data-stu-id="08b37-104">Example</span></span>  
 <span data-ttu-id="08b37-105">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]程式碼說明具名<xref:System.Windows.Controls.RichTextBox>具有簡單內容的控制項。</span><span class="sxs-lookup"><span data-stu-id="08b37-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a><span data-ttu-id="08b37-106">範例</span><span class="sxs-lookup"><span data-stu-id="08b37-106">Example</span></span>  
 <span data-ttu-id="08b37-107">下列程式碼會實作採用的方法<xref:System.Windows.Controls.RichTextBox>做為引數，並傳回字串，表示的純文字內容<xref:System.Windows.Controls.RichTextBox>。</span><span class="sxs-lookup"><span data-stu-id="08b37-107">The following code implements a method that takes a <xref:System.Windows.Controls.RichTextBox> as an argument, and returns a string representing the plain text contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="08b37-108">此方法會建立新<xref:System.Windows.Documents.TextRange>從內容<xref:System.Windows.Controls.RichTextBox>，並使用<xref:System.Windows.Documents.FlowDocument.ContentStart%2A>和<xref:System.Windows.Documents.FlowDocument.ContentEnd%2A>，表示要擷取之內容的範圍。</span><span class="sxs-lookup"><span data-stu-id="08b37-108">The method creates a new <xref:System.Windows.Documents.TextRange> from the contents of the <xref:System.Windows.Controls.RichTextBox>, using the <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> to indicate the range of the contents to extract.</span></span>  <span data-ttu-id="08b37-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> 並<xref:System.Windows.Documents.FlowDocument.ContentEnd%2A>每個屬性會傳回<xref:System.Windows.Documents.TextPointer>，且可供存取上的內容表示基礎 FlowDocument <xref:System.Windows.Controls.RichTextBox>。</span><span class="sxs-lookup"><span data-stu-id="08b37-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> properties each return a <xref:System.Windows.Documents.TextPointer>, and are accessible on the underlying FlowDocument that represents the contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  <span data-ttu-id="08b37-110"><xref:System.Windows.Documents.TextRange> 提供文字屬性，它會傳回的純文字部分<xref:System.Windows.Documents.TextRange>做為字串。</span><span class="sxs-lookup"><span data-stu-id="08b37-110"><xref:System.Windows.Documents.TextRange> provides a Text property, which returns the plain text portions of the <xref:System.Windows.Documents.TextRange> as a string.</span></span>  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a><span data-ttu-id="08b37-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08b37-111">See also</span></span>

- [<span data-ttu-id="08b37-112">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="08b37-112">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="08b37-113">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="08b37-113">TextBox Overview</span></span>](textbox-overview.md)
