---
title: HOW TO：建立多行 TextBox 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 29fb4c9498fe163c36e71680242d3ef8cf98c089
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001269"
---
# <a name="how-to-create-a-multiline-textbox-control"></a>HOW TO：建立多行 TextBox 控制項
此範例示範如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]來定義<xref:System.Windows.Controls.TextBox>會自動擴展以容納多行文字的控制項。  
  
## <a name="example"></a>範例  
 設定<xref:System.Windows.Controls.TextBox.TextWrapping%2A>屬性設定為**包裝**會導致輸入的文字自動換行至新行時的邊緣<xref:System.Windows.Controls.TextBox>達到控制項時，會自動展開<xref:System.Windows.Controls.TextBox>控制項以容納新的一行，如果必要。  
  
 設定<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>屬性設定為 **，則為 true** RETURN 鍵按下時，會自動再次展開要插入新行<xref:System.Windows.Controls.TextBox>以容納新的一行，如有必要。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>屬性新增至的捲軸<xref:System.Windows.Controls.TextBox>，如此的內容<xref:System.Windows.Controls.TextBox>捲動如果<xref:System.Windows.Controls.TextBox>擴充框架或視窗的大小超過。  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.TextWrapping>
- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
