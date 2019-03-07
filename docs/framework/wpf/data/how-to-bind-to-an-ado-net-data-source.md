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
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="ce62d-102">HOW TO：繫結至 ADO.NET 資料來源</span><span class="sxs-lookup"><span data-stu-id="ce62d-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="ce62d-103">此範例示範如何繫結[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<xref:System.Windows.Controls.ListBox>若要控制[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`。</span><span class="sxs-lookup"><span data-stu-id="ce62d-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="ce62d-104">範例</span><span class="sxs-lookup"><span data-stu-id="ce62d-104">Example</span></span>

<span data-ttu-id="ce62d-105">在這個範例中，`OleDbConnection` 物件會用於連接到資料來源，這個資料來源是連接字串中指定的 `Access MDB` 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce62d-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="ce62d-106">建立連接之後，會建立 `OleDbDataAdapter` 物件。</span><span class="sxs-lookup"><span data-stu-id="ce62d-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="ce62d-107">`OleDbDataAdapter` 物件會執行一個 select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] 陳述式，以從資料庫擷取資料錄集。</span><span class="sxs-lookup"><span data-stu-id="ce62d-107">The `OleDbDataAdapter` object executes a select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="ce62d-108">[!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] 命令的結果會透過呼叫 `OleDbDataAdapter` 的 `Fill` 方法，儲存在 `DataSet` 的 `DataTable` 中。</span><span class="sxs-lookup"><span data-stu-id="ce62d-108">The results from the [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="ce62d-109">這個範例中的 `DataTable` 名為 `BookTable`。</span><span class="sxs-lookup"><span data-stu-id="ce62d-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="ce62d-110">範例接著會設定<xref:System.Windows.FrameworkElement.DataContext%2A>的屬性<xref:System.Windows.Controls.ListBox>到`DataSet`物件。</span><span class="sxs-lookup"><span data-stu-id="ce62d-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="ce62d-111">我們接著可以繫結<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>的屬性<xref:System.Windows.Controls.ListBox>要`BookTable`的`DataSet`:</span><span class="sxs-lookup"><span data-stu-id="ce62d-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="ce62d-112">`BookItemTemplate` 是<xref:System.Windows.DataTemplate>，定義資料的顯示方式：</span><span class="sxs-lookup"><span data-stu-id="ce62d-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="ce62d-113">`IntColorConverter` 會將 `int` 轉換成色彩。</span><span class="sxs-lookup"><span data-stu-id="ce62d-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="ce62d-114">藉由使用這個轉換子<xref:System.Windows.Controls.TextBlock.Background%2A>的第三個色彩<xref:System.Windows.Controls.TextBlock>顯示為綠色如果的值`NumPages`不小於 350，紅色。</span><span class="sxs-lookup"><span data-stu-id="ce62d-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="ce62d-115">這裡不顯示轉換器的實作。</span><span class="sxs-lookup"><span data-stu-id="ce62d-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce62d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce62d-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="ce62d-117">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="ce62d-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="ce62d-118">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="ce62d-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
