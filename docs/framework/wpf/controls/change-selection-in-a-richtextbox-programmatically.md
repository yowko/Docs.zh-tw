---
title: "以程式設計方式變更 RichTextBox 中的選項"
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
- changing selections in a text box [WPF]
- changing selections in a RichTextBox [WPF]
ms.assetid: f1213205-1ad7-4cd2-b115-460173cc5aa3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f645a5719425742ba02f8f9056ca788fd6fdb931
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="change-selection-in-a-richtextbox-programmatically"></a><span data-ttu-id="f1764-102">以程式設計方式變更 RichTextBox 中的選項</span><span class="sxs-lookup"><span data-stu-id="f1764-102">Change Selection in a RichTextBox Programmatically</span></span>
<span data-ttu-id="f1764-103">此範例示範如何以程式設計方式變更目前的選取範圍中<xref:System.Windows.Controls.RichTextBox>。</span><span class="sxs-lookup"><span data-stu-id="f1764-103">This example shows how to programmatically change the current selection in a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="f1764-104">此選項會與相同使用者已選取使用使用者介面的內容。</span><span class="sxs-lookup"><span data-stu-id="f1764-104">This selection is the same as if the user had selected the content by using the user interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1764-105">範例</span><span class="sxs-lookup"><span data-stu-id="f1764-105">Example</span></span>  
 <span data-ttu-id="f1764-106">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]程式碼說明具名<xref:System.Windows.Controls.RichTextBox>具有簡單內容的控制項。</span><span class="sxs-lookup"><span data-stu-id="f1764-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml#changeselectionprogrammaticalyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="f1764-107">範例</span><span class="sxs-lookup"><span data-stu-id="f1764-107">Example</span></span>  
 <span data-ttu-id="f1764-108">下列程式碼以程式設計方式選取某些任意文字，當使用者按一下內<xref:System.Windows.Controls.RichTextBox>。</span><span class="sxs-lookup"><span data-stu-id="f1764-108">The following code programmatically selects some arbitrary text when the user clicks inside the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml.cs#changeselectionprogrammaticalycodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/ChangeSelectionProgrammaticaly.xaml.vb#changeselectionprogrammaticalycodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="f1764-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="f1764-109">See Also</span></span>  
 [<span data-ttu-id="f1764-110">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="f1764-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="f1764-111">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="f1764-111">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
