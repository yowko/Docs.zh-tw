---
title: HOW TO：將 TextBox 控制項設為唯讀
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 7f24458eb98bd669d59f15c49d1d9e3beb6833b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229832"
---
# <a name="how-to-make-a-textbox-control-read-only"></a>HOW TO：將 TextBox 控制項設為唯讀
此範例示範如何設定<xref:System.Windows.Controls.TextBox>控制項不允許使用者輸入或修改。  
  
## <a name="example"></a>範例  
 若要防止使用者修改的內容<xref:System.Windows.Controls.TextBox>控制項，並設定<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>屬性設定為 **，則為 true**。  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>屬性會影響僅供使用者輸入，它不會影響文字中設定[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]popis<xref:System.Windows.Controls.TextBox>控制項或設定以程式設計方式透過文字<xref:System.Windows.Controls.TextBox.Text%2A>屬性。  
  
 預設值<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>已**false**。  
  
## <a name="see-also"></a>另請參閱

- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
