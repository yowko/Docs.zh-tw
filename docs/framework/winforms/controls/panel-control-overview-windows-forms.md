---
title: "Panel 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Panel"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "群組控制項, Panel 控制項"
  - "Panel 控制項 [Windows Form], 關於 Panel 控制項"
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Panel 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.Panel> 控制項可用來提供其他控制項的可識別群組。  通常，您會使用面板 \(Panel\)，依功能來細分一個表單。  例如，您可能有一張指定郵寄選項的訂單，例如要使用哪個夜間貨運。  將所有的選項集中在一個面板中，可讓使用者有邏輯的視覺提示。  在設計階段時，所有的控制項都可以輕易地移動 — 當您移動 <xref:System.Windows.Forms.Panel> 控制項時，其內所含的所有控制項也會移動。  您可以透過面板的 <xref:System.Windows.Forms.Control.Controls%2A> 屬性來存取群組在面板中的控制項。  這個屬性會傳回 <xref:System.Windows.Forms.Control> 執行個體的集合，因此您通常必須將這種方法所擷取的控制項強制轉型為特定型別。  
  
## Panel 和 GroupBox 的比較  
 <xref:System.Windows.Forms.Panel> 控制項類似 <xref:System.Windows.Forms.GroupBox> 控制項；然而，只有 <xref:System.Windows.Forms.Panel> 控制項可以擁有捲軸，而只有 <xref:System.Windows.Forms.GroupBox> 控制項顯示標題。  
  
## 主要屬性  
 若要顯示捲軸，請將 <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> 屬性設定為 `true`。  您也可以設定 <xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.BackgroundImage%2A> 和 <xref:System.Windows.Forms.Panel.BorderStyle%2A> 屬性來自訂面板外觀。  如需 <xref:System.Windows.Forms.Control.BackColor%2A> 和 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性的詳細資訊，請參閱 [如何：設定面板背景](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)。  <xref:System.Windows.Forms.Panel.BorderStyle%2A> 屬性決定面板的外框是否沒有框線 \(<xref:System.Windows.Forms.BorderStyle>\)、清楚的線條 \(<xref:System.Windows.Forms.BorderStyle>\) 還是有陰影的線條 \(<xref:System.Windows.Forms.BorderStyle>\)。  
  
## 請參閱  
 <xref:System.Windows.Forms.Panel>   
 [GroupBox 控制項](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)   
 [如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)   
 [如何：使用設計工具設定 Windows Form 面板的背景](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)