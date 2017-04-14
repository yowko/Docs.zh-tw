---
title: "如何：使用設計工具設定 Windows Form 面板的背景 | Microsoft Docs"
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
  - "背景色彩, Windows Form Panel 控制項"
  - "背景影像, Windows Form Panel 控制項"
  - "色彩, Windows Form Panel 控制項"
  - "Panel 控制項 [Windows Form], 背景"
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用設計工具設定 Windows Form 面板的背景
Windows Form <xref:System.Windows.Forms.Panel> 控制項可顯示背景色彩和背景影像。  <xref:System.Windows.Forms.Control.BackColor%2A> 屬性設定面板所收納的控制項之背景色彩，例如標籤和選項按鈕。  如果 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性未設定，則選取的 <xref:System.Windows.Forms.Control.BackColor%2A> 會填滿整個面板。  如果設定了 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性，則影像會顯示在面板所收納的控制項之後。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.Panel> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在 Windows Form 設計工具中設定背景  
  
1.  選取 <xref:System.Windows.Forms.Panel> 控制項。  
  
2.  在 \[**屬性**\] 視窗中，按一下 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性旁邊的箭號按鈕，顯示一個含三個索引標籤的視窗。  
  
3.  選取 \[**自訂**\] 索引標籤，以顯示色板。  
  
4.  選取 \[**Web**\] 或 \[**系統**\] 索引標籤，以顯示預先定義的色彩名稱清單，然後選取一種色彩。  
  
5.  在 \[**屬性**\] 視窗中，按一下 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性旁邊的箭頭按鈕。  
  
6.  在 \[**開啟**\] 對話方塊中，選取您要顯示的檔案。  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.BackColor%2A>   
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>   
 [Panel 控制項](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)   
 [Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)   
 [如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)