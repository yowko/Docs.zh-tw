---
title: "如何：偵測 TextBox 中的文字何時變更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92fc8995ab75cc25bac3bb21b1646052822c3721
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>如何：偵測 TextBox 中的文字何時變更
這個範例會示範一個方式來使用<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>事件以執行方法時中的文字<xref:System.Windows.Controls.TextBox>控制項已變更。  
  
 中的程式碼後置類別[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]包含<xref:System.Windows.Controls.TextBox>控制項，您想要監視的變更，插入每當呼叫方法<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>事件引發。  這個方法必須符合所預期的簽章<xref:System.Windows.Controls.TextChangedEventHandler>委派。  
  
 此事件處理常式會呼叫時的內容<xref:System.Windows.Controls.TextBox>控制項已變更，可能是由使用者或以程式設計的方式。  
  
 **注意：**時引發這個事件<xref:System.Windows.Controls.TextBox>控制項為建立，一開始填入文字。  
  
## <a name="example"></a>範例  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，定義您<xref:System.Windows.Controls.TextBox>控制項，指定<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>屬性值符合事件處理常式方法名稱。  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>範例  
 中的程式碼後置類別[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]包含<xref:System.Windows.Controls.TextBox>控制項，您想要監視的變更，插入每當呼叫方法<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>事件引發。  這個方法必須符合所預期的簽章<xref:System.Windows.Controls.TextChangedEventHandler>委派。  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 此事件處理常式會呼叫時的內容<xref:System.Windows.Controls.TextBox>控制項已變更，可能是由使用者或以程式設計的方式。  
  
 **注意：**時引發這個事件<xref:System.Windows.Controls.TextBox>控制項為建立，一開始填入文字。  
  
 註解  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
