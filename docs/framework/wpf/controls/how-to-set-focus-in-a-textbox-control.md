---
title: "如何：在 TextBox 控制項中設定焦點 | Microsoft Docs"
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
  - "焦點, 設定"
  - "TextBox 控制項, 設定焦點"
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：在 TextBox 控制項中設定焦點
本範例顯示如何使用 <xref:System.Windows.UIElement.Focus%2A> 方法，將焦點設在 <xref:System.Windows.Controls.TextBox> 控制項上。  
  
## 範例  
 下列 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例描述一個名為 *tbFocusMe* 的簡單 <xref:System.Windows.Controls.TextBox> 控制項  
  
 [!code-xml[TextBox_MiscCode#_TextBoxFocusXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## 範例  
 下列範例會呼叫 <xref:System.Windows.UIElement.Focus%2A> 方法，將焦點設在名為 *tbFocusMe* 的 <xref:System.Windows.Controls.TextBox> 控制項上。  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## 請參閱  
 <xref:System.Windows.UIElement.Focusable%2A>   
 <xref:System.Windows.UIElement.IsFocused%2A>   
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)