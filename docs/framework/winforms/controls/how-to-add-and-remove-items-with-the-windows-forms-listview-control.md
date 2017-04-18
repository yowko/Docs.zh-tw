---
title: "如何：使用 Windows Form ListView 控制項加入和移除項目 | Microsoft Docs"
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
  - "清單檢視, 加入清單項目"
  - "ListView 控制項 [Windows Form], 加入清單項目"
  - "ListView 控制項 [Windows Form], 填入"
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用 Windows Form ListView 控制項加入和移除項目
將項目加入至 Windows Form <xref:System.Windows.Forms.ListView> 控制項的程序，主要包括指定項目和指派項目屬性。  加入或移除清單項目 \(List Item\) 可於任何時候執行。  
  
### 若要以程式設計方式加入項目  
  
1.  使用 <xref:System.Windows.Forms.ListView.Items%2A> 屬性的 <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> 方法。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### 若要以程式設計的方式移除項目  
  
1.  使用 <xref:System.Windows.Forms.ListView.Items%2A> 屬性的 <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> 或 <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> 方法。  <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> 方法會移除單一項目；<xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> 方法則會移除清單中的所有項目。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## 請參閱  
 <xref:System.Windows.Forms.ListView>   
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)