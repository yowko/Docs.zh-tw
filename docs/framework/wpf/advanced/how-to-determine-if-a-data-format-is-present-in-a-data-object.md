---
title: "如何：判斷資料格式是否出現在資料物件中 | Microsoft Docs"
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
  - "資料格式 [WPF], 判斷是否存在"
  - "DataFormats 類別 [WPF]"
  - "拖放功能 [WPF], 資料格式存在"
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：判斷資料格式是否出現在資料物件中
下列範例顯示如何使用各種 <xref:System.Windows.DataObject.GetDataPresent%2A> 方法多載，查詢資料物件中是否存在特定資料格式。  
  
## 範例  
  
### 描述  
 下列範例程式碼使用 <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> 多載，藉由描述項字串來查詢是否存在特定資料格式。  
  
### 程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## 範例  
  
### 描述  
 下列範例程式碼使用 <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> 多載，藉由型別來查詢是否存在特定資料格式。  
  
### 程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## 範例  
  
### 描述  
 下列範例程式碼使用 <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> 多載，藉由描述項字串來查詢資料，並指定自動轉換資料格式的處理方式。  
  
### 程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## 請參閱  
 <xref:System.Windows.IDataObject>