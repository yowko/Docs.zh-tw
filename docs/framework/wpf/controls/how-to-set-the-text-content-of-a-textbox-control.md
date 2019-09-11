---
title: 作法：設定 TextBox 控制項的文字內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 2e2bc70b108991fd4e3c138bfac5bff942173e33
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856106"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="69894-102">HOW TO：設定 TextBox 控制項的文字內容</span><span class="sxs-lookup"><span data-stu-id="69894-102">How to: Set the Text Content of a TextBox Control</span></span>

<span data-ttu-id="69894-103">這個範例顯示如何使用<xref:System.Windows.Controls.TextBox.Text%2A>屬性來設定<xref:System.Windows.Controls.TextBox>控制項的初始文字內容。</span><span class="sxs-lookup"><span data-stu-id="69894-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>

> [!NOTE]
> <span data-ttu-id="69894-104">雖然此[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例的版本可以在`<TextBox.Text>`每個<xref:System.Windows.Controls.TextBox>按鈕<xref:System.Windows.Controls.TextBox>內容的文字周圍使用標記，但並不是<xref:System.Windows.Controls.TextBox.Text%2A>必要的，因為會將<xref:System.Windows.Markup.ContentPropertyAttribute>屬性套用至屬性.</span><span class="sxs-lookup"><span data-stu-id="69894-104">Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="69894-105">如需詳細資訊, 請參閱[XAML 總覽 (WPF)](../advanced/xaml-overview-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="69894-105">For more information, see [XAML Overview (WPF)](../advanced/xaml-overview-wpf.md).</span></span>

## <a name="example"></a><span data-ttu-id="69894-106">範例</span><span class="sxs-lookup"><span data-stu-id="69894-106">Example</span></span>

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a><span data-ttu-id="69894-107">範例</span><span class="sxs-lookup"><span data-stu-id="69894-107">Example</span></span>

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a><span data-ttu-id="69894-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69894-108">See also</span></span>

- [<span data-ttu-id="69894-109">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="69894-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="69894-110">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="69894-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
