---
title: "如何：使用設計工具將 Windows Form DataGridView 控制項中的資料行設為唯讀 | Microsoft Docs"
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
  - "資料行 [Windows Form], 唯讀"
  - "資料 [Windows Form], 顯示"
  - "DataGridView 控制項 [Windows Form], 唯讀資料行"
  - "Windows Form, 資料行"
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：使用設計工具將 Windows Form DataGridView 控制項中的資料行設為唯讀
根據預設，使用者可以修改顯示於 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項的文字和數值資料。  如果您想顯示不可用來修改的資料，就必須讓包含資料的資料行成為唯讀。  如需如何讓控制項完全唯讀的詳細資訊，請參閱 [如何：使用設計工具防止在 Windows Form DataGridView 控制項中新增和刪除資料列](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.DataGridView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要使用設計工具讓資料行成為唯讀  
  
1.  按一下 <xref:System.Windows.Forms.DataGridView> 控制項右上角的智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\)，然後選取 \[**編輯資料行**\]。  
  
2.  從 \[**已選取的資料行**\] 清單中選取資料行。  
  
3.  在 \[**資料行屬性**\] 方格中，將 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> 屬性設定為 `true`。  
  
    > [!NOTE]
    >  您也可以選取 \[**加入資料行**\] 對話方塊中的 \[**唯讀**\] 核取方塊，藉此在加入資料行時，讓它成為唯讀。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=fullName>   
 [如何：使用設計工具在 Windows Form DataGridView 控制項中加入和移除資料行](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [如何：使用設計工具防止在 Windows Form DataGridView 控制項中新增和刪除資料列](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)