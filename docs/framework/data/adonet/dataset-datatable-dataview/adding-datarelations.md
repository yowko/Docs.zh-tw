---
title: 加入 DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 9cefc97e571f315a6a644e0a058d4283168ecb9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034507"
---
# <a name="adding-datarelations"></a>加入 DataRelation
在包含多個 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataTable> 中，可以使用 <xref:System.Data.DataRelation> 物件建立資料表間的關聯性、巡覽資料表，並從相關資料表傳回子資料列或父資料列。  
  
 建立所需的引數**DataRelation**是名稱**DataRelation**所建立，以及一或多個陣列<xref:System.Data.DataColumn>做為父和子資料行的參考關聯性中的資料行。 建立之後**DataRelation**，可以先使用資料表間巡覽並擷取值。  
  
 新增**DataRelation**要<xref:System.Data.DataSet>新增，根據預設，<xref:System.Data.UniqueConstraint>父資料表和<xref:System.Data.ForeignKeyConstraint>到子資料表。 如需有關這些預設條件約束的詳細資訊，請參閱 < [DataTable 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)。  
  
 下列程式碼範例會建立**DataRelation**使用兩個<xref:System.Data.DataTable>中的物件<xref:System.Data.DataSet>。 每個<xref:System.Data.DataTable>包含名為的資料行**CustID**，做為兩者之間的連結<xref:System.Data.DataTable>物件。 範例會新增單一**DataRelation**要**關聯**集合<xref:System.Data.DataSet>。 在範例中的第一個引數指定的名稱**DataRelation**所建立。 第二個引數設定父**DataColumn**和第三個引數設定子**DataColumn**。  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 A **DataRelation**還有**巢狀**屬性，當設定為**true**，導致從巢狀相關聯的資料列，從父資料表中的子資料表的資料列當撰寫為 XML 項目使用<xref:System.Data.DataSet.WriteXml%2A>。 如需詳細資訊，請參閱[在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)。  
  
## <a name="see-also"></a>另請參閱

- [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
