---
title: 操作說明：將游標放置在 TextBox 控制項中文字的開頭或結尾
description: 瞭解如何將游標放在 Windows Presentation Foundation TextBox 控制項文字內容的開頭或結尾。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: afe8b11d032b5d61fa91cbf324f02cd8415d2ea8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167517"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a>操作說明：將游標放置在 TextBox 控制項中文字的開頭或結尾
這個範例示範如何將游標放在控制項文字內容的開頭或結尾 <xref:System.Windows.Controls.TextBox> 。  
  
## <a name="example"></a>範例  
 下列程式 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 代碼說明 <xref:System.Windows.Controls.TextBox> 控制項並為其指派名稱。  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a>範例  
 若要將游標放在控制項內容的開頭 <xref:System.Windows.Controls.TextBox> ，請呼叫 <xref:System.Windows.Controls.TextBox.Select%2A> 方法，並指定選取範圍開始位置為0，而選取範圍長度為0。  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a>範例  
 若要將游標放在控制項內容的結尾 <xref:System.Windows.Controls.TextBox> ，請呼叫 <xref:System.Windows.Controls.TextBox.Select%2A> 方法，並將選取範圍的開始位置指定為等於文字內容的長度，且選取範圍長度為0。  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a>另請參閱

- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
