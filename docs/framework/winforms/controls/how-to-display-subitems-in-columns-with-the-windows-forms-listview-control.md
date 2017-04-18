---
title: "如何：使用 Windows Form ListView 控制項以資料行顯示子項目 | Microsoft Docs"
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
  - "詳細檢視。"
  - "清單項目"
  - "ListView 控制項 [Windows Form], 加入 ListSubItems"
  - "子項目"
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：使用 Windows Form ListView 控制項以資料行顯示子項目
Windows Form <xref:System.Windows.Forms.ListView> 控制項在 Details 檢視中可以顯示各項目的其他文字或子項目。  第一資料行顯示項目文字，例如員工編號。  第二、第三和後續資料行顯示第一、第二和後續相關子項目。  
  
### 若要將子項目加入至清單項目  
  
1.  加入任何需要的資料行。  由於第一個資料行會顯示項目的 <xref:System.Windows.Forms.ListView.Text%2A> 屬性，因此您需要的資料行數會比子項目數多一個。  如需加入資料行的詳細資訊，請參閱 [如何：將資料行加入至 Windows Form ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)。  
  
2.  呼叫由項目之 <xref:System.Windows.Forms.ListViewItem.SubItems%2A> 屬性所傳回的集合之 <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> 方法。  下列程式碼範例會為清單項目設定員工姓名和部門。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## 請參閱  
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [如何：使用 Windows Form ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [如何：將資料行加入至 Windows Form ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)   
 [如何：顯示 Windows Form ListView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)   
 [如何：將自訂資訊加入 TreeView 或 ListView 控制項 \(Windows Form\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)