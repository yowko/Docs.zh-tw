---
title: "操作說明：繫結至 ADO.NET 資料來源"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0eb555bb9f21385d2d0b66fe0dd39112c8350dec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="03f31-102">操作說明：繫結至 ADO.NET 資料來源</span><span class="sxs-lookup"><span data-stu-id="03f31-102">How to: Bind to an ADO.NET Data Source</span></span>
<span data-ttu-id="03f31-103">這個範例示範如何將繫結[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<xref:System.Windows.Controls.ListBox>控制權傳輸至[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`。</span><span class="sxs-lookup"><span data-stu-id="03f31-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03f31-104">範例</span><span class="sxs-lookup"><span data-stu-id="03f31-104">Example</span></span>  
 <span data-ttu-id="03f31-105">在這個範例中，`OleDbConnection` 物件會用於連接到資料來源，這個資料來源是連接字串中指定的 `Access MDB` 檔案。</span><span class="sxs-lookup"><span data-stu-id="03f31-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="03f31-106">建立連接之後，會建立 `OleDbDataAdpater` 物件。</span><span class="sxs-lookup"><span data-stu-id="03f31-106">After the connection is established, an `OleDbDataAdpater` object is created.</span></span> <span data-ttu-id="03f31-107">`OleDbDataAdpater` 物件會執行一個 select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] 陳述式，以從資料庫擷取資料錄集。</span><span class="sxs-lookup"><span data-stu-id="03f31-107">The `OleDbDataAdpater` object executes a select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="03f31-108">[!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] 命令的結果會透過呼叫 `OleDbDataAdapter` 的 `Fill` 方法，儲存在 `DataSet` 的 `DataTable` 中。</span><span class="sxs-lookup"><span data-stu-id="03f31-108">The results from the [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="03f31-109">這個範例中的 `DataTable` 名為 `BookTable`。</span><span class="sxs-lookup"><span data-stu-id="03f31-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="03f31-110">範例接著會設定<xref:System.Windows.FrameworkElement.DataContext%2A>屬性<xref:System.Windows.Controls.ListBox>至`DataSet`物件。</span><span class="sxs-lookup"><span data-stu-id="03f31-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="03f31-111">我們就可以繫結<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性<xref:System.Windows.Controls.ListBox>至`BookTable`的`DataSet`:</span><span class="sxs-lookup"><span data-stu-id="03f31-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>  
  
 [!code-xaml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="03f31-112">`BookItemTemplate`是<xref:System.Windows.DataTemplate>，定義資料的顯示方式：</span><span class="sxs-lookup"><span data-stu-id="03f31-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>  
  
 [!code-xaml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 <span data-ttu-id="03f31-113">`IntColorConverter` 會將 `int` 轉換成色彩。</span><span class="sxs-lookup"><span data-stu-id="03f31-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="03f31-114">這個轉換子中，使用<xref:System.Windows.Controls.TextBlock.Background%2A>色彩的第三個<xref:System.Windows.Controls.TextBlock>會出現綠色如果的值`NumPages`因小於 350 和紅色。</span><span class="sxs-lookup"><span data-stu-id="03f31-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="03f31-115">這裡不顯示轉換器的實作。</span><span class="sxs-lookup"><span data-stu-id="03f31-115">The implementation of the converter is not shown here.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f31-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03f31-116">See Also</span></span>  
 <xref:System.Windows.Data.BindingListCollectionView>  
 [<span data-ttu-id="03f31-117">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="03f31-117">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="03f31-118">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="03f31-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
