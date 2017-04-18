---
title: "如何：將 TextBox 控制項設為唯讀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "唯讀 TextBox 控制項"
  - "唯讀 TextBox 控制項"
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：將 TextBox 控制項設為唯讀
這個範例顯示如何設定 <xref:System.Windows.Controls.TextBox> 控制項不允許使用者輸入或修改。  
  
## 範例  
 為了防止使用者修改 <xref:System.Windows.Controls.TextBox> 控制項的內容，請將 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> 屬性設定為 **true**。  
  
 [!code-xml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> 屬性 \(Attribute\) 只會影響使用者輸入，並不會影響 <xref:System.Windows.Controls.TextBox> 控制項之[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 描述中設定的文字，或透過 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性 \(Property\) 以程式設計方式設定的文字。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> 的預設值為 **false**。  
  
## 請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)