---
title: 加入 DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: fde1e2ace09e31234d199876ae7f063e01e7a7e4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203976"
---
# <a name="adding-datarelations"></a>加入 DataRelation
在包含多個 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataTable> 中，可以使用 <xref:System.Data.DataRelation> 物件建立資料表間的關聯性、巡覽資料表，並從相關資料表傳回子資料列或父資料列。  
  
 建立**datarelation**所需的引數是所建立之**datarelation**的名稱, 以及一個或多個<xref:System.Data.DataColumn>參考的陣列, 這些資料行是做為關聯性中的父系和子資料行。 建立**DataRelation**之後, 您可以使用它在資料表之間流覽, 並取得值。  
  
 根據預設 , <xref:System.Data.DataSet> <xref:System.Data.ForeignKeyConstraint>將 DataRelation 加入至父資料表, 並將加入至子資料工作表。 <xref:System.Data.UniqueConstraint> 如需這些預設條件約束的詳細資訊, 請參閱[DataTable 條件約束](datatable-constraints.md)。  
  
 下列程式碼範例會在中<xref:System.Data.DataSet>使用兩<xref:System.Data.DataTable>個物件來建立**DataRelation** 。 每<xref:System.Data.DataTable>個都包含一個名為**CustID**的資料行, 其可做<xref:System.Data.DataTable>為兩個物件之間的連結。 這個範例會將單一**DataRelation**加入的關聯性<xref:System.Data.DataSet>集合。 範例中的第一個引數會指定所建立之**DataRelation**的名稱。 第二個引數會設定父系**datacolumn** , 而第三個引數會設定子**datacolumn**。  
  
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
  
 **DataRelation**也有一個**Nested**屬性, 當設定為**true**時, 會導致子資料工作表的資料列在使用<xref:System.Data.DataSet.WriteXml%2A>當做 XML 專案寫入時, 從父資料表的相關資料列中加以嵌套。 如需詳細資訊，請參閱[在 DataSet 中使用 XML](using-xml-in-a-dataset.md)。  
  
## <a name="see-also"></a>另請參閱

- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
