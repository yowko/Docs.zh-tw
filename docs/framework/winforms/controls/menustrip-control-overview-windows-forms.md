---
title: "MenuStrip 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "MenuStrip"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "功能表, 建立"
  - "MenuStrip 控制項 [Windows Form], 關於 MenuStrip 控制項"
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# MenuStrip 控制項概觀 (Windows Form)
功能表藉由保留通用主題所群組的命令，對使用者公開功能。  
  
 在這個版本的 Visual Studio 和 .NET Framework 中，<xref:System.Windows.Forms.MenuStrip> 是新的控制項。  利用這個控制項，可以輕鬆建立功能表，此功能表與 Microsoft Office 中所找到的功能表類似。  
  
 <xref:System.Windows.Forms.MenuStrip> 控制項支援多重文件介面 \(MDI\) 與功能表合併、工具提示和溢位。  您可以加入便捷鍵、快速鍵、核取記號、影像和分隔線，來加強功能表的使用性和可讀性。  
  
 <xref:System.Windows.Forms.MenuStrip> 控制項會取代 <xref:System.Windows.Forms.MainMenu> 控制項並加入其他功能，不過，也可以選擇保留 <xref:System.Windows.Forms.MainMenu> 控制項，以提供回溯相容性 \(Backward Compatibility\) 以及未來使用。  
  
## 使用 MenuStrip 控制項的方法  
 <xref:System.Windows.Forms.MenuStrip> 控制項的用途包括：  
  
-   建立容易自訂且經常使用的功能表，這個功能表應該支援進階使用者介面和配置功能，例如文字和影像的排序及對齊方式、拖放作業、MDI、溢位和存取功能表命令時的替代模式。  
  
-   支援一般的作業系統外觀和行為。  
  
-   以處理其他控制項事件的方式，來處理所有容器和被收納項目共同的事件。  
  
 下表顯示 <xref:System.Windows.Forms.MenuStrip> 及其相關類別的一些重要屬性：  
  
|屬性|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|取得或設定 <xref:System.Windows.Forms.ToolStripMenuItem>，其用來顯示 MDI 子表單的清單。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=fullName>|取得或設定在 MDI 應用程式中子功能表如何與父功能表合併。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=fullName>|取得或設定 MDI 應用程式中某一功能表之合併項目的位置。|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=fullName>|取得或設定值，指出此表單是否為 MDI 子表單的容器。|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|取得或設定值，指出是否顯示 <xref:System.Windows.Forms.MenuStrip> 的工具提示。|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|取得或設定值，指出 <xref:System.Windows.Forms.MenuStrip> 是否支援溢位功能。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|取得或設定與 <xref:System.Windows.Forms.ToolStripMenuItem> 關聯的快速鍵。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|取得或設定值，指出 <xref:System.Windows.Forms.ToolStripMenuItem> 的旁邊是否顯示與 <xref:System.Windows.Forms.ToolStripMenuItem> 關聯的快速鍵。|  
  
 下表顯示重要的 <xref:System.Windows.Forms.MenuStrip> 附屬類別。  
  
|類別|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|表示顯示在 <xref:System.Windows.Forms.MenuStrip> 或 <xref:System.Windows.Forms.ContextMenuStrip> 上的可選取選項。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|代表捷徑功能表。|  
|<xref:System.Windows.Forms.ToolStripDropDown>|代表允許使用者從清單選取單一項目的控制項，此份清單是使用者按一下 <xref:System.Windows.Forms.ToolStripDropDownButton> 或較高層級功能表項目時所顯示的清單。|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|提供衍生自 <xref:System.Windows.Forms.ToolStripItem> 的控制項的基本功能，當按一下這個控制項時會顯示下拉式項目。|  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 <xref:System.Windows.Forms.ToolStripItem>   
 <xref:System.Windows.Forms.ToolStripDropDown>