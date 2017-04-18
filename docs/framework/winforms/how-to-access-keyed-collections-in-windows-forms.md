---
title: "如何：在 Windows Form 中存取索引集合 | Microsoft Docs"
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
  - "集合, 使用索引鍵存取"
  - "索引集合 [Windows Form]"
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：在 Windows Form 中存取索引集合
-   您可依據索引鍵來存取個別的集合項目。  這項功能已經加入到 Windows Form 應用程式所通常使用的許多集合類別 \(Class\)。  下列清單顯示一些具有可存取之索引集合的集合類別：  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 在集合中與某個項目關聯的索引鍵，通常都會是該項目的名稱。  下列程序向您示範如何使用集合類別來執行常見工作。  
  
### 找到控制項集合中的巢狀控制項並將焦點放在其中  
  
-   使用 <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> 和 <xref:System.Windows.Forms.Control.Focus%2A> 方法來指定要找到之控制項的名稱，並將焦點放在其中。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### 存取影像集合中的影像  
  
-   使用 <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> 屬性來指定您所要存取影像的名稱。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### 將索引標籤頁設定為選取的索引標籤  
  
-   搭配使用 <xref:System.Windows.Forms.TabControl.SelectedTab%2A> 屬性與 <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> 屬性，指定要將其設定為選取之索引標籤的索引標籤頁名稱。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## 請參閱  
 [Windows Form 使用者入門](../../../docs/framework/winforms/getting-started-with-windows-forms.md)   
 [如何：使用 Windows Form ImageList 元件加入或移除影像](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)