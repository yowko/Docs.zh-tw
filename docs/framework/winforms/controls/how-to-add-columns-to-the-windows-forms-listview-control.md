---
title: "如何：將資料行加入至 Windows Form ListView 控制項 | Microsoft Docs"
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
  - "清單檢視, 加入資料行"
  - "ListView 控制項 [Windows Form], 加入資料行行首"
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：將資料行加入至 Windows Form ListView 控制項
在 \[詳細資料\] 檢視中，<xref:System.Windows.Forms.ListView> 控制項可以為每個清單項目顯示多個資料行。  您可以使用資料行，為使用者顯示關於各個清單項目的數種類型資訊。  例如，檔案清單可以顯示檔案名稱、檔案類型、大小和檔案上次修改日期。  如需在建立資料行後填入資料的詳細資訊，請參閱 [如何：使用 Windows Form ListView 控制項以資料行顯示子項目](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)。  
  
### 如果要以程式設計的方式加入資料行  
  
1.  將控制項的 <xref:System.Windows.Forms.ListView.View%2A> 屬性設定為 <xref:System.Windows.Forms.View>。  
  
2.  使用清單檢視的 <xref:System.Windows.Forms.ListView.Columns%2A> 屬性的 <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> 方法。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## 請參閱  
 <xref:System.Windows.Forms.ListView>   
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)