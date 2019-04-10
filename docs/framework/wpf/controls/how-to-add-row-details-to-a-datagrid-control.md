---
title: HOW TO：將資料列詳細資料新增至 DataGrid 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: d5b6539f3d379088528b9654861267988b6fc69b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317883"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>HOW TO：將資料列詳細資料新增至 DataGrid 控制項
當使用<xref:System.Windows.Controls.DataGrid>控制項，您可以藉由新增資料列的詳細資料 區段中自訂資料呈現方式。 新增資料列詳細資料 區段可讓您將可選擇性地看見或是已摺疊的範本中的部分資料。 例如，您可以在其中新增資料列詳細資料，以<xref:System.Windows.Controls.DataGrid>其中會提供每個資料列的資料摘要<xref:System.Windows.Controls.DataGrid>，但是當使用者選取一個資料列會顯示更多資料欄位。 您定義的範本中的資料列詳細資料 區段<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>屬性。 下圖顯示資料列詳細資料區段的範例。  
  
 ![顯示資料列詳細資料的 DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 為內嵌 XAML 或資源，您會定義資料列詳細資料範本。 下列程序中會展示這兩個方法。 資料範本新增為資源可以使用在整個專案，而不需要重新建立範本。 資料範本新增為內嵌 XAML 就只能存取從控制項定義的位置。  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>若要使用內嵌 XAML 顯示資料列詳細資料  
  
1. 建立<xref:System.Windows.Controls.DataGrid>顯示來自資料來源的資料。  
  
2. 在 <xref:System.Windows.Controls.DataGrid> 項目中，加入 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 項目。  
  
3. 建立<xref:System.Windows.DataTemplate>，定義資料列的 [詳細資料] 區段的外觀。  
  
     下列 XAML 示範<xref:System.Windows.Controls.DataGrid>以及如何定義<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>內嵌。 <xref:System.Windows.Controls.DataGrid>顯示三個值在每個資料列和三個多個值時選取的資料列。  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     下列程式碼顯示用來選取的資料，會顯示在查詢<xref:System.Windows.Controls.DataGrid>。 在此範例中，查詢會從包含客戶資訊的實體選取資料。  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>若要使用的資源來顯示資料列詳細資料  
  
1. 建立<xref:System.Windows.Controls.DataGrid>顯示來自資料來源的資料。  
  
2. 新增<xref:System.Windows.FrameworkElement.Resources%2A>元素的根項目，例如<xref:System.Windows.Window>控制或<xref:System.Windows.Controls.Page>控制項，或是將<xref:System.Windows.Application.Resources%2A>項目<xref:System.Windows.Application>App.xaml （或 Application.xaml） 檔案中的類別。  
  
3. 在資源項目中，建立<xref:System.Windows.DataTemplate>，定義資料列的 [詳細資料] 區段的外觀。  
  
     下列 XAML 示範<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>中所定義<xref:System.Windows.Application>類別。  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. 在  <xref:System.Windows.DataTemplate>，將[X:key 指示詞](../../xaml-services/x-key-directive.md)唯一識別資料範本的值。  
  
5. 在 <xref:System.Windows.Controls.DataGrid>項目，設定<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>屬性，以在先前步驟中定義的資源。 將資源指派為靜態資源。  
  
     下列 XAML 顯示<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>屬性設定為 資源從先前的範例。  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>若要設定可見性，並避免水平捲動的資料列詳細資料  
  
1. 如有需要設定<xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A>屬性設<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>值。  
  
     根據預設，此值設為<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>。 您可以將它設定為<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible>以顯示所有資料列的詳細資料或<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed>隱藏所有資料列的詳細資料。  
  
2. 如有需要設定<xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A>屬性設`true`以避免資料列詳細資料從水平捲動的區段。
