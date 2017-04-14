---
title: "如何：選取 Windows Form ListView 控制項中的項目 | Microsoft Docs"
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
  - "清單檢視, 選取項目"
  - "清單, 選取項目"
  - "ListView 控制項 [Windows Form], 選取項目"
  - "選取範圍, 清單檢視"
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：選取 Windows Form ListView 控制項中的項目
此範例示範如何以程式設計方式選取 Windows Forms <xref:System.Windows.Forms.ListView> 控制項中的項目。  以程式設計的方式選取項目並不會自動將焦點變更為 <xref:System.Windows.Forms.ListView> 控制項。  因此，通常您也會想要在選取項目時，將此設定設為焦點。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `listView1` 的 <xref:System.Windows.Forms.ListView> 控制項，而且至少含有一個項目。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 命名空間的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=fullName>