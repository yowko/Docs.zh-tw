---
title: "如何：將 TextBox 控制項設為唯讀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36116346b389dac7e9783e69d9bcd79573b4bf75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-a-textbox-control-read-only"></a>如何：將 TextBox 控制項設為唯讀
這個範例示範如何設定<xref:System.Windows.Controls.TextBox>控制項不允許使用者輸入或修改。  
  
## <a name="example"></a>範例  
 若要修改的內容時，防止使用者<xref:System.Windows.Controls.TextBox>控制，請設定<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>屬性設定為**true**。  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>屬性會影響只有使用者輸入，則不會影響文字中設定[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]描述<xref:System.Windows.Controls.TextBox>控制項或設定以程式設計方式透過文字<xref:System.Windows.Controls.TextBox.Text%2A>屬性。  
  
 預設值<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>是**false**。  
  
## <a name="see-also"></a>另請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
