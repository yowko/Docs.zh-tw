---
title: 如何：使用 GridView 顯示 ListView 內容
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 103a439b9cee959d0077e5a759364eb9b943905d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>如何：使用 GridView 顯示 ListView 內容
這個範例示範如何定義<xref:System.Windows.Controls.GridView>檢視模式<xref:System.Windows.Controls.ListView>控制項。  
  
## <a name="example"></a>範例  
 您可以定義的檢視模式<xref:System.Windows.Controls.GridView>藉由指定<xref:System.Windows.Controls.GridViewColumn>物件。 下列範例示範如何定義<xref:System.Windows.Controls.GridViewColumn>繫結至指定的資料內容的物件<xref:System.Windows.Controls.ListView>控制項。 這<xref:System.Windows.Controls.GridView>範例會指定三個<xref:System.Windows.Controls.GridViewColumn>物件對應至`FirstName`， `LastName`，和`EmployeeNumber`欄位`EmployeeInfoDataSource`設定為<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>的<xref:System.Windows.Controls.ListView>控制項。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下圖顯示此範例中的顯示方式。  
  
 ![含有 GridView 輸出的 ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
