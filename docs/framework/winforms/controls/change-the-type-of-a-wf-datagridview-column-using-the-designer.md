---
title: "如何：使用設計工具變更 Windows Form DataGridView 資料行的類型 | Microsoft Docs"
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
  - "資料行 [Windows Form], 類型"
  - "資料 [Windows Form], 顯示"
  - "DataGridView 控制項 [Windows Form], 變更資料行類型"
  - "Windows Form, 資料行"
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用設計工具變更 Windows Form DataGridView 資料行的類型
您有時候可能會想變更已經加入至 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項的資料行型別。  例如，您可能想修改在繫結控制項至資料來源時，所自動產生的某些資料行的型別。  當您所顯示的資料表在其資料行中，包含相關資料表內資料列的外部索引鍵時，這會非常有用。  在這種情況下，您可能想以顯示相關資料表中更具意義之值的下拉式方塊，取代顯示這些外部索引鍵的文字方塊資料行。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.DataGridView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要使用設計工具變更資料行型別  
  
1.  按一下 <xref:System.Windows.Forms.DataGridView> 控制項右上角的智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\)，然後選取 \[**編輯資料行**\]。  
  
2.  從 \[**已選取的資料行**\] 清單中選取資料行。  
  
3.  在 \[**資料行屬性**\] 方格中，將 `ColumnType` 屬性設定為新的資料行型別。  
  
    > [!NOTE]
    >  `ColumnType` 是僅限設計階段的屬性，表示代表資料行型別的類別。  這不是定義在資料行類別中的實質屬性。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn>   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)