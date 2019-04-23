---
title: HOW TO：儲存、載入和列印 RichTextBox 內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- saving RichTextBox controls [WPF]
- printing RichTextBox controls [WPF]
- loading RichTextBox controls [WPF]
- RichTextBox control [WPF], saving
- RichTextBox control [WPF], printing
- RichTextBox control [WPF], loading
ms.assetid: ffb113d3-c68a-47ca-8ac0-882283f38326
ms.openlocfilehash: 90581bee7815dafd44c3cae18a8af7394fee1e9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072453"
---
# <a name="how-to-save-load-and-print-richtextbox-content"></a><span data-ttu-id="fcb56-102">HOW TO：儲存、載入和列印 RichTextBox 內容</span><span class="sxs-lookup"><span data-stu-id="fcb56-102">How to: Save, Load, and Print RichTextBox Content</span></span>
<span data-ttu-id="fcb56-103">下列範例示範如何將儲存的內容<xref:System.Windows.Controls.RichTextBox>檔案，以載入該內容的恢復為<xref:System.Windows.Controls.RichTextBox>，以及列印內容。</span><span class="sxs-lookup"><span data-stu-id="fcb56-103">The following example shows how to save content of a <xref:System.Windows.Controls.RichTextBox> to a file, load that content back into the <xref:System.Windows.Controls.RichTextBox>, and print the contents.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcb56-104">範例</span><span class="sxs-lookup"><span data-stu-id="fcb56-104">Example</span></span>  
 <span data-ttu-id="fcb56-105">以下是此範例的標記。</span><span class="sxs-lookup"><span data-stu-id="fcb56-105">Below is the markup for the example.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="fcb56-106">範例</span><span class="sxs-lookup"><span data-stu-id="fcb56-106">Example</span></span>  
 <span data-ttu-id="fcb56-107">以下是此範例的程式碼後置。</span><span class="sxs-lookup"><span data-stu-id="fcb56-107">Below is the code behind for the example.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="fcb56-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcb56-108">See also</span></span>

- [<span data-ttu-id="fcb56-109">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="fcb56-109">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="fcb56-110">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="fcb56-110">TextBox Overview</span></span>](textbox-overview.md)
