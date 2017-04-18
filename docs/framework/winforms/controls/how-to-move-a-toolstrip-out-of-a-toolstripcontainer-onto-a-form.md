---
title: "如何：將 ToolStrip 移出 ToolStripContainer 並移至表單上 | Microsoft Docs"
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
  - "ToolStrip 控制項 [Windows Forms], 表單的父代"
  - "Windows Form, ToolStrip 控制項的父代"
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：將 ToolStrip 移出 ToolStripContainer 並移至表單上
使用下列程序將 <xref:System.Windows.Forms.ToolStrip> 從 <xref:System.Windows.Forms.ToolStripContainer> 移出至表單上。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要將 ToolStrip 移出 ToolStripContainer 並移至表單上  
  
1.  選取 <xref:System.Windows.Forms.ToolStrip>。  
  
2.  按下 CTRL\+X 以剪下 <xref:System.Windows.Forms.ToolStrip>，或以滑鼠右鍵按一下 <xref:System.Windows.Forms.ToolStrip> 並從內容功能表中選擇 \[**剪下**\]。  
  
3.  選取表單。  
  
4.  按下 CTRL\+V 以貼上 <xref:System.Windows.Forms.ToolStrip>，或從 \[**編輯**\] 功能表選擇 \[**貼上**\]。  
  
5.  將 <xref:System.Windows.Forms.ToolStrip> 的 <xref:System.Windows.Forms.ToolStrip.Dock%2A> 屬性設定為 \[**Top**\]。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripContainer>   
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)