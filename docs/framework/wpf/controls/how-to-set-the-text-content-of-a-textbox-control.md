---
title: HOW TO：設定 TextBox 控制項的文字內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: da91e27b804d649f5b8010bc9d7c074425be26f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024140"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="adc7c-102">HOW TO：設定 TextBox 控制項的文字內容</span><span class="sxs-lookup"><span data-stu-id="adc7c-102">How to: Set the Text Content of a TextBox Control</span></span>
<span data-ttu-id="adc7c-103">此範例示範如何使用<xref:System.Windows.Controls.TextBox.Text%2A>屬性來設定初始的文字內容<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="adc7c-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 <span data-ttu-id="adc7c-104">**附註**雖然[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]版的範例可以使用`<TextBox.Text>`標記的每個按鈕的文字周圍<xref:System.Windows.Controls.TextBox>內容，您不需要因為<xref:System.Windows.Controls.TextBox>適用於<xref:System.Windows.Markup.ContentPropertyAttribute>屬性<xref:System.Windows.Controls.TextBox.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="adc7c-104">**Note** Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="adc7c-105">如需詳細資訊，請參閱 < [XAML 概觀 (WPF)](../advanced/xaml-overview-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="adc7c-105">For more information, see [XAML Overview (WPF)](../advanced/xaml-overview-wpf.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="adc7c-106">範例</span><span class="sxs-lookup"><span data-stu-id="adc7c-106">Example</span></span>  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a><span data-ttu-id="adc7c-107">範例</span><span class="sxs-lookup"><span data-stu-id="adc7c-107">Example</span></span>  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a><span data-ttu-id="adc7c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adc7c-108">See also</span></span>

- [<span data-ttu-id="adc7c-109">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="adc7c-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="adc7c-110">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="adc7c-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
