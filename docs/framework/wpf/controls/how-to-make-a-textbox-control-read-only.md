---
title: HOW TO：將 TextBox 控制項設為唯讀
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 3784471020210f995c8bb0a377d56a2466d97da1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364522"
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
