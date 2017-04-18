---
title: "如何：擷取特定資料格式的資料 | Microsoft Docs"
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
  - "DataFormats 類別 [WPF], 擷取資料"
  - "DataObject 類別 [WPF], 擷取資料"
  - "拖放功能 [WPF], 擷取資料"
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：擷取特定資料格式的資料
下列範例示範如何從資料物件擷取指定之格式的資料。  
  
## 範例  
  
### 描述  
 下列範例程式碼會先使用 <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> 多載檢查指定的資料格式 \(原生格式或自動轉換的格式\) 是否可用；如果指定的資料格式可用，這個範例會使用 <xref:System.Windows.DataObject.GetData%28System.String%29> 方法擷取資料。  
  
### 程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## 範例  
  
### 描述  
 下列範例程式碼會先使用 <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> 多載檢查指定的原生資料格式是否可用 \(篩選自動轉換的資料格式\)；如果指定的資料格式可用，這個範例會使用  <xref:System.Windows.DataObject.GetData%28System.String%29> 方法擷取資料。  
  
### 程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## 請參閱  
 <xref:System.Windows.IDataObject>   
 [拖放概觀](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)