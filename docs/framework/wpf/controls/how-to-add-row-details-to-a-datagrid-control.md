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
ms.openlocfilehash: 4db414e1907d42071f7251c390077d4020fa577c
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559673"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>如何：將資料列詳細資料加入至 DataGrid 控制項
使用 <xref:System.Windows.Controls.DataGrid> 控制項時，您可以藉由加入資料列詳細資料區段來自訂資料呈現方式。 加入 [資料列詳細資料] 區段可讓您在範本中，將可選擇性地顯示或折迭的某些資料群組起來。 例如，您可以將資料列詳細資料加入至僅顯示 <xref:System.Windows.Controls.DataGrid>中每個資料列之資料摘要的 <xref:System.Windows.Controls.DataGrid>，但當使用者選取資料列時，會顯示更多的資料欄位。 您可以在 [<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>] 屬性中定義 [資料列詳細資料] 區段的範本。 下圖顯示資料列詳細資料區段的範例。  
  
 ![以資料列詳細資料顯示的 DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 您可以將資料列詳細資料範本定義為內嵌 XAML 或資源。 下列程式會顯示這兩種方法。 新增為資源的資料範本可以在整個專案中使用，而不需要重新建立範本。 加入為內嵌 XAML 的資料範本只能從其定義所在的控制項存取。  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>若要使用內嵌 XAML 顯示資料列詳細資料  
  
1. 建立顯示資料來源資料的 <xref:System.Windows.Controls.DataGrid>。  
  
2. 在 <xref:System.Windows.Controls.DataGrid> 項目中，加入 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 項目。  
  
3. 建立定義 [資料列詳細資料] 區段外觀的 <xref:System.Windows.DataTemplate>。  
  
     下列 XAML 會顯示 <xref:System.Windows.Controls.DataGrid> 以及如何定義內嵌 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>。 當選取資料列時，<xref:System.Windows.Controls.DataGrid> 會在每個資料列中顯示三個值，以及三個更多的值。  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     下列程式碼顯示用來選取 <xref:System.Windows.Controls.DataGrid>中所顯示之資料的查詢。 在此範例中，查詢會從包含客戶資訊的實體選取資料。  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>使用資源顯示資料列詳細資料  
  
1. 建立顯示資料來源資料的 <xref:System.Windows.Controls.DataGrid>。  
  
2. 將 <xref:System.Windows.FrameworkElement.Resources%2A> 元素新增至根項目（例如 <xref:System.Windows.Window> 控制項或 <xref:System.Windows.Controls.Page> 控制項），或將 <xref:System.Windows.Application.Resources%2A> 專案加入至 app.xaml （或 app.xaml）檔案中的 <xref:System.Windows.Application> 類別。  
  
3. 在 resources 元素中，建立定義 [資料列詳細資料] 區段外觀的 <xref:System.Windows.DataTemplate>。  
  
     下列 XAML 會顯示 <xref:System.Windows.Application> 類別中定義的 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>。  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. 在 <xref:System.Windows.DataTemplate>上，將  [x：Key](../../../desktop-wpf/xaml-services/xkey-directive.md)  指示詞設定為可唯一識別資料範本的值。  
  
5. 在 <xref:System.Windows.Controls.DataGrid> 元素中，將 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 屬性設定為先前步驟中定義的資源。 將資源指派為靜態資源。  
  
     下列 XAML 顯示 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 屬性設定為上一個範例中的資源。  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>若要設定可見度並防止水準滾動列詳細資料  
  
1. 如有需要，請將 <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> 屬性設定為 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> 值。  
  
     依預設，此值設定為 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>。 您可以將它設定為 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible>，以顯示所有資料列的詳細資料，或 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> 隱藏所有資料列的詳細資訊。  
  
2. 如有需要，請將 <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> 屬性設定為 [`true`]，以防止資料列詳細資料區段水準滾動。
