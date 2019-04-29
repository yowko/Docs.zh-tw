---
title: 導覽 DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: f4dfccad23bf5d15f5cbd0a33e76a136417e13ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607254"
---
# <a name="navigating-datarelations"></a>導覽 DataRelation
<xref:System.Data.DataRelation> 的其中一個主要功能，是讓您可以從 <xref:System.Data.DataTable> 內的某個 <xref:System.Data.DataSet> 巡覽至另一個。 這可讓您擷取所有相關<xref:System.Data.DataRow>物件，其中一**DataTable**時指定單一**DataRow**某個**DataTable**。 例如，在建立後，才能**DataRelation**客戶資料表與資料表之間的訂單，您可以擷取特定客戶的資料列使用的所有訂單資料列**GetChildRows**。  
  
 下列程式碼範例會建立**DataRelation**之間**客戶**資料表和**訂單**資料表**DataSet** ，並傳回每個客戶的所有訂單。  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 下一個範例則是以前述範例為基礎，在四個資料表之間建立關聯，並巡覽其中的關聯性。 如同先前的範例中， **CustomerID**與相關**客戶**資料表**訂單**資料表。 在每一位客戶**客戶**資料表中的所有子資料列**訂單**決定都資料表，以傳回特定客戶的訂單數目和其**OrderID**值。  
  
 展開的範例也會傳回的值從**OrderDetails**並**產品**資料表。 **訂單**資料表與相關**OrderDetails**資料表使用**OrderID**來判斷每個已排序的客戶訂單、 產品和數量。 因為**OrderDetails**資料表僅包含**ProductID**訂購的產品**OrderDetails**相關**產品**使用**ProductID**以傳回**ProductName**。 在這項關聯**產品**表格是父系和**訂單詳細資料**資料表是子系。 如此一來，當逐一查看**OrderDetails**資料表**GetParentRow**呼叫以擷取相關**ProductName**值。  
  
 請注意，當**DataRelation**建立**客戶**並**訂單**資料表，會指定任何值**createConstraints**旗標 (預設值是 **，則為 true**)。 這是假設所有的資料列**訂單**資料表有**CustomerID**存在的父系中的值**客戶**資料表。 如果**CustomerID**存在於**訂單**資料表，不存在於**客戶**資料表，<xref:System.Data.ForeignKeyConstraint>導致擲回例外狀況。  
  
 當子資料行可能包含父資料行不包含的值時，設定**createConstraints**旗標設為**false**加入時**DataRelation**。 在範例中， **createConstraints**旗標設為**false** for **DataRelation**之間**訂單**資料表以及**OrderDetails**資料表。 這可讓應用程式以傳回所有記錄**OrderDetails**資料表和記錄的子集**訂單**資料表，而不會產生執行階段例外狀況。 展開範例會產生下列格式的輸出。  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 下列程式碼範例是展開的範例位置中的值**OrderDetails**並**產品**會傳回資料表，只使用部分中記錄的**訂單**所傳回的資料表。  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
