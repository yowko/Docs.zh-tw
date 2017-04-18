---
title: "如何：將浮水印加入至 TextBox | Microsoft Docs"
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
  - "使用背景影像增加 TextBox 的可用性 [WPF]"
  - "在文字方塊內部顯示背景影像以協助使用者輸入 [WPF]"
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：將浮水印加入至 TextBox
下列範例顯示如何增加 <xref:System.Windows.Controls.TextBox> 的可用性，方式是在 <xref:System.Windows.Controls.TextBox> 內顯示說明背景影像，直到使用者輸入文字時才移除影像。  此外，當使用者移除輸入內容時會再度還原背景影像。  請參閱下圖。  
  
 ![具有背景影像的 TextBox](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing\_TextBox\_using\_background\_image")  
  
> [!NOTE]
>  本範例中使用背景影像而非簡單操作 <xref:System.Windows.Controls.TextBox> 的 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性的原因，是背景影像不會妨礙資料繫結。  
  
## 範例  
 [!code-xml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## 請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)