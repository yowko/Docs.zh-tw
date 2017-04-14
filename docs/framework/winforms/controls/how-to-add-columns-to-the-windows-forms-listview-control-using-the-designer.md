---
title: "如何：使用設計工具在 Windows Form ListView 控制項中加入資料行 | Microsoft Docs"
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
  - "資料行 [Windows Form], 加入到 ListView 控制項"
  - "ListView 控制項 [Windows Form], 加入資料行行首"
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：使用設計工具在 Windows Form ListView 控制項中加入資料行
Windows Form <xref:System.Windows.Forms.ListView> 控制項在 \[**詳細資料**\] 檢視中，每一個清單項目可以使用多個資料行來顯示。  您可以使用資料行來顯示關於各個清單項目的數種資訊。  例如，檔案清單可以顯示檔案名稱、檔案類型、大小和檔案上次修改日期。  如需在資料行建立後填入資料的詳細資訊，請參閱 [如何：使用 Windows Form ListView 控制項以資料行顯示子項目](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.ListView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 在設計工具中加入資料行  
  
1.  請在 \[**屬性**\] 視窗中，將控制項的 <xref:System.Windows.Forms.ListView.View%2A> 屬性設定為 <xref:System.Windows.Forms.View>。  
  
2.  在 \[**屬性**\] 視窗中，按一下 <xref:System.Windows.Forms.ListView.Columns%2A> 屬性旁邊的**省略符號** \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕。  
  
     \[**ColumnHeader 集合編輯器**\] 隨即出現。  
  
3.  使用 \[**加入**\] 按鈕來加入新的資料行。  接著，您可以選取資料行行首並設定其文字 \(資料行的標題\)、文字對齊以及寬度。  
  
## 請參閱  
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [如何：使用 Windows Form ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [如何：使用 Windows Form ListView 控制項以資料行顯示子項目](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)   
 [如何：顯示 Windows Form ListView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)   
 [如何：將自訂資訊加入 TreeView 或 ListView 控制項 \(Windows Form\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)