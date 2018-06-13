---
title: 如何：從 TextBox 取得線條集合
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: 64187527da3cfb97343e2036338822d479dd997a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552736"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>如何：從 TextBox 取得線條集合
這個範例示範如何取得集合中的文字行<xref:System.Windows.Controls.TextBox>。  
  
## <a name="example"></a>範例  
 下列範例顯示簡單的方法採用<xref:System.Windows.Controls.TextBox>做為引數，並傳回<xref:System.Collections.Specialized.StringCollection>包含中的文字行**文字方塊**。  <xref:System.Windows.Controls.TextBox.LineCount%2A>屬性用來判斷目前有多少行**文字方塊**，而<xref:System.Windows.Controls.TextBox.GetLineText%2A>方法可用來擷取每一行，並將它加入至線條的集合。  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>另請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
