---
title: HOW TO：繫結至 ADO.NET 資料來源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: 08933e67c2cc4b7ccfb6ae0c9dfde34f40e4e5f5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465541"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>HOW TO：繫結至 ADO.NET 資料來源

此範例示範如何繫結[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<xref:System.Windows.Controls.ListBox>若要控制[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`。

## <a name="example"></a>範例

在這個範例中，`OleDbConnection` 物件會用於連接到資料來源，這個資料來源是連接字串中指定的 `Access MDB` 檔案。 建立連接之後，會建立 `OleDbDataAdapter` 物件。 `OleDbDataAdapter` 物件會執行一個 select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] 陳述式，以從資料庫擷取資料錄集。 [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] 命令的結果會透過呼叫 `OleDbDataAdapter` 的 `Fill` 方法，儲存在 `DataSet` 的 `DataTable` 中。 這個範例中的 `DataTable` 名為 `BookTable`。 範例接著會設定<xref:System.Windows.FrameworkElement.DataContext%2A>的屬性<xref:System.Windows.Controls.ListBox>到`DataSet`物件。

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

我們接著可以繫結<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>的屬性<xref:System.Windows.Controls.ListBox>要`BookTable`的`DataSet`:

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate` 是<xref:System.Windows.DataTemplate>，定義資料的顯示方式：

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

`IntColorConverter` 會將 `int` 轉換成色彩。 藉由使用這個轉換子<xref:System.Windows.Controls.TextBlock.Background%2A>的第三個色彩<xref:System.Windows.Controls.TextBlock>顯示為綠色如果的值`NumPages`不小於 350，紅色。 這裡不顯示轉換器的實作。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.BindingListCollectionView>
- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
