---
title: "如何：處理 ContextMenuStrip Opening 事件 | Microsoft Docs"
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
  - "內容功能表, 事件處理"
  - "ContextMenuStrip 控制項 [Windows Form]"
  - "事件處理, 內容功能表"
  - "捷徑功能表, 事件處理"
  - "ToolStrip 控制項 [Windows Forms]"
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：處理 ContextMenuStrip Opening 事件
您可以藉由處理 <xref:System.Windows.Forms.ToolStripDropDown.Opening> 事件，自訂 <xref:System.Windows.Forms.ContextMenuStrip> 控制項的行為。  
  
## 範例  
 下列程式碼範例會示範如何處理 <xref:System.Windows.Forms.ToolStripDropDown.Opening> 事件。  事件處理常式會動態將項目加入至 <xref:System.Windows.Forms.ContextMenuStrip> 控制項。  如需完整的程式碼範例，請參閱[如何：以動態方式加入 ToolStrip 項目](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md)。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 將 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=fullName> 屬性設定為 `true` 以防止功能表開啟。  
  
## 請參閱  
 <xref:System.Windows.Forms.ContextMenuStrip>   
 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>   
 <xref:System.Windows.Forms.ToolStripDropDown>   
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)