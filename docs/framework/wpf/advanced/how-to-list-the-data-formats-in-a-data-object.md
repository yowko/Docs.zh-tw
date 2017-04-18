---
title: "如何：列出資料物件中的資料格式 | Microsoft Docs"
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
  - "資料格式 [WPF], 列出"
  - "DataFormats 類別 [WPF]"
  - "拖放功能 [WPF], 列出資料格式"
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：列出資料物件中的資料格式
下列範例顯示如何使用 <xref:System.Windows.DataObject.GetFormats%2A> 方法多載，取得代表資料物件中每個可用資料格式之字串的陣列。  
  
## 範例  
  
### 描述  
 下列範例程式碼會使用 <xref:System.Windows.DataObject.GetFormats%2A> 多載取得字串陣列，這個字串陣列表示資料物件中所有可用的資料格式 \(包括原生格式和可自動轉換的格式\)。  
  
### 程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## 範例  
  
### 描述  
 下列範例程式碼使用 <xref:System.Windows.DataObject.GetFormats%2A> 多載，取得僅代表資料物件中可用資料格式之字串的陣列 \(可自動轉換的資料格式會篩選掉\)。  
  
### 程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## 請參閱  
 <xref:System.Windows.IDataObject>   
 [拖放概觀](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)