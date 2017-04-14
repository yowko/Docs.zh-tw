---
title: "如何：自動縮放 ToolStripTextBox 以填滿 ToolStrip 的剩餘寬度 (Windows Form) | Microsoft Docs"
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
  - "文字方塊, ToolStrip 控制項中自動縮放 [Windows Form]"
  - "ToolStrip 控制項 [Windows Forms], 自動縮放文字方塊"
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：自動縮放 ToolStripTextBox 以填滿 ToolStrip 的剩餘寬度 (Windows Form)
當您將 <xref:System.Windows.Forms.ToolStrip> 控制項的 <xref:System.Windows.Forms.ToolStrip.Stretch%2A> 屬性設定為 `true` 時，控制項會填滿其容器的兩端，並且會隨著其容器調整大小而調整大小。  在這個組態中，您可能會發現它非常有助於自動縮放控制項中的項目 \(例如：<xref:System.Windows.Forms.ToolStripTextBox>\) 以填滿可用的空間，並隨著控制項調整大小而調整大小。  例如，如果您想要實現類似於 Microsoft® Internet Explorer 中之位址列的外觀和行為，這個自動縮放功能是非常有用的。  
  
## 範例  
 下列程式碼範例將提供衍生自 <xref:System.Windows.Forms.ToolStripTextBox> 且名稱為 `ToolStripSpringTextBox` 的類別。  這個類別將覆寫 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> 方法，以計算在減去其他所有項目的寬度之後，父 <xref:System.Windows.Forms.ToolStrip> 控制項的可用寬度。  這個程式碼範例將同時提供 <xref:System.Windows.Forms.Form> 類別和 `Program` 類別，以示範新的行為。  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripTextBox>   
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=fullName>   
 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [如何：在 StatusStrip 中以互動方式使用 Spring 屬性](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)