---
title: "如何：使用設計工具搭配 Windows Form ListView 控制項加入和移除項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ListView 控制項 [Windows Form], 加入清單項目"
  - "ListView 控制項 [Windows Form], 填入"
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：使用設計工具搭配 Windows Form ListView 控制項加入和移除項目
將項目加入至 Windows Form <xref:System.Windows.Forms.ListView> 控制項的程序，主要包括指定項目和指派項目屬性。  加入或移除清單項目 \(List Item\) 可於任何時候執行。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.ListView> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要使用設計工具加入或移除項目  
  
1.  選取 <xref:System.Windows.Forms.ListView> 控制項。  
  
2.  在 \[**屬性**\] 視窗中，按一下 <xref:System.Windows.Forms.ListView.Items%2A> 屬性旁邊的**省略符號** \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕。  
  
     \[**ListViewItem 集合編輯器**\] 隨即出現。  
  
3.  若要加入項目，請按一下 \[**加入**\] 按鈕。  然後您可以設定新項目的屬性，例如 <xref:System.Windows.Forms.ListView.Text%2A> 和 <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> 屬性。  
  
4.  若要移除項目，請選取項目然後按一下 \[**移除**\] 按鈕。  
  
## 請參閱  
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [如何：將資料行加入至 Windows Form ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)   
 [如何：使用 Windows Form ListView 控制項以資料行顯示子項目](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)   
 [如何：顯示 Windows Form ListView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)   
 [如何：將自訂資訊加入 TreeView 或 ListView 控制項 \(Windows Form\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)   
 [如何：在 Windows Form ListView 控制項中群組項目](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)