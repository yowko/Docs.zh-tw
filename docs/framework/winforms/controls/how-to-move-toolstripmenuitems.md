---
title: "如何：移動 ToolStripMenuItems | Microsoft Docs"
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
  - "功能表項目, 剪下和貼上"
  - "功能表項目, 拖放"
  - "功能表項目, 移動"
  - "功能表, 排列項目"
  - "MenuStrip 控制項 [Windows Form], 排列項目"
  - "ToolStripMenuItems, 剪下和貼上"
  - "ToolStripMenuItems, 拖放"
  - "ToolStripMenuItems, 移動"
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：移動 ToolStripMenuItems
在設計階段時，將整個最上層功能表及其功能表項目移動至 <xref:System.Windows.Forms.MenuStrip> 上的不同位置。  您也能移動最上層功能表之間的個別功能表項目，或變更功能表內功能表項目的位置。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要將最上層功能表及其功能表項目移至另一個最上層位置  
  
1.  在想移動的功能表上按一下，並按住滑鼠左鍵。  
  
2.  將插入點拖曳至預期的新位置之前的最上層功能表，然後釋放滑鼠左鍵。  
  
     選取的功能表會移至插入點的右邊。  
  
### 若要將最上層功能表及其功能表項目移至下拉式位置  
  
1.  以滑鼠左鍵按一下您想要移動的功能表，然後按下 CTRL\+X，或以滑鼠右鍵按一下功能表，然後從捷徑功能表選取 \[**剪下**\]。  
  
2.  在目的端最上層功能表，以滑鼠左鍵按一下在預期的新位置上方的功能表項目，然後按下 CTRL\+V，或以滑鼠右鍵按一下在預期的新位置上方的功能表項目，然後從捷徑功能表選取 \[**貼上**\]。  
  
     您所剪下的功能表會插入在選取的功能表項目之後。  
  
### 若要使用項目集合編輯器移動功能表內的功能表項目  
  
1.  以滑鼠右鍵按一下包含想要移動之功能表項目的功能表。  
  
2.  從捷徑功能表上選取 \[**編輯 DropDownItems**\]。  
  
3.  在 \[**項目集合編輯器**\] 中，以滑鼠左鍵按一下想移動的功能表項目。  
  
4.  按一下向上或向下鍵以移動功能表內的功能表項目。  
  
5.  按一下 \[**確定**\]。  
  
### 若要使用鍵盤移動功能表內的功能表項目  
  
1.  按下並按住 ALT 鍵。  
  
2.  在您想移動的功能表上按一下並按住滑鼠左鍵。  
  
3.  將功能表項目拖曳至新位置，然後釋放滑鼠左鍵。  
  
### 若要將功能表項目移動至另一個功能表  
  
1.  以滑鼠左鍵按一下您想移動的功能表項目並按 CTRL\+X，或以滑鼠右鍵按一下功能表項目，然後從捷徑功能表選取 \[**剪下**\]。  
  
2.  以滑鼠左鍵按一下會包含您剪下的功能表項目的功能表。  
  
3.  以滑鼠左鍵按一下在預期的新位置之前的功能表項目，然後按下 CTRL\+V，或以滑鼠右鍵按一下在預期的新位置之前的功能表項目，然後從捷徑功能表選取 \[**貼上**\]。  
  
     您所剪下的功能表項目會插入在選取的功能表項目之後。  
  
## 請參閱  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)