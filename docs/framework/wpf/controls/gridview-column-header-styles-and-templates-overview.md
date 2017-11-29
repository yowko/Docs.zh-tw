---
title: "GridView 資料行行首樣式和範本概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ad0f7cacc8256e060bb12611bd1818b694e1e6dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gridview-column-header-styles-and-templates-overview"></a>GridView 資料行行首樣式和範本概觀
這個概觀討論的屬性，用來自訂中的資料行標頭的優先順序<xref:System.Windows.Controls.GridView>檢視模式<xref:System.Windows.Controls.ListView>控制項。  
  
## <a name="customizing-a-column-header-in-a-gridview"></a>自訂在 GridView 的資料行標頭  
 定義內容、 配置和樣式中的資料行標頭的屬性，<xref:System.Windows.Controls.GridView>找到許多相關的類別上。 其中某些屬性具有功能類似或相同。  
  
 下表中的資料列顯示一組執行相同的函式的內容。 您可以使用這些屬性來自訂資料行標頭中的<xref:System.Windows.Controls.GridView>。 相關屬性的優先順序是由右至左右欄中的屬性具有最高優先順序的位置。 例如，如果<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>上設定<xref:System.Windows.Controls.GridViewColumnHeader>物件和<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>就會在相關聯集<xref:System.Windows.Controls.GridViewColumn>、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>優先。 在此案例中，<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>沒有任何作用。  
  
 **在 GridView 的資料行標頭的相關的屬性**  
  
|||||  
|-|-|-|-|  
|**類別**|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|**內容功能表屬性**|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|不適用|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|**ToolTip**<br /><br /> **屬性**|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|不適用|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|**標頭範本**<br /><br /> **屬性**|<xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|**樣式屬性**|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <sup>1</sup>如**標頭範本內容**，如果您設定範本及範本選擇器內容、 範本屬性會優先採用。 例如，如果您同時設定<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>和<xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>屬性<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>屬性會優先。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)
