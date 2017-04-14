---
title: "MainMenu 元件概觀 (Windows Form) | Microsoft Docs"
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
  - "MenuItem"
  - "MainMenu"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "MainMenu 控制項 [Windows Form], 關於 MainMenu 控制項"
  - "功能表"
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# MainMenu 元件概觀 (Windows Form)
> [!IMPORTANT]
>  雖然 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.ContextMenuStrip> 會取代和加入功能至舊版的 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 控制項，但是會保留 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 以提供回溯相容性 \(Backward Compatibility\) 和未來使用 \(如果您選擇要用\)。  
  
 Windows Form <xref:System.Windows.Forms.MainMenu> 元件會顯示執行階段的功能表。  主功能表的所有子功能表和個別項目都是 <xref:System.Windows.Forms.MenuItem> 物件。  
  
## 主要屬性  
 藉由將 <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> 屬性設定為 `true`，您可將功能表項目指定為預設項目。  當按一下功能表時，預設項目會以粗體文字顯示。  功能表項目的 <xref:System.Windows.Forms.MenuItem.Checked%2A> 屬性可為 `true` 或 `false`，分別指示是否已選取功能表項目。  這個功能表項目的 <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> 屬性，客製選擇項目的外觀；如果 <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> 設定為 `true`，選項按鈕會在此項目旁顯示；如果 <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> 設定為 `false`，在項目旁會有勾選符號顯示。  
  
## 請參閱  
 <xref:System.Windows.Forms.MainMenu>   
 <xref:System.Windows.Forms.Menu>   
 <xref:System.Windows.Forms.MenuItem>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>   
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)