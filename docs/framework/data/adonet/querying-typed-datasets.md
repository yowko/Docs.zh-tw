---
title: 查詢具類型資料集
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: d956fd5f07c108146d20623bcf811266380c132c
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44270630"
---
# <a name="query-typed-datasets"></a>查詢具類型資料集

如果結構描述<xref:System.Data.DataSet>在應用程式的設計階段，我們建議您使用具型別的已知<xref:System.Data.DataSet>使用 LINQ to DataSet 時。 具型別<xref:System.Data.DataSet>是衍生自類別<xref:System.Data.DataSet>。 因此，它繼承了 <xref:System.Data.DataSet> 所有的方法、事件和屬性。 此外，具型別<xref:System.Data.DataSet>提供強型別的方法、 事件和屬性。 這表示，您可以依照名稱存取資料表和資料行，而不需要使用以集合為基礎的方法。 這讓查詢更簡單且更方便讀取。 如需詳細資訊，請參閱 < [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)。

LINQ to DataSet 也支援查詢具型別<xref:System.Data.DataSet>。 使用具型別<xref:System.Data.DataSet>，您就不必在使用泛型<xref:System.Data.DataRowExtensions.Field%2A>方法或<xref:System.Data.DataRowExtensions.SetField%2A>方法來存取資料行的資料。 系統會在編譯時期提供屬性名稱，因為型別資訊包含在 <xref:System.Data.DataSet> 中。 LINQ to DataSet 提供存取資料行值為正確的類型，讓程式碼會編譯而不是在執行階段時攔截類型不符的錯誤。

您可以開始查詢具型別之前<xref:System.Data.DataSet>，您必須使用來產生類別**DataSet 設計工具**Visual Studio 中。 如需詳細資訊，請參閱 <<c0> [ 建立和設定資料集](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)。

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

- [查詢資料集](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [跨資料表查詢](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [單一資料表查詢](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
