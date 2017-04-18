---
title: "如何：設定 MDI 應用程式的自動功能表合併功能 | Microsoft Docs"
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
  - "合併, 自動功能表"
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：設定 MDI 應用程式的自動功能表合併功能
下列程序將提供使用 <xref:System.Windows.Forms.MenuStrip> 在多重文件介面 \(MDI\) 應用程式中設定自動合併的基本步驟。  
  
### 若要設定自動功能表合併功能  
  
1.  透過將 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`，以建立 MDI 父表單。  
  
2.  將 <xref:System.Windows.Forms.MenuStrip> 加入至 MDI 父視窗，然後將其 <xref:System.Windows.Forms.Form.MainMenuStrip%2A> 屬性設定為該 <xref:System.Windows.Forms.MenuStrip>。  
  
3.  建立 MDI 子表單，並將其 <xref:System.Windows.Forms.Form.MdiParent%2A> 屬性設定為父表單的名稱。  
  
4.  將 <xref:System.Windows.Forms.MenuStrip> 加入至 MDI 子表單中。  
  
5.  在子表單上，將 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStripItem.Visible%2A> 屬性設定為 `false`。  
  
6.  將功能表項目加入至子表單啟動時，要合併至父表單之 <xref:System.Windows.Forms.MenuStrip> 的子表單 <xref:System.Windows.Forms.MenuStrip>。  
  
7.  使用子表單之 <xref:System.Windows.Forms.MenuStrip> 中功能表項目上的 <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> 屬性，控制將這些功能表項目合併到父表單的方式。  
  
## 請參閱  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)