---
title: 如何：將資料列詳細資料加入至 DataGrid 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: b6b0cc99c9833e514d2d52ecf139ab8e110f73e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>如何：將資料列詳細資料加入至 DataGrid 控制項
當使用<xref:System.Windows.Controls.DataGrid>控制項，可以自訂資料的呈現方式，藉由新增資料列詳細資料區段。 加入資料列詳細資料 區段可讓您群組中的範本，您可以選擇顯示或摺疊的部分資料。 例如，您可以加入資料列詳細資料，以<xref:System.Windows.Controls.DataGrid>其中會提供每個資料列的資料摘要<xref:System.Windows.Controls.DataGrid>，但在使用者選取一個資料列時，會帶來更多資料欄位。 您定義的範本中的資料列詳細資料區段<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>屬性。 下圖顯示資料列詳細資料區段的範例。  
  
 ![顯示資料列詳細資料的 DataGrid](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")  
  
 您可以定義資料列詳細資料範本做為內嵌 XAML 或資源。 下列程序中，會顯示這兩種方法。 資料範本新增為資源可在整個專案而不需要重新建立範本。 因為內嵌 XAML 只能存取從控制項定義的位置加入資料範本。  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>若要使用內嵌 XAML 來顯示資料列詳細資料  
  
1.  建立<xref:System.Windows.Controls.DataGrid>，會顯示從資料來源的資料。  
  
2.  在 <xref:System.Windows.Controls.DataGrid> 項目中，加入 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 項目。  
  
3.  建立<xref:System.Windows.DataTemplate>，定義資料列的 [詳細資料] 區段的外觀。  
  
     下列 XAML 顯示<xref:System.Windows.Controls.DataGrid>以及如何定義<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>內嵌。 <xref:System.Windows.Controls.DataGrid>顯示三個值的每個資料列和三個多個值在選取的資料列時。  
  
     [!code-xaml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     下列程式碼顯示用來選取資料中所顯示的查詢<xref:System.Windows.Controls.DataGrid>。 在此範例中，查詢會從包含客戶資訊的實體選取資料。  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>若要使用資源來顯示資料列詳細資料  
  
1.  建立<xref:System.Windows.Controls.DataGrid>，會顯示從資料來源的資料。  
  
2.  新增<xref:System.Windows.FrameworkElement.Resources%2A>元素的根元素，例如<xref:System.Windows.Window>控制項或<xref:System.Windows.Controls.Page>控制項，或是將<xref:System.Windows.Application.Resources%2A>元素<xref:System.Windows.Application>App.xaml （或 Application.xaml） 檔案中的類別。  
  
3.  在資源項目建立<xref:System.Windows.DataTemplate>，定義資料列的 [詳細資料] 區段的外觀。  
  
     下列 XAML 顯示<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>中定義<xref:System.Windows.Application>類別。  
  
     [!code-xaml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  在<xref:System.Windows.DataTemplate>，將[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)唯一識別資料範本的值。  
  
5.  在<xref:System.Windows.Controls.DataGrid>項目，設定<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>先前步驟中所定義的資源屬性。 將資源指派為靜態的資源。  
  
     下列 XAML 顯示<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>屬性設定為 資源從先前的範例。  
  
     [!code-xaml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>若要設定可見性，並防止水平捲動的資料列詳細資料  
  
1.  如有需要設定<xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A>屬性<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>值。  
  
     根據預設，此值設定為<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>。 您可以將它設定為<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible>以顯示所有資料列的詳細資料或<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed>隱藏所有資料列的詳細資料。  
  
2.  如有需要設定<xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A>屬性`true`以避免資料列詳細資料水平捲動的區段。
