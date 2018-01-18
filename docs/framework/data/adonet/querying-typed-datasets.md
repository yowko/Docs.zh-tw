---
title: "查詢具類型資料集"
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
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fff678a54416e72f4be8c3fdfdcacec5a7d90af7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="querying-typed-datasets"></a><span data-ttu-id="6e975-102">查詢具類型資料集</span><span class="sxs-lookup"><span data-stu-id="6e975-102">Querying Typed DataSets</span></span>
<span data-ttu-id="6e975-103">如果在應用程式設計階段中便已知 <xref:System.Data.DataSet> 的結構描述，我們建議您在使用 <xref:System.Data.DataSet> 時使用具型別 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6e975-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="6e975-104">具型別的<xref:System.Data.DataSet>是衍生自類別<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="6e975-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6e975-105">因此，它繼承了 <xref:System.Data.DataSet> 所有的方法、事件和屬性。</span><span class="sxs-lookup"><span data-stu-id="6e975-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6e975-106">此外，具類型<xref:System.Data.DataSet>提供強型別的方法、 事件和屬性。</span><span class="sxs-lookup"><span data-stu-id="6e975-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="6e975-107">這表示，您可以依照名稱存取資料表和資料行，而不需要使用以集合為基礎的方法。</span><span class="sxs-lookup"><span data-stu-id="6e975-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="6e975-108">這讓查詢更簡單且更方便讀取。</span><span class="sxs-lookup"><span data-stu-id="6e975-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="6e975-109">如需詳細資訊，請參閱[型別資料集](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="6e975-109">For more information, see [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="6e975-110">也支援查詢具<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="6e975-110"> also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6e975-111">使用具型別的<xref:System.Data.DataSet>，您不必使用泛型<xref:System.Data.DataRowExtensions.Field%2A>方法或<xref:System.Data.DataRowExtensions.SetField%2A>方法來存取資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="6e975-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span>  <span data-ttu-id="6e975-112">系統會在編譯時期提供屬性名稱，因為型別資訊包含在 <xref:System.Data.DataSet> 中。</span><span class="sxs-lookup"><span data-stu-id="6e975-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="6e975-113"> 可讓您存取資料行值當做正確的型別，如此一來您就能在編譯程式碼時攔截型別不符的錯誤，而不必等到執行階段。</span><span class="sxs-lookup"><span data-stu-id="6e975-113"> provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>  
  
 <span data-ttu-id="6e975-114">開始查詢具型別 <xref:System.Data.DataSet> 之前，您必須使用 [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] 中的 DataSet 設計工具來產生此類別。</span><span class="sxs-lookup"><span data-stu-id="6e975-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the DataSet Designer in [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].</span></span>  <span data-ttu-id="6e975-115">如需詳細資訊，請參閱[建立和設定資料集](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="6e975-115">For more information, see [Create and configure datasets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e975-116">範例</span><span class="sxs-lookup"><span data-stu-id="6e975-116">Example</span></span>  
 <span data-ttu-id="6e975-117">下列範例將顯示具型別 <xref:System.Data.DataSet> 的查詢：</span><span class="sxs-lookup"><span data-stu-id="6e975-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e975-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="6e975-118">See Also</span></span>  
 [<span data-ttu-id="6e975-119">查詢資料集</span><span class="sxs-lookup"><span data-stu-id="6e975-119">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="6e975-120">跨資料表查詢</span><span class="sxs-lookup"><span data-stu-id="6e975-120">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [<span data-ttu-id="6e975-121">單一資料表查詢</span><span class="sxs-lookup"><span data-stu-id="6e975-121">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
