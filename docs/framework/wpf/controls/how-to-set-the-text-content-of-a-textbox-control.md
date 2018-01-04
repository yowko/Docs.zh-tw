---
title: "如何：設定 TextBox 控制項的文字內容"
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
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef354a986ee71cfa7a8e00a62905ee909d9cf30d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="fc548-102">如何：設定 TextBox 控制項的文字內容</span><span class="sxs-lookup"><span data-stu-id="fc548-102">How to: Set the Text Content of a TextBox Control</span></span>
<span data-ttu-id="fc548-103">這個範例示範如何使用<xref:System.Windows.Controls.TextBox.Text%2A>屬性來設定的初始文字內容<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="fc548-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 <span data-ttu-id="fc548-104">**請注意**雖然[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例中的版本無法使用`<TextBox.Text>`標記每個按鈕的文字周圍<xref:System.Windows.Controls.TextBox>內容，則不需要因為<xref:System.Windows.Controls.TextBox>適用於<xref:System.Windows.Markup.ContentPropertyAttribute>屬性<xref:System.Windows.Controls.TextBox.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="fc548-104">**Note** Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="fc548-105">如需詳細資訊，請參閱[XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="fc548-105">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc548-106">範例</span><span class="sxs-lookup"><span data-stu-id="fc548-106">Example</span></span>  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a><span data-ttu-id="fc548-107">範例</span><span class="sxs-lookup"><span data-stu-id="fc548-107">Example</span></span>  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a><span data-ttu-id="fc548-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="fc548-108">See Also</span></span>  
 [<span data-ttu-id="fc548-109">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="fc548-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="fc548-110">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="fc548-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
