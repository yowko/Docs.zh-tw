---
title: "ContextMenu 元件概觀 (Windows Form) | Microsoft Docs"
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
  - "ContextMenu"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "內容功能表, ContextMenu 元件"
  - "ContextMenu 元件 [Windows Form], 關於 ContextMenu 元件"
  - "捷徑功能表, ContextMenu 元件"
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# ContextMenu 元件概觀 (Windows Form)
> [!IMPORTANT]
>  雖然 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.ContextMenuStrip> 會取代和加入功能至舊版的 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 控制項，但是會保留 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 以提供回溯相容性 \(Backward Compatibility\) 和未來使用 \(如果您選擇要用\)。  
  
 利用 Windows Form <xref:System.Windows.Forms.ContextMenu> 元件，您可以提供捷徑功能表，供使用者輕鬆選取與所選物件關聯的常用命令。  捷徑功能表中的項目通常是出現在應用程式其他地方的主功能表項目子集。  通常使用者只要按一下滑鼠右鍵，即可存取捷徑功能表。  在 Windows Form 上，捷徑功能表是與控制項關聯。  
  
## 主要屬性  
 您可以將控制項的 <xref:System.Windows.Forms.Control.ContextMenu%2A> 屬性設定為 <xref:System.Windows.Forms.ContextMenu> 元件，這麼做就可建立捷徑功能表與控制項的關聯。  單一捷徑功能表可以和多個控制項建立關聯，但是每個控制項只能有一個捷徑功能表。  
  
 <xref:System.Windows.Forms.ContextMenu> 元件的主要屬性是 <xref:System.Windows.Forms.Menu.MenuItems%2A> 屬性。  您可以加入功能表項目，方法是用程式設計方式來建立 <xref:System.Windows.Forms.MenuItem> 物件，然後將這些物件加入至捷徑功能表的 <xref:System.Windows.Forms.Menu.MenuItemCollection>。  由於捷徑功能表中的項目通常都源自於其他功能表，因此將項目加入捷徑功能表最常使用的方法就是複製它們。  
  
## 請參閱  
 <xref:System.Windows.Forms.ContextMenu>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>