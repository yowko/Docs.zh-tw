---
title: HOW TO：從 TextBox 取得文字行集合
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: b7b2f1c2e071388635fb50b1e3573fd7f44334dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224633"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>HOW TO：從 TextBox 取得文字行集合
此範例示範如何取得從文字行集合<xref:System.Windows.Controls.TextBox>。  
  
## <a name="example"></a>範例  
 下列範例顯示簡單的方法採用<xref:System.Windows.Controls.TextBox>做為引數，並傳回<xref:System.Collections.Specialized.StringCollection>包含中的文字行**TextBox**。  <xref:System.Windows.Controls.TextBox.LineCount%2A>屬性用來判斷目前的行數**TextBox**，和<xref:System.Windows.Controls.TextBox.GetLineText%2A>方法可用來擷取每一行，並將它新增至之線條的集合。  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>另請參閱

- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
