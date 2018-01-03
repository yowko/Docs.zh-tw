---
title: "導覽 DataRelation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d7d1dc98bdb235c6501ee503494d3c2bdc3a1820
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="navigating-datarelations"></a>導覽 DataRelation
<xref:System.Data.DataRelation> 的其中一個主要功能，是讓您可以從 <xref:System.Data.DataTable> 內的某個 <xref:System.Data.DataSet> 巡覽至另一個。 這可讓您擷取所有相關<xref:System.Data.DataRow>中其中一個物件**DataTable**時指定單一**DataRow**從相關**DataTable**。 例如，在建立之後**DataRelation**客戶資料表和資料表之間的訂單，您可以擷取特定客戶的資料列使用的所有訂單資料列**GetChildRows**。  
  
 下列程式碼範例會建立**DataRelation**之間**客戶**資料表和**訂單**資料表**資料集**並傳回每個客戶的所有訂單。  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 下一個範例則是以前述範例為基礎，在四個資料表之間建立關聯，並巡覽其中的關聯性。 如同先前的範例， **CustomerID**相關**客戶**資料表**訂單**資料表。 每個客戶在**客戶**資料表中的所有子資料列**訂單**判別都資料表，以傳回特定客戶的訂單數目和他們**OrderID**值。  
  
 展開的範例也會傳回的值從**OrderDetails**和**產品**資料表。 **訂單**資料表與相關**OrderDetails**資料表使用**OrderID**來判斷每個已排序客戶訂單、 產品和數量。 因為**OrderDetails**資料表僅包含**ProductID**訂購產品， **OrderDetails**相關**產品**使用**ProductID**以傳回**ProductName**。 在這項關聯**產品**資料表是父代和**Order Details**資料表是子系。 如此一來，當逐一查看時**OrderDetails**資料表**GetParentRow**呼叫以擷取相關**ProductName**值。  
  
 請注意，當**DataRelation**建立**客戶**和**訂單**資料表，會指定任何值**createConstraints**旗標 (預設值是**true**)。 這是假設所有中的資料列**訂單**資料表有**CustomerID**值存在於父**客戶**資料表。 如果**CustomerID**存在於**訂單**中不存在的資料表**客戶**資料表<xref:System.Data.ForeignKeyConstraint>，會擲回例外狀況。  
  
 當子資料行可能包含不包含父資料行的值時，設定**createConstraints**旗標設為**false**加入時**DataRelation**。 在範例中， **createConstraints**旗標設為**false**如**DataRelation**之間**訂單**資料表和**OrderDetails**資料表。 這可讓應用程式來傳回所有的記錄從**OrderDetails**資料表和記錄的子集**訂單**資料表，而不會產生執行階段例外狀況。 展開範例會產生下列格式的輸出。  
  
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
  
 下列程式碼範例是展開的範例位置的值從**OrderDetails**和**產品**傳回資料表，只使用部分的記錄**訂單**資料表傳回。  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
