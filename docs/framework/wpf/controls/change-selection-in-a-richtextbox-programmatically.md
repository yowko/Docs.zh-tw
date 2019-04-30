---
title: 以程式設計方式變更 RichTextBox 中的選項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- changing selections in a text box [WPF]
- changing selections in a RichTextBox [WPF]
ms.assetid: f1213205-1ad7-4cd2-b115-460173cc5aa3
ms.openlocfilehash: b8acfe7cde1fe5dae96cd6324f75c5b146be9ec9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001711"
---
# <a name="change-selection-in-a-richtextbox-programmatically"></a><span data-ttu-id="59121-102">以程式設計方式變更 RichTextBox 中的選項</span><span class="sxs-lookup"><span data-stu-id="59121-102">Change Selection in a RichTextBox Programmatically</span></span>
<span data-ttu-id="59121-103">此範例示範如何以程式設計方式變更目前的選取範圍中<xref:System.Windows.Controls.RichTextBox>。</span><span class="sxs-lookup"><span data-stu-id="59121-103">This example shows how to programmatically change the current selection in a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="59121-104">此選取項目會與相同使用者已選取使用使用者介面的內容。</span><span class="sxs-lookup"><span data-stu-id="59121-104">This selection is the same as if the user had selected the content by using the user interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59121-105">範例</span><span class="sxs-lookup"><span data-stu-id="59121-105">Example</span></span>  
 <span data-ttu-id="59121-106">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]程式碼說明具名<xref:System.Windows.Controls.RichTextBox>具有簡單內容的控制項。</span><span class="sxs-lookup"><span data-stu-id="59121-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml#changeselectionprogrammaticalyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="59121-107">範例</span><span class="sxs-lookup"><span data-stu-id="59121-107">Example</span></span>  
 <span data-ttu-id="59121-108">下列程式碼以程式設計方式選取一些任意的文字，當使用者按一下內<xref:System.Windows.Controls.RichTextBox>。</span><span class="sxs-lookup"><span data-stu-id="59121-108">The following code programmatically selects some arbitrary text when the user clicks inside the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml.cs#changeselectionprogrammaticalycodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/ChangeSelectionProgrammaticaly.xaml.vb#changeselectionprogrammaticalycodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="59121-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59121-109">See also</span></span>

- [<span data-ttu-id="59121-110">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="59121-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="59121-111">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="59121-111">TextBox Overview</span></span>](textbox-overview.md)
