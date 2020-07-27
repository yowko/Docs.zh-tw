---
title: 如何：在 TextBox 控制項中設定焦點
description: 瞭解如何使用 Focus 方法，將焦點設定在 Windows Presentation Foundation TextBox 控制項上。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: e107c22a3c5b701e02cbc8506d10fa35ee15c79d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168058"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a>如何：在 TextBox 控制項中設定焦點
這個範例示範如何使用 <xref:System.Windows.UIElement.Focus%2A> 方法，將焦點設定在控制項上 <xref:System.Windows.Controls.TextBox> 。  
  
## <a name="example"></a>範例  
 下列 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例說明 <xref:System.Windows.Controls.TextBox> 名為*tbFocusMe*的簡單控制項  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a>範例  
 下列範例會呼叫 <xref:System.Windows.UIElement.Focus%2A> 方法，以將焦點設定為 <xref:System.Windows.Controls.TextBox> 名稱為*tbFocusMe*的控制項。  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
