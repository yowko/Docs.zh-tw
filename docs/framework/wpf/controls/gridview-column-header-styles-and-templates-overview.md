---
title: GridView 資料行行首樣式和範本概觀
ms.date: 03/30/2017
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
ms.openlocfilehash: 83643d8acea706bad439683702e4228d240b97bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911361"
---
# <a name="gridview-column-header-styles-and-templates-overview"></a>GridView 資料行行首樣式和範本概觀
本概觀將討論您用來自訂資料行標頭中的屬性的優先順序<xref:System.Windows.Controls.GridView>檢視模式<xref:System.Windows.Controls.ListView>控制項。  
  
## <a name="customizing-a-column-header-in-a-gridview"></a>自訂 GridView 中的資料行標頭  
 定義內容、 配置和樣式的資料行標頭中的屬性，<xref:System.Windows.Controls.GridView>許多相關的類別上找到。 其中某些屬性具有功能類似或相同。  
  
 下表中的資料列會顯示一組執行相同的函式的內容。 您可以使用這些屬性來自訂資料行標頭<xref:System.Windows.Controls.GridView>。 相關屬性的優先順序是由右至左最右側資料行中的屬性具有最高優先順序的位置。 比方說，如果<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>上設定<xref:System.Windows.Controls.GridViewColumnHeader>物件並<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>就會在相關聯集<xref:System.Windows.Controls.GridViewColumn>、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>會優先使用。 在此案例中，<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>沒有任何作用。  
  
 **在 GridView 資料行標頭的相關的屬性**  
  
|||||  
|-|-|-|-|  
|**類別**|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|**內容功能表屬性**|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|不適用|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|**ToolTip**<br /><br /> **屬性**|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|不適用|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|**標頭的範本**<br /><br /> **屬性**|<xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|**樣式屬性**|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <sup>1</sup>for**標頭的範本內容**，如果您設定的範本和範本選取器屬性，範本的屬性擁有優先權。 例如，如果您同時設定<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>並<xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>屬性，<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>屬性會優先。  
  
## <a name="see-also"></a>另請參閱

- [HOW-TO 主題](listview-how-to-topics.md)
- [ListView 概觀](listview-overview.md)
- [GridView 概觀](gridview-overview.md)
