---
title: HOW TO：從 TextBox 取得線條集合
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: a63470c6f0db72340f482bf638910685aa3f461f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561760"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>HOW TO：從 TextBox 取得線條集合
此範例示範如何取得從文字行集合<xref:System.Windows.Controls.TextBox>。  
  
## <a name="example"></a>範例  
 下列範例顯示簡單的方法採用<xref:System.Windows.Controls.TextBox>做為引數，並傳回<xref:System.Collections.Specialized.StringCollection>包含中的文字行**TextBox**。  <xref:System.Windows.Controls.TextBox.LineCount%2A>屬性用來判斷目前的行數**TextBox**，和<xref:System.Windows.Controls.TextBox.GetLineText%2A>方法可用來擷取每一行，並將它新增至之線條的集合。  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>另請參閱
- [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
