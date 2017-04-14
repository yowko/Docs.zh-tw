---
title: "如何：將多個資料格式儲存在資料物件中 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DataFormats 類別 [WPF], 儲存多個格式"
  - "DataObject 類別 [WPF], 儲存多個格式"
  - "拖放功能 [WPF], 儲存多個格式"
ms.assetid: 941ace29-29c4-4c26-b75b-ea7d06aa0d69
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：將多個資料格式儲存在資料物件中
下列範例顯示如何使用 <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> 方法，以多種格式將資料加入至資料物件。  
  
## 範例  
  
### 描述  
  
### 程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
## 請參閱  
 <xref:System.Windows.IDataObject>   
 [拖放概觀](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)