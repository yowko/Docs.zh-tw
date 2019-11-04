---
title: 如何：設定 TextBox 控制項的文字內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 9b16f2d99295a28725255361b0be3ef7f4245fd2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459298"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>如何：設定 TextBox 控制項的文字內容

這個範例示範如何使用 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性來設定 <xref:System.Windows.Controls.TextBox> 控制項的初始文字內容。

> [!NOTE]
> 雖然範例的 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 版本可以在每個按鈕的 <xref:System.Windows.Controls.TextBox> 內容文字周圍使用 `<TextBox.Text>` 標記，但並不是必要的，因為 <xref:System.Windows.Controls.TextBox> 會將 <xref:System.Windows.Markup.ContentPropertyAttribute> 屬性套用至 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性。 如需詳細資訊，請參閱[XAML 總覽（WPF）](../../../desktop-wpf/fundamentals/xaml.md)。

## <a name="example"></a>範例

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>範例

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>請參閱

- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
