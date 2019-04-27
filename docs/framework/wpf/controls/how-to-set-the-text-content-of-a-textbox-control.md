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
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>HOW TO：設定 TextBox 控制項的文字內容
此範例示範如何使用<xref:System.Windows.Controls.TextBox.Text%2A>屬性來設定初始的文字內容<xref:System.Windows.Controls.TextBox>控制項。  
  
 **附註**雖然[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]版的範例可以使用`<TextBox.Text>`標記的每個按鈕的文字周圍<xref:System.Windows.Controls.TextBox>內容，您不需要因為<xref:System.Windows.Controls.TextBox>適用於<xref:System.Windows.Markup.ContentPropertyAttribute>屬性<xref:System.Windows.Controls.TextBox.Text%2A>屬性。 如需詳細資訊，請參閱 < [XAML 概觀 (WPF)](../advanced/xaml-overview-wpf.md)。  
  
## <a name="example"></a>範例  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a>範例  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a>另請參閱

- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
