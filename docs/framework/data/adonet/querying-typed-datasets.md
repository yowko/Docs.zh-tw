---
title: 查詢具類型資料集
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 55714c4dae73cd17a849cc35681797dfa4266e3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782974"
---
# <a name="query-typed-datasets"></a>查詢具類型資料集

如果在應用程式設計<xref:System.Data.DataSet>時間知道的架構，我們建議您在使用 LINQ to DataSet 時使用具<xref:System.Data.DataSet>類型的。 具類型<xref:System.Data.DataSet>的是衍生自的<xref:System.Data.DataSet>類別。 因此，它繼承了 <xref:System.Data.DataSet> 所有的方法、事件和屬性。 此外，具類型<xref:System.Data.DataSet>的會提供強型別方法、事件和屬性。 這表示，您可以依照名稱存取資料表和資料行，而不需要使用以集合為基礎的方法。 這讓查詢更簡單且更方便讀取。 如需詳細資訊，請參閱具[類型的資料集](./dataset-datatable-dataview/typed-datasets.md)。

LINQ to DataSet 也支援對具類型<xref:System.Data.DataSet>的查詢。 使用具類型<xref:System.Data.DataSet>的時，您不需要使用泛型<xref:System.Data.DataRowExtensions.Field%2A>方法或<xref:System.Data.DataRowExtensions.SetField%2A>方法來存取資料行資料。 系統會在編譯時期提供屬性名稱，因為型別資訊包含在 <xref:System.Data.DataSet> 中。 LINQ to DataSet 提供資料行值的存取權做為正確的類型，因此在編譯器代碼而不是在執行時間時，會攔截到類型不符的錯誤。

在您可以開始查詢<xref:System.Data.DataSet>具型別之前，您必須使用 Visual Studio 中的**DataSet 設計**工具來產生類別。 如需詳細資訊，請參閱[建立和設定資料集](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)。

## <a name="example"></a>範例

下列範例將顯示具型別 <xref:System.Data.DataSet> 的查詢：

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a>另請參閱

- [查詢資料集](querying-datasets-linq-to-dataset.md)
- [跨資料表查詢](cross-table-queries-linq-to-dataset.md)
- [單一資料表查詢](single-table-queries-linq-to-dataset.md)
