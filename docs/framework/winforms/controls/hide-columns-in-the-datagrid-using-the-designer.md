---
title: "如何：使用設計工具隱藏 Windows Form DataGridView 控制項中的資料行 | Microsoft Docs"
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
  - "資料行 [Windows Form], 隱藏"
  - "資料 [Windows Form], 顯示"
  - "DataGridView 控制項 [Windows Form], 隱藏資料行"
  - "Windows Form, 資料行"
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用設計工具隱藏 Windows Form DataGridView 控制項中的資料行
有時候您會想要只顯示 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項中的一些可用資料行。  例如，您可能想要對具有管理認證的使用者顯示員工薪資資料行，但對其他使用者隱藏此項資訊；  或者，也可能想將控制項繫結至包含許多資料行的資料來源，但只想要顯示其中某些資料行。  在這種情況下，通常您會將不想顯示的資料行移除，而非加以隱藏。  如需詳細資訊，請參閱 [如何：使用設計工具在 Windows Form DataGridView 控制項中加入和移除資料行](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.DataGridView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要使用設計工具隱藏資料行  
  
1.  按一下 <xref:System.Windows.Forms.DataGridView> 控制項右上角的智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\)，然後選取 \[**編輯資料行**\]。  
  
2.  從 \[**已選取的資料行**\] 清單中選取資料行。  
  
3.  在 \[**資料行屬性**\] 方格中，將 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> 屬性設定為 `false`。  
  
    > [!NOTE]
    >  您也可以清除 \[**加入資料行**\] 對話方塊中的 \[**可見的**\] 核取方塊，藉此在加入資料行時進行隱藏。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=fullName>   
 [如何：使用設計工具在 Windows Form DataGridView 控制項中加入和移除資料行](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)