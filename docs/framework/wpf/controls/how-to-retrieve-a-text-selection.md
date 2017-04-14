---
title: "如何：擷取文字選取項目 | Microsoft Docs"
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
  - "擷取文字"
  - "文字, 擷取"
  - "TextBox 控制項, 擷取文字"
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：擷取文字選取項目
此範例顯示如何使用 <xref:System.Windows.Controls.TextBox.SelectedText%2A> 屬性擷取使用者在 <xref:System.Windows.Controls.TextBox> 控制項中選取的文字。  
  
## 範例  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例顯示如何定義包含要選取之部分文字的 <xref:System.Windows.Controls.TextBox> 控制項，以及含有指定 <xref:System.Windows.Controls.Button.OnClick%2A> 方法的 <xref:System.Windows.Controls.Button> 控制項。  
  
 此範例會使用具有相關 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式的按鈕來擷取文字選取項目。  當使用者按一下按鈕時，<xref:System.Windows.Controls.Button.OnClick%2A> 方法即會將文字方塊中的所選文字複製到字串中。  據以擷取文字選取項目的特定情況 \(按一下按鈕\) 以及針對該選取所執行的動作 \(將文字選取項目複製到字串中\)，皆可輕易地修改以因應各種案例的需要。  
  
 [!code-xml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## 範例  
 下列 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 範例顯示此範例之 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中定義的按鈕所適用的 <xref:System.Windows.Controls.Button.OnClick%2A> 事件處理常式。  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## 請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)