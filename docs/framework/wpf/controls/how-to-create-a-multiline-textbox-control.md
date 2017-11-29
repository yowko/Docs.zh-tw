---
title: "如何：建立多行 TextBox 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 244eb38ea47bbd7376c2f8c6f5b2609fbd9c4330
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
