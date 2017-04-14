---
title: "合併 Windows Form MenuStrip 控制項中的功能表項目 | Microsoft Docs"
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
  - "MenuStrip, 合併"
  - "合併, 一般概念"
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 合併 Windows Form MenuStrip 控制項中的功能表項目
如果您有多重文件介面 \(MDI\) 應用程式，您可以從子表單將功能表項目或整個功能表合併至父表單的功能表。  
  
 這個主題將說明在 MDI 應用程式中合併功能表項目的相關基本概念。  
  
## 一般概念  
 合併程序會牽涉目標控制項和來源控制項：  
  
-   目標控制項是在您要在其中合併功能表項目之主表單或 MDI 父表單上的 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
-   來源控制項是在包含要合併至目標功能表的功能表項目之 MDI 子表單上的 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> 屬性可識別功能表項目，而您可以使用目前 MDI 父表單之 MDI 子表單的標題填入其下拉式清單。  例如，您通常會列出目前在 \[**視窗**\] 功能表上開啟的 MDI 子表單。  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> 屬性可識別哪些功能表項目來自 MDI 子表單上的 <xref:System.Windows.Forms.MenuStrip>。  
  
 您可以手動或自動合併功能表項目。  針對這兩種方法，功能表項目都會以相同的方式進行合併，但啟動合併的方式不同，請參閱本主題稍後之＜手動合併＞和＜自動合併＞章節中的討論。  在手動合併和自動合併中，每一個合併動作都會影響下一個合併動作。  
  
 和使用 <xref:System.Windows.Forms.MainMenu> 的情況一樣，<xref:System.Windows.Forms.MenuStrip> 合併會將功能表項目從一個 <xref:System.Windows.Forms.ToolStrip> 移至另一個，而非進行複製。  
  
## MergeAction 值  
 您可以使用 <xref:System.Windows.Forms.MergeAction> 屬性來設定在來源 <xref:System.Windows.Forms.MenuStrip> 中之功能表項目上的合併動作。  
  
 下表說明可用之合併動作的意義和一般的使用方式。  
  
|MergeAction 值|描述|一般用法|  
|-------------------|--------|----------|  
|<xref:System.Windows.Forms.MergeAction>|\(預設值\) 將來源項目加入至目標項目集合的結尾處。|當啟動某部分程式時，將功能表項目加入至功能表的結尾處。|  
|<xref:System.Windows.Forms.MergeAction>|根據在來源項目上設定之 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 屬性所指定的位置，將來源項目加入至目標項目的集合中。|當啟動某部分程式時，將功能表項目加入至功能表的中間或開頭。<br /><br /> 如果兩個功能表項目的 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 值相同，則會以相反的順序加入。  請適當設定 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>，以保留原始的順序。|  
|<xref:System.Windows.Forms.MergeAction>|尋找相符的文字，或者在找不到相符的文字時使用 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 值，然後以來源功能表項目取代相符的目標功能表項目。|使用名稱相同，但用途不同的來源功能表項目取代目標功能表項目。|  
|<xref:System.Windows.Forms.MergeAction>|尋找相符的文字，或者在找不到相符的文字時使用 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 值，然後將來源的所有下拉式項目加入至目標。|建置功能表結構，將功能表項目插入或加入至子功能表，或從子功能表中移除功能表項目。  例如，您可以將功能表項目從 MDI 子表單加入至主 <xref:System.Windows.Forms.MenuStrip> 的 \[**另存新檔**\] 功能表。<br /><br /> <xref:System.Windows.Forms.MergeAction> 可以讓您透過功能表結構進行巡覽，而不需要執行任何動作。  它提供了評估後續項目的方法。|  
|<xref:System.Windows.Forms.MergeAction>|尋找相符的文字，或者在找不到相符的文字時使用 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 值，然後將該項目從目標中移除。|將功能表項目從目標 <xref:System.Windows.Forms.MenuStrip> 中移除。|  
  
## 手動合併  
 只有 <xref:System.Windows.Forms.MenuStrip> 控制項會加入自動合併。  若要組合其他控制項 \(例如：<xref:System.Windows.Forms.ToolStrip> 和 <xref:System.Windows.Forms.StatusStrip> 控制項\) 的項目，您必須視需要在程式碼中呼叫 <xref:System.Windows.Forms.ToolStripManager.Merge%2A> 和 <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> 方法，手動合併這些項目。  
  
## 自動合併  
 您可以透過啟動來源表單來使用 MDI 應用程式的自動合併功能。  若要在 MDI 應用程式中使用 <xref:System.Windows.Forms.MenuStrip>，請將 <xref:System.Windows.Forms.Form.MainMenuStrip%2A> 屬性設定為目標 <xref:System.Windows.Forms.MenuStrip>，讓在來源 <xref:System.Windows.Forms.MenuStrip> 上執行的合併動作可以反映在目標 <xref:System.Windows.Forms.MenuStrip> 中。  
  
 您可以透過啟動 MDI 來源上的 <xref:System.Windows.Forms.MenuStrip> 來觸發自動合併。  在啟動之後，來源 <xref:System.Windows.Forms.MenuStrip> 便會立即合併至 MDI 目標。  當新的表單變成使用中時，便會在上一個表單中還原合併，然後在新的表單上觸發合併。  您可以視需要設定每一個 <xref:System.Windows.Forms.ToolStripItem> 上的 <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> 屬性，以及設定每一個 <xref:System.Windows.Forms.MenuStrip> 上的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性，以控制這個行為。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStripManager>   
 <xref:System.Windows.Forms.MenuStrip>   
 [MenuStrip 控制項](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)   
 [如何：使用 MenuStrip 建立 MDI 視窗清單](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)   
 [如何：設定 MDI 應用程式的自動功能表合併功能](../../../../docs/framework/winforms/controls/how-to-set-up-automatic-menu-merging-for-mdi-applications.md)