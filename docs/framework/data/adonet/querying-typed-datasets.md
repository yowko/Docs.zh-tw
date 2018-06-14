---
title: 查詢具類型資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 30a6512202615590a4b399b8ce7173b213a8873c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353481"
---
# <a name="querying-typed-datasets"></a>查詢具類型資料集
如果在應用程式設計階段中便已知 <xref:System.Data.DataSet> 的結構描述，我們建議您在使用 <xref:System.Data.DataSet> 時使用具型別 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]。 具型別的<xref:System.Data.DataSet>是衍生自類別<xref:System.Data.DataSet>。 因此，它繼承了 <xref:System.Data.DataSet> 所有的方法、事件和屬性。 此外，具類型<xref:System.Data.DataSet>提供強型別的方法、 事件和屬性。 這表示，您可以依照名稱存取資料表和資料行，而不需要使用以集合為基礎的方法。 這讓查詢更簡單且更方便讀取。 如需詳細資訊，請參閱[型別資料集](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 也支援查詢具<xref:System.Data.DataSet>。 使用具型別的<xref:System.Data.DataSet>，您不必使用泛型<xref:System.Data.DataRowExtensions.Field%2A>方法或<xref:System.Data.DataRowExtensions.SetField%2A>方法來存取資料行的資料。  系統會在編譯時期提供屬性名稱，因為型別資訊包含在 <xref:System.Data.DataSet> 中。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 可讓您存取資料行值當做正確的型別，如此一來您就能在編譯程式碼時攔截型別不符的錯誤，而不必等到執行階段。  
  
 開始查詢具型別 <xref:System.Data.DataSet> 之前，您必須使用 [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] 中的 DataSet 設計工具來產生此類別。  如需詳細資訊，請參閱[建立和設定資料集](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)。  
  
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
 [查詢資料集](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [跨資料表查詢](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [單一資料表查詢](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
