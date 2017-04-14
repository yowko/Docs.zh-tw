---
title: "瀏覽 DataRelation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 瀏覽 DataRelation
<xref:System.Data.DataRelation> 的其中一個主要功能，是讓您可以從 <xref:System.Data.DataSet> 內的某個 <xref:System.Data.DataTable> 巡覽至另一個。  這項功能可讓您在指定了相關 **DataTable** 的單一 **DataRow** 時，擷取某個 **DataTable** 中所有相關的 <xref:System.Data.DataRow> 物件。  例如，在客戶資料表和訂單資料表之間建立 **DataRelation** 之後，您就可以使用 **GetChildRows** 擷取特定客戶資料列的所有訂單資料列。  
  
 下列程式碼範例會在 **DataSet** 的 **Customers** 資料表與 **Orders** 資料表間建立 **DataRelation**，並傳回每個客戶的所有訂單。  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 下一個範例則是以前述範例為基礎，在四個資料表之間建立關聯，並巡覽其中的關聯性。  如前面範例所述，**CustomerID** 將 **Customers** 資料表關聯至 **Orders** 資料表。  針對 **Customers** 資料表中的每個客戶，在 **Orders** 資料表內都已有了對應的子資料列，這樣才能傳回特定客戶擁有的訂單數目和他們的 **OrderID** 值。  
  
 展開的範例也可傳回來自 **OrderDetails** 和 **Products** 資料表的值。  其中，**Orders** 資料表與 **OrderDetails** 資料表有關聯，並且可使用 **OrderID** 來判斷每個客戶訂單中所訂購的產品和數量。  由於 **OrderDetails** 資料表僅包含訂購產品的 **ProductID**，因此 **OrderDetails** 會使用 **ProductID** 來建立與 **Products** 的關聯，以傳回 **ProductName**。  在這項關聯中，**Products** 資料表為父代，而 **Order Details** 資料表為子系。  因此，逐一查看 **OrderDetails** 資料表時，會呼叫 **GetParentRow** 以擷取相關的 **ProductName** 值。  
  
 請注意，**Customers** 和 **Orders** 資料表的 **DataRelation** 建立後，**createConstraints** 旗標並沒有指定值 \(預設值為 **true**\)。  這是假設 **Orders** 資料表內所有的資料列都具有父 **Customers** 資料表的 **CustomerID** 值。  如果 **Orders** 資料表中的 **CustomerID** 不存在於 **Customers** 資料表中，<xref:System.Data.ForeignKeyConstraint> 就會擲回例外狀況。  
  
 若子資料行可能包含父資料行所沒有的值，請在加入 **DataRelation** 時，將 **createConstraints** 旗標設定為 **false**。  在此範例中，**Orders** 資料表和 **OrderDetails** 資料表間 **DataRelation** 所屬的 **createConstraints** 旗標是設定為 **false**。  這樣能使應用程式從 **OrderDetails** 資料表傳回所有資料，並只從 **Orders** 資料表傳回記錄的子集，而不會產生執行階段例外狀況。  展開範例會產生下列格式的輸出。  
  
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
  
 下列程式碼範例是展開的範例，其中傳回了 **OrderDetails** 和 **Products** 資料表的值，並只從 **Orders** 資料表傳回記錄的子集。  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## 請參閱  
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)