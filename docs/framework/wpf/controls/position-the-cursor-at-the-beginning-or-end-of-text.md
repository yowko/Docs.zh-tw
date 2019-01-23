---
title: HOW TO：將游標放置在 TextBox 控制項中文字的開頭或結尾
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: 2b280c6ea74a4b7a896f33a3552997a730d24a39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497614"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a>HOW TO：將游標放置在 TextBox 控制項中文字的開頭或結尾
此範例示範如何將資料指標的開頭或結尾的文字內容置於<xref:System.Windows.Controls.TextBox>控制項。  
  
## <a name="example"></a>範例  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]程式碼說明<xref:System.Windows.Controls.TextBox>控制，並將它指派名稱。  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a>範例  
 若要將游標放在內容的開頭<xref:System.Windows.Controls.TextBox>控制項，呼叫<xref:System.Windows.Controls.TextBox.Select%2A>方法並指定將選取範圍開始位置是 0，並選取項目長度為 0。  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a>範例  
 將游標的內容結尾處<xref:System.Windows.Controls.TextBox>控制項，呼叫<xref:System.Windows.Controls.TextBox.Select%2A>方法並指定相等的長度的文字內容，並選取項目長度為 0 的選取範圍開始位置。  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a>另請參閱
- [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
