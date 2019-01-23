---
title: HOW TO：在 TextBox 控制項中設定焦點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: 1ab7fa5f5ce895d163e3db3dd020fee3f29b7153
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590704"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a>HOW TO：在 TextBox 控制項中設定焦點
此範例示範如何使用<xref:System.Windows.UIElement.Focus%2A>方法，以將焦點設定在<xref:System.Windows.Controls.TextBox>控制項。  
  
## <a name="example"></a>範例  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例說明簡單<xref:System.Windows.Controls.TextBox>控制項，名為*tbFocusMe*  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a>範例  
 下列範例會呼叫<xref:System.Windows.UIElement.Focus%2A>方法，以將焦點設<xref:System.Windows.Controls.TextBox>具有名稱控制項*tbFocusMe*。  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
