---
title: 加入 DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 5fe2bd45e0abada1f9ec7071e3863da853479b51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202379"
---
# <a name="adding-datarelations"></a>加入 DataRelation

在包含多個 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataTable> 中，可以使用 <xref:System.Data.DataRelation> 物件建立資料表間的關聯性、巡覽資料表，並從相關資料表傳回子資料列或父資料列。  
  
 建立 **datarelation** 所需的引數是要建立之 **datarelation** 的名稱，以及一或多個資料行參考的陣列，這些資料行會當做 <xref:System.Data.DataColumn> 關聯性中的父資料行和子資料行。 建立 **DataRelation**之後，您可以使用它在資料表之間進行導覽，並取得值。  
  
 依預設，將 **DataRelation** 加入至 <xref:System.Data.DataSet> <xref:System.Data.UniqueConstraint> 父資料表和 <xref:System.Data.ForeignKeyConstraint> 子資料工作表。 如需這些預設條件約束的詳細資訊，請參閱 [DataTable 條件約束](datatable-constraints.md)。  
  
 下列程式碼範例會在中使用兩個物件來建立 **DataRelation** <xref:System.Data.DataTable> <xref:System.Data.DataSet> 。 每個都 <xref:System.Data.DataTable> 包含一個名為 **CustID**的資料行，此資料行會做為兩個物件之間的連結 <xref:System.Data.DataTable> 。 此範例會將單一 **DataRelation** 新增至 **的關聯集合** <xref:System.Data.DataSet> 。 範例中的第一個引數會指定要建立之 **DataRelation** 的名稱。 第二個引數會設定父 **datacolumn** ，而第三個引數會設定子 **datacolumn**。  
  
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
  
 **DataRelation**也有一個**Nested**屬性，當設為**true**時，會讓子資料工作表中的資料列在使用撰寫為 XML 專案時，從父資料表的相關資料列中嵌套 <xref:System.Data.DataSet.WriteXml%2A> 。 如需詳細資訊，請參閱[在 DataSet 中使用 XML](using-xml-in-a-dataset.md)。  
  
## <a name="see-also"></a>另請參閱

- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
