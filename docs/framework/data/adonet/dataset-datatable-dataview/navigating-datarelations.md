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
ms.openlocfilehash: 5b90b58595c86fc3c4dcaf7fd453c517d6f14904
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="navigating-datarelations"></a><span data-ttu-id="15c26-102">導覽 DataRelation</span><span class="sxs-lookup"><span data-stu-id="15c26-102">Navigating DataRelations</span></span>
<span data-ttu-id="15c26-103"><xref:System.Data.DataRelation> 的其中一個主要功能，是讓您可以從 <xref:System.Data.DataTable> 內的某個 <xref:System.Data.DataSet> 巡覽至另一個。</span><span class="sxs-lookup"><span data-stu-id="15c26-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="15c26-104">這可讓您擷取所有相關<xref:System.Data.DataRow>中其中一個物件**DataTable**時指定單一**DataRow**從相關**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="15c26-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="15c26-105">例如，在建立之後**DataRelation**客戶資料表和資料表之間的訂單，您可以擷取特定客戶的資料列使用的所有訂單資料列**GetChildRows**。</span><span class="sxs-lookup"><span data-stu-id="15c26-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="15c26-106">下列程式碼範例會建立**DataRelation**之間**客戶**資料表和**訂單**資料表**資料集**並傳回每個客戶的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="15c26-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="15c26-107">下一個範例則是以前述範例為基礎，在四個資料表之間建立關聯，並巡覽其中的關聯性。</span><span class="sxs-lookup"><span data-stu-id="15c26-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="15c26-108">如同先前的範例， **CustomerID**相關**客戶**資料表**訂單**資料表。</span><span class="sxs-lookup"><span data-stu-id="15c26-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="15c26-109">每個客戶在**客戶**資料表中的所有子資料列**訂單**判別都資料表，以傳回特定客戶的訂單數目和他們**OrderID**值。</span><span class="sxs-lookup"><span data-stu-id="15c26-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="15c26-110">展開的範例也會傳回的值從**OrderDetails**和**產品**資料表。</span><span class="sxs-lookup"><span data-stu-id="15c26-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="15c26-111">**訂單**資料表與相關**OrderDetails**資料表使用**OrderID**來判斷每個已排序客戶訂單、 產品和數量。</span><span class="sxs-lookup"><span data-stu-id="15c26-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="15c26-112">因為**OrderDetails**資料表僅包含**ProductID**訂購產品， **OrderDetails**相關**產品**使用**ProductID**以傳回**ProductName**。</span><span class="sxs-lookup"><span data-stu-id="15c26-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="15c26-113">在這項關聯**產品**資料表是父代和**Order Details**資料表是子系。</span><span class="sxs-lookup"><span data-stu-id="15c26-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="15c26-114">如此一來，當逐一查看時**OrderDetails**資料表**GetParentRow**呼叫以擷取相關**ProductName**值。</span><span class="sxs-lookup"><span data-stu-id="15c26-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="15c26-115">請注意，當**DataRelation**建立**客戶**和**訂單**資料表，會指定任何值**createConstraints**旗標 (預設值是**true**)。</span><span class="sxs-lookup"><span data-stu-id="15c26-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="15c26-116">這是假設所有中的資料列**訂單**資料表有**CustomerID**值存在於父**客戶**資料表。</span><span class="sxs-lookup"><span data-stu-id="15c26-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="15c26-117">如果**CustomerID**存在於**訂單**中不存在的資料表**客戶**資料表<xref:System.Data.ForeignKeyConstraint>，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="15c26-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="15c26-118">當子資料行可能包含不包含父資料行的值時，設定**createConstraints**旗標設為**false**加入時**DataRelation**。</span><span class="sxs-lookup"><span data-stu-id="15c26-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="15c26-119">在範例中， **createConstraints**旗標設為**false**如**DataRelation**之間**訂單**資料表和**OrderDetails**資料表。</span><span class="sxs-lookup"><span data-stu-id="15c26-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="15c26-120">這可讓應用程式來傳回所有的記錄從**OrderDetails**資料表和記錄的子集**訂單**資料表，而不會產生執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="15c26-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="15c26-121">展開範例會產生下列格式的輸出。</span><span class="sxs-lookup"><span data-stu-id="15c26-121">The expanded sample generates output in the following format.</span></span>  
  
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
  
 <span data-ttu-id="15c26-122">下列程式碼範例是展開的範例位置的值從**OrderDetails**和**產品**傳回資料表，只使用部分的記錄**訂單**資料表傳回。</span><span class="sxs-lookup"><span data-stu-id="15c26-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="15c26-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15c26-123">See Also</span></span>  
 [<span data-ttu-id="15c26-124">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="15c26-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="15c26-125">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="15c26-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
