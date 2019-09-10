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
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>HOW TO：設定 TextBox 控制項的文字內容

這個範例顯示如何使用<xref:System.Windows.Controls.TextBox.Text%2A>屬性來設定<xref:System.Windows.Controls.TextBox>控制項的初始文字內容。

> [!NOTE]
> 雖然此[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例的版本可以在`<TextBox.Text>`每個<xref:System.Windows.Controls.TextBox>按鈕<xref:System.Windows.Controls.TextBox>內容的文字周圍使用標記，但並不是<xref:System.Windows.Controls.TextBox.Text%2A>必要的，因為會將<xref:System.Windows.Markup.ContentPropertyAttribute>屬性套用至屬性. 如需詳細資訊, 請參閱[XAML 總覽 (WPF)](../advanced/xaml-overview-wpf.md)。

## <a name="example"></a>範例

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>範例

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>另請參閱

- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
