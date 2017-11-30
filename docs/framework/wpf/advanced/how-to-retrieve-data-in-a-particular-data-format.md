---
title: "如何：擷取特定資料格式的資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e6513fd6d8d443b76059626c0e40991e35830c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a>如何：擷取特定資料格式的資料
下列範例會示範如何從指定的格式中的資料物件擷取資料。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>多載來檢查指定的資料設定格式 （原生或自動轉換）; 如果指定的格式使用時，此範例會擷取資料使用<xref:System.Windows.DataObject.GetData%28System.String%29>方法。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>多載，先檢查是否指定的資料格式是使用原生 （自動轉換的資料格式已篩選）; 如果指定的格式使用時，此範例會擷取資料使用<xref:System.Windows.DataObject.GetData%28System.String%29>方法。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.IDataObject>  
 [拖放概觀](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
