---
title: "如何：在 TextBox 控制項中啟用定位字元 | Microsoft Docs"
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
  - "定位字元, 啟用"
  - "TextBox 控制項, 啟用定位字元"
ms.assetid: 14b1b064-61f7-4958-be63-88d85b868d03
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：在 TextBox 控制項中啟用定位字元
本範例顯示如何讓 <xref:System.Windows.Controls.TextBox> 控制項接受定位字元成為一般輸入。  
  
## 範例  
 若要讓 <xref:System.Windows.Controls.TextBox> 控制項接受定位字元做為輸入，請將 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsTab%2A> 屬性設為 **true**。  
  
 [!code-xml[TextBox_EnablingTab#_AcceptsTab](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_EnablingTab/CS/Window1.xaml#_acceptstab)]  
  
## 請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)