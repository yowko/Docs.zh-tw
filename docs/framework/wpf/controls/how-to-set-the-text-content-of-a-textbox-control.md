---
title: 如何：設定 TextBox 控制項的文字內容
description: 瞭解如何使用 Text 屬性來設定 Windows Presentation Foundation TextBox 控制項的初始文字內容。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 41efb69e297b3c6fdb1203c358dcc72d7a9f806f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168039"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="004ba-103">如何：設定 TextBox 控制項的文字內容</span><span class="sxs-lookup"><span data-stu-id="004ba-103">How to: Set the Text Content of a TextBox Control</span></span>

<span data-ttu-id="004ba-104">這個範例顯示如何使用 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性來設定控制項的初始文字內容 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="004ba-104">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>

> [!NOTE]
> <span data-ttu-id="004ba-105">雖然此 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例的版本可以在 `<TextBox.Text>` 每個按鈕內容的文字周圍使用標記 <xref:System.Windows.Controls.TextBox> ，但並不是必要的，因為會將 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Markup.ContentPropertyAttribute> 屬性套用至 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="004ba-105">Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="004ba-106">如需詳細資訊，請參閱[XAML 總覽（WPF）](../../../desktop-wpf/fundamentals/xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="004ba-106">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span></span>

## <a name="example"></a><span data-ttu-id="004ba-107">範例</span><span class="sxs-lookup"><span data-stu-id="004ba-107">Example</span></span>

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a><span data-ttu-id="004ba-108">範例</span><span class="sxs-lookup"><span data-stu-id="004ba-108">Example</span></span>

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a><span data-ttu-id="004ba-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="004ba-109">See also</span></span>

- [<span data-ttu-id="004ba-110">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="004ba-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="004ba-111">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="004ba-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
