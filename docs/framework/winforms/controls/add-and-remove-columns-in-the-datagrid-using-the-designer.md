---
title: "如何：使用設計工具在 Windows Form DataGridView 控制項中加入和移除資料行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.DataGridViewAddColumnDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DataGridView 控制項 [Windows Form], 加入資料行"
  - "DataGridView 控制項 [Windows Form], 移除資料行"
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：使用設計工具在 Windows Form DataGridView 控制項中加入和移除資料行
Windows Form <xref:System.Windows.Forms.DataGridView> 控制項必須包含資料行，才能夠顯示資料。  如果您計劃以手動方式填入控制項，就必須自行加入資料行。  此外，您也可以繫結控制項至資料來源，該資料來源會自動產生並填入資料行。  如果資料來源包含的資料行比您想顯示的還多，便可以移除不必要的資料行。  
  
 下列程序需要 \[**Windows 應用程式**\] 專案，且專案具有包含 <xref:System.Windows.Forms.DataGridView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要使用設計工具加入資料行  
  
1.  按一下 <xref:System.Windows.Forms.DataGridView> 控制項右上角的智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\)，然後選取 \[**加入資料行**\]。  
  
2.  在 \[**加入資料行**\] 對話方塊中選擇 \[**已繫結資料的資料行**\] 選項，然後從資料來源選取資料行，或選擇 \[**未繫結的資料行**\] 選項，並使用提供的欄位定義資料行。  
  
3.  按一下 \[**加入**\] 按鈕以加入資料行，如果現有資料行尚未填滿控制項顯示區域，就會讓資料行出現在設計工具中。  
  
    > [!NOTE]
    >  您可以在 \[**編輯資料行**\] 對話方塊中修改資料行屬性，此對話方塊可從控制項的智慧標籤存取。  
  
### 若要使用設計工具移除資料行  
  
1.  從控制項的智慧標籤中選擇 \[**編輯資料行**\]。  
  
2.  從 \[**已選取的資料行**\] 清單中選取資料行。  
  
3.  按一下 \[**移除**\] 按鈕以刪除資料行，讓資料行從設計工具中消失。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)