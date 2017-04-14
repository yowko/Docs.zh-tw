---
title: "如何：使用邊框距離在 Windows Form 控制項周圍建立框線 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "控制項 [Windows Form], Margin 屬性"
  - "控制項 [Windows Form], 大綱"
  - "控制項 [Windows Form], Padding 屬性"
  - "Margin 屬性 [Windows Form]"
  - "邊界"
  - "邊界, Windows Form"
  - "Padding 屬性 [Windows Form]"
  - "填補, Windows Form"
ms.assetid: bac7ed4d-a163-4259-98bd-155a36345890
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：使用邊框距離在 Windows Form 控制項周圍建立框線
下列程式碼範例示範如何在 <xref:System.Windows.Forms.RichTextBox> 控制項周圍建立框線或外框。  此範例將 <xref:System.Windows.Forms.Panel> 控制項的 <xref:System.Windows.Forms.Padding> 屬性值設定為 5，並將子 <xref:System.Windows.Forms.RichTextBox> 控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle>。  <xref:System.Windows.Forms.Panel> 控制項的 <xref:System.Windows.Forms.Control.BackColor%2A> 是設定為 <xref:System.Drawing.Color.Blue%2A>，這會在 <xref:System.Windows.Forms.RichTextBox> 控制項周圍建立藍色的框線。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Forms.Padding>   
 [Windows Form 控制項的邊界和邊框距離](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)