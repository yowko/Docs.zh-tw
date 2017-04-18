---
title: "如何：使用設計工具變更 Windows Form DataGridView 控制項中資料行的順序 | Microsoft Docs"
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
  - "資料行 [Windows Form], 順序"
  - "資料 [Windows Form], 顯示"
  - "DataGridView 控制項 [Windows Form], 資料行順序"
  - "Windows Form, 資料行"
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用設計工具變更 Windows Form DataGridView 控制項中資料行的順序
當您繫結 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項至資料來源時，資料來源會指出自動產生之資料行的顯示順序。  如果這個順序不是您所喜好的，您可使用設計工具變更資料行的順序。  您也可能想要加入未繫結的資料行至控制項，並變更這些資料行的顯示順序。  如需如何以程式設計方式變更資料行順序的詳細資訊，請參閱 [如何：變更 Windows Form DataGridView 控制項資料行的順序](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.DataGridView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### 若要使用設計工具變更資料行順序  
  
1.  按一下 <xref:System.Windows.Forms.DataGridView> 控制項右上角的智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\)，然後選取 \[**編輯資料行**\]。  
  
2.  從 \[**已選取的資料行**\] 清單中選取資料行。  
  
3.  按一下 \[**選取的資料行**\] 清單右邊的向上或向下鍵，直到選取的資料行在您想要的位置為止。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 [如何：使用設計工具在 Windows Form DataGridView 控制項中加入和移除資料行](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)