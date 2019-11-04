---
title: 操作說明：繫結至 ADO.NET 資料來源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: 0b3d7147f45bee5e8abd95bdc51c5f5f695cf830
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458401"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>操作說明：繫結至 ADO.NET 資料來源

這個範例示範如何將 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> 控制項系結至 ADO.NET `DataSet`。

## <a name="example"></a>範例

在這個範例中，`OleDbConnection` 物件會用於連接到資料來源，這個資料來源是連接字串中指定的 `Access MDB` 檔案。 建立連接之後，會建立 `OleDbDataAdapter` 物件。 `OleDbDataAdapter` 物件會執行 select 結構化查詢語言 (SQL) （SQL）語句，以從資料庫中取出記錄集。 SQL 命令的結果會藉由呼叫 `OleDbDataAdapter`的 `Fill` 方法，儲存在 `DataSet` 的 `DataTable` 中。 這個範例中的 `DataTable` 名為 `BookTable`。 然後，此範例會將 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性設定為 `DataSet` 物件。

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

然後，我們可以將 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性系結至 `DataSet`的 `BookTable`：

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate` 是定義資料顯示方式的 <xref:System.Windows.DataTemplate>：

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

`IntColorConverter` 會將 `int` 轉換成色彩。 使用此轉換器時，如果 `NumPages` 的值小於350，則第三個 <xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Background%2A> 色彩會顯示綠色，否則為紅色。 這裡不顯示轉換器的實作。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Data.BindingListCollectionView>
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
