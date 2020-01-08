---
title: 使用 DataView 進行排序 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: 2998de7dee34f9b5410bfe53988e0b7cfa797784
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634751"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>使用 DataView 進行排序 (LINQ to DataSet)
根據特定準則來排序資料，然後透過 UI 控制項呈現資料給用戶端的功能是資料繫結的重要層面。 <xref:System.Data.DataView> 提供了許多方式來排序資料並傳回依據特定排序準則所排序的資料列。 除了以字串為基礎的排序功能之外，<xref:System.Data.DataView> 也可以讓您使用語言整合式查詢（LINQ）運算式來進行排序準則。 LINQ 運算式除了以字串為基礎的排序，還允許更複雜且功能更強大的排序作業。 本主題將說明兩種使用 <xref:System.Data.DataView> 進行排序的方法。  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>從含有排序資訊的查詢中建立 DataView  
 可以從 LINQ to DataSet 查詢建立 <xref:System.Data.DataView> 物件。 如果該查詢包含 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.ThenBy%2A>或 <xref:System.Linq.Enumerable.ThenByDescending%2A> 子句，這些子句中的運算式會當做排序 <xref:System.Data.DataView>中資料的基礎使用。 例如，如果查詢包含 `Order By…`和 `Then By…` 子句，則產生的 <xref:System.Data.DataView> 會依照指定的兩個數據行來排序資料。  
  
 以運算式為基礎的排序會比較簡單的以字串為基礎的排序提供功能更強大且更複雜的排序。 請注意，以字串為基礎的排序和以運算式為基礎的排序會互斥 (Mutually Exclusive)。 如果您從查詢中建立 <xref:System.Data.DataView.Sort%2A> 之後才設定以字串為基礎的 <xref:System.Data.DataView>，就會清除從查詢中推斷的以運算式為基礎的篩選，而且無法加以重設。  
  
 在您建立 <xref:System.Data.DataView> 以及修改任何排序或篩選資訊時，系統就會建立 <xref:System.Data.DataView> 的索引。 在建立 <xref:System.Data.DataView> 的 LINQ to DataSet 查詢中提供排序準則，並于稍後不修改排序資訊，以獲得最佳效能。 如需詳細資訊，請參閱[DataView Performance](dataview-performance.md)。  
  
> [!NOTE]
> 在大部分清況中，用於排序的運算式不應該具有副作用 (Side Effect) 而且必須具決定性。 此外，這些運算式不應該包含取決於固定執行次數的任何邏輯，因為排序作業可能會執行任何次數。  
  
### <a name="example"></a>範例  
 下列範例會查詢 SalesOrderHeader 資料表並依據訂單日期排序傳回的資料列、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>範例  
 下列範例會查詢 SalesOrderHeader 資料表並依據總金額排序傳回的資料列、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>範例  
 下列範例會查詢 SalesOrderDetail 資料表並先後依據訂單數量和銷售訂單識別碼排序傳回的資料列、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>使用以字串為基礎的 Sort 屬性  
 <xref:System.Data.DataView> 的以字串為基礎的排序功能仍適用于 LINQ to DataSet。 從 LINQ to DataSet 查詢建立 <xref:System.Data.DataView> 之後，您可以使用 <xref:System.Data.DataView.Sort%2A> 屬性來設定 <xref:System.Data.DataView>的排序。  
  
 以字串為基礎的排序和以運算式為基礎的排序功能會互斥。 因此，設定 <xref:System.Data.DataView.Sort%2A> 屬性將會清除繼承自查詢 (從中建立 <xref:System.Data.DataView>) 的以運算式為基礎的排序。  
  
 如需以字串為基礎 <xref:System.Data.DataView.Sort%2A> 篩選的詳細資訊，請參閱[排序和篩選資料](./dataset-datatable-dataview/sorting-and-filtering-data.md)。  
  
### <a name="example"></a>範例  
 下列範例會從 Contact 資料表中建立 <xref:System.Data.DataView> 並按照姓氏的遞減順序排序資料列，然後再按照名字的遞增順序排序資料列：  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>範例  
 下列範例會在 Contact 資料表中查詢是否有以字母 "S" 為開頭的姓氏。  <xref:System.Data.DataView> 是從該查詢中建立並繫結至 <xref:System.Windows.Forms.BindingSource> 物件。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>清除排序  
 在您已經使用 <xref:System.Data.DataView> 屬性來設定排序資訊之後，就可以清除 <xref:System.Data.DataView.Sort%2A> 上的排序資訊。 目前有兩種方式可以清除 <xref:System.Data.DataView> 中的排序資訊：  
  
- 將 <xref:System.Data.DataView.Sort%2A> 屬性設定為 `null`。  
  
- 將 <xref:System.Data.DataView.Sort%2A> 屬性設定為空字串。  
  
### <a name="example"></a>範例  
 下列範例會從查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView.Sort%2A> 屬性設定為空字串，藉以清除排序：  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>範例  
 下列範例會從 Contact 資料表中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView.Sort%2A> 屬性設定為按照姓氏的遞減順序排序。 然後，系統會將 <xref:System.Data.DataView.Sort%2A> 屬性設定為 `null`，藉以清除排序資訊：  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>請參閱

- [資料繫結和 LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [使用 DataView 進行篩選](filtering-with-dataview-linq-to-dataset.md)
- [排序資料](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))
