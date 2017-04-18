---
title: "如何：使用設計工具隱藏 ToolStripMenuItems | Microsoft Docs"
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
  - "功能表項目, 隱藏"
  - "MenuStrip 控制項 [Windows Form], 在設計工具中隱藏功能表項目"
  - "ToolStripMenuItems, 在設計工具中隱藏功能表項目"
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用設計工具隱藏 ToolStripMenuItems
隱藏功能表項目是控制應用程式的使用者介面 \(UI\) 和限制使用者命令的方式。  通常，當功能表上的所有功能表項目都無法使用時，您會想要隱藏整個功能表。  這樣可以減少使用者的操作困擾。  此外，您可能會想要隱藏並停用功能表或功能表項目，因為單獨隱藏並無法防止使用者經由使用快速鍵存取功能表命令。  如需停用功能表項目的詳細資訊，請參閱 [如何：使用設計工具停用 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要隱藏最上層功能表及其子功能表項目  
  
1.  選取最上層的功能表項目，並將該項目的 <xref:System.Windows.Forms.ToolStripItem.Visible%2A> 或 <xref:System.Windows.Forms.ToolStripItem.Available%2A> 屬性設定為 `false`。  
  
     當您隱藏最上層功能表項目時，也會同時隱藏該功能表中的所有功能表項目。  如果您在將 <xref:System.Windows.Forms.ToolStripItem.Visible%2A> 設定為 `false` 之後按一下 <xref:System.Windows.Forms.MenuStrip> 上的其他地方，整個最上層功能表項目和子功能表項目將會從表單上消失，以此展示出您的動作在執行階段的作用。  若要在設計階段顯示已隱藏的最上層功能表項目，請按一下 \[**元件匣**\]、\[**文件大綱**\] 或屬性方格上方的 <xref:System.Windows.Forms.MenuStrip>。  
  
> [!NOTE]
>  除了在多重文件介面 \(MDI\) 中合併子功能表以外，您很少會需要隱藏整個功能表。  
  
### 若要隱藏子功能表項目  
  
1.  選取子功能表項目，並將其 <xref:System.Windows.Forms.ToolStripItem.Visible%2A> 屬性設定為 `false`。  
  
     當您隱藏子功能表項目時，該項目在設計階段會在表單上保持可見狀態，因此您可輕易選取它以執行進一步工作。  在執行階段時則會將它隱藏起來。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>   
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>   
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>   
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)   
 [如何：使用設計工具停用 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)