---
title: 如何：建立多行 TextBox 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 9f4c9e637b686c82b4ec8a4a5d6d3a78d46f97c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553283"
---
# <a name="how-to-create-a-multiline-textbox-control"></a>如何：建立多行 TextBox 控制項
這個範例示範如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定義<xref:System.Windows.Controls.TextBox>會自動擴展以容納多行文字的控制項。  
  
## <a name="example"></a>範例  
 設定<xref:System.Windows.Controls.TextBox.TextWrapping%2A>屬性**包裝**會導致輸入的文字換行至新行時的邊緣<xref:System.Windows.Controls.TextBox>達到控制項時，自動展開<xref:System.Windows.Controls.TextBox>以包含新行的空間，如果控制項必要的。  
  
 設定<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>屬性**true**導致 RETURN 鍵按下時，再次自動展開要插入新行<xref:System.Windows.Controls.TextBox>來視需要加入新行的空間。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>屬性新增至捲軸<xref:System.Windows.Controls.TextBox>，如此的內容<xref:System.Windows.Controls.TextBox>可以捲動，即透過如果<xref:System.Windows.Controls.TextBox>展開超過框架或將它關閉的視窗。  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.TextWrapping>  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
