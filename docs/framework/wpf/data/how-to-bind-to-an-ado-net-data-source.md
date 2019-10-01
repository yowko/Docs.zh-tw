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
ms.openlocfilehash: dbe34cba8f01320fbf37beea65ed95656e09395c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697134"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="ca8cc-102">HOW TO：繫結至 ADO.NET 資料來源</span><span class="sxs-lookup"><span data-stu-id="ca8cc-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="ca8cc-103">這個範例示範如何將 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 的 @no__t 1 控制項系結至 ADO.NET `DataSet`。</span><span class="sxs-lookup"><span data-stu-id="ca8cc-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an ADO.NET `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="ca8cc-104">範例</span><span class="sxs-lookup"><span data-stu-id="ca8cc-104">Example</span></span>

<span data-ttu-id="ca8cc-105">在這個範例中，`OleDbConnection` 物件會用於連接到資料來源，這個資料來源是連接字串中指定的 `Access MDB` 檔案。</span><span class="sxs-lookup"><span data-stu-id="ca8cc-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="ca8cc-106">建立連接之後，會建立 `OleDbDataAdapter` 物件。</span><span class="sxs-lookup"><span data-stu-id="ca8cc-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="ca8cc-107">@No__t 0 物件會執行 select 結構化查詢語言 (SQL) （SQL）語句，以從資料庫中取出記錄集。</span><span class="sxs-lookup"><span data-stu-id="ca8cc-107">The `OleDbDataAdapter` object executes a select Structured Query Language (SQL) statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="ca8cc-108">SQL 命令的結果會藉由呼叫 `OleDbDataAdapter` 的 `Fill` 方法，儲存在 @no__t 1 的 `DataTable` 中。</span><span class="sxs-lookup"><span data-stu-id="ca8cc-108">The results from the SQL command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="ca8cc-109">這個範例中的 `DataTable` 名為 `BookTable`。</span><span class="sxs-lookup"><span data-stu-id="ca8cc-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="ca8cc-110">然後，此範例會將 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性設定為 @no__t 2 物件。</span><span class="sxs-lookup"><span data-stu-id="ca8cc-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="ca8cc-111">然後，我們可以將 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性系結至 `DataSet` 的 `BookTable`：</span><span class="sxs-lookup"><span data-stu-id="ca8cc-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="ca8cc-112">`BookItemTemplate` 是定義資料顯示方式的 <xref:System.Windows.DataTemplate>：</span><span class="sxs-lookup"><span data-stu-id="ca8cc-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="ca8cc-113">`IntColorConverter` 會將 `int` 轉換成色彩。</span><span class="sxs-lookup"><span data-stu-id="ca8cc-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="ca8cc-114">使用此轉換器時，如果 `NumPages` 的值小於350，則第三個 @no__t 的 <xref:System.Windows.Controls.TextBlock.Background%2A> 色彩會顯示綠色，否則為紅色。</span><span class="sxs-lookup"><span data-stu-id="ca8cc-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="ca8cc-115">這裡不顯示轉換器的實作。</span><span class="sxs-lookup"><span data-stu-id="ca8cc-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca8cc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca8cc-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="ca8cc-117">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="ca8cc-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="ca8cc-118">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="ca8cc-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
