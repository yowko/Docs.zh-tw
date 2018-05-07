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
ms.openlocfilehash: 37d636a5e35e9c52ca35ae558b60b5f32d63cabe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>如何：設定 TextBox 控制項的文字內容
這個範例示範如何使用<xref:System.Windows.Controls.TextBox.Text%2A>屬性來設定的初始文字內容<xref:System.Windows.Controls.TextBox>控制項。  
  
 **請注意**雖然[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例中的版本無法使用`<TextBox.Text>`標記每個按鈕的文字周圍<xref:System.Windows.Controls.TextBox>內容，則不需要因為<xref:System.Windows.Controls.TextBox>適用於<xref:System.Windows.Markup.ContentPropertyAttribute>屬性<xref:System.Windows.Controls.TextBox.Text%2A>屬性。 如需詳細資訊，請參閱[XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  
## <a name="example"></a>範例  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a>範例  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a>另請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
