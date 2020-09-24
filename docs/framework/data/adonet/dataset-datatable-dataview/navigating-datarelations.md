---
title: 導覽 DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 5eb2ee16712be5ccd5e9aa0af4dde22dcaaeea09
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148382"
---
# <a name="navigating-datarelations"></a>導覽 DataRelation

<xref:System.Data.DataRelation> 的其中一個主要功能，是讓您可以從 <xref:System.Data.DataTable> 內的某個 <xref:System.Data.DataSet> 巡覽至另一個。 這可讓您在 <xref:System.Data.DataRow> 指定來自相關**datatable**的單一**DataRow**時，從一個**datatable**中取出所有相關物件。 例如，在客戶資料表與訂單資料表之間建立 **DataRelation** 之後，您就可以使用 **GetChildRows**抓取特定客戶資料列的所有訂單資料列。  
  
 下列程式碼範例會在**Customers**資料表和**資料集**的**orders**資料表之間建立**DataRelation** ，並傳回每個客戶的所有訂單。  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 下一個範例則是以前述範例為基礎，在四個資料表之間建立關聯，並巡覽其中的關聯性。 如同上述範例， **CustomerID** 會將 **Customers** 資料表與 **Orders** 資料表產生關聯。 針對**Customers**資料表中的每個客戶，會決定**orders**資料表中的所有子資料列，以便傳回特定客戶擁有的訂單**數目及其訂單值。**  
  
 展開的範例也會傳回來自 **OrderDetails** 和 **Products** 資料表的值。 **Orders**資料表**與使用「訂單表**」的**OrderDetails**資料表相關，以決定每個客戶訂單的訂購產品和數量。 因為**OrderDetails**資料表只包含已訂購產品的**Productid** ，所以**OrderDetails**會與使用**ProductID**的**產品**相關，以便傳回**ProductName**。 在這種關聯性中， **Products** 資料表是父系，而 **Order Details** 資料表則是子系。 因此，逐一查看 **OrderDetails** 資料表時，會呼叫 **GetParentRow** 以抓取相關的 **ProductName** 值。  
  
 請注意，為**Customers**和**Orders**資料表建立**DataRelation**時，不會為**createConstraints**旗標指定值 (預設值為**true**) 。 這會假設 **Orders** 資料表中的所有資料列都有一個 **CustomerID** 值存在於父 **Customers** 資料表中。 如果**Orders**資料表中沒有**CustomerID**存在於**Customers**資料表中，則會擲回例外狀況 <xref:System.Data.ForeignKeyConstraint> 。  
  
 當子資料行可能包含父資料行不包含的值時，請在加入**DataRelation**時將**createConstraints**旗標設定為**false** 。 在此範例中， **Orders**資料表和**OrderDetails**資料表之間的**DataRelation** **createConstraints**旗標設為**false** 。 這可讓應用程式從 **OrderDetails** 資料表傳回所有記錄，而不會產生執行時間例外狀況，只傳回 **Orders** 資料表中的記錄子集。 展開範例會產生下列格式的輸出。  
  
```output  
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
  
 下列程式碼範例是展開的範例，其中會傳回來自 **OrderDetails** 和 **Products** 資料表的值，其中只會傳回 **Orders** 資料表中的記錄子集。  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
