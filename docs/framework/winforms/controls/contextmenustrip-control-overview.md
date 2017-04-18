---
title: "ContextMenuStrip 控制項概觀 | Microsoft Docs"
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
  - "ContextMenuStrip"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "內容功能表, ContextMenuStrip 控制項 [Windows Form]"
  - "ContextMenuStrip 控制項 [Windows Form], 關於 ContextMenuStrip 控制項"
  - "捷徑功能表, ContextMenuStrip 控制項 [Windows Form]"
ms.assetid: 9787cdb3-88f1-4198-972f-eefd9524ce39
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# ContextMenuStrip 控制項概觀
> [!NOTE]
>  <xref:System.Windows.Forms.ContextMenuStrip> 控制項會取代 <xref:System.Windows.Forms.ContextMenu> 控制項並加入其他功能，不過，也可以選擇保留 <xref:System.Windows.Forms.ContextMenu> 控制項，以提供回溯相容性 \(Backward Compatibility\) 以及未來使用。  
  
 當使用者按一下滑鼠右鍵時，捷徑功能表 \(亦稱為內容功能表\) 會顯示在滑鼠位置上。  快速鍵「*功能表*」會提供選項給滑鼠指標位置上的工作區或控制項。  
  
 <xref:System.Windows.Forms.ContextMenuStrip> 控制項的目的是與新的 <xref:System.Windows.Forms.ToolStrip> 和相關的控制項完美搭配，但您也可以輕鬆地將 <xref:System.Windows.Forms.ContextMenuStrip> 與其他控制項相關聯。  
  
 下表顯示重要的 <xref:System.Windows.Forms.ContextMenuStrip> 附屬類別。  
  
|類別|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|表示顯示在 <xref:System.Windows.Forms.MenuStrip> 或 <xref:System.Windows.Forms.ContextMenuStrip> 上的可選取選項。|  
|<xref:System.Windows.Forms.ToolStripDropDown>|代表允許使用者從清單選取單一項目的控制項，此份清單是使用者按一下 <xref:System.Windows.Forms.ToolStripDropDownButton> 或較高層級功能表項目時所顯示的清單。|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|提供衍生自 <xref:System.Windows.Forms.ToolStripItem> 的控制項的基本功能，當按一下這個控制項時會顯示下拉式項目。|  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 <xref:System.Windows.Forms.ToolStripDropDown>