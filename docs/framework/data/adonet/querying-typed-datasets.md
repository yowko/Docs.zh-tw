---
title: 查詢具類型資料集
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: d956fd5f07c108146d20623bcf811266380c132c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560243"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="7ccd6-102">查詢具類型資料集</span><span class="sxs-lookup"><span data-stu-id="7ccd6-102">Query typed DataSets</span></span>

<span data-ttu-id="7ccd6-103">如果結構描述<xref:System.Data.DataSet>在應用程式的設計階段，我們建議您使用具型別的已知<xref:System.Data.DataSet>使用 LINQ to DataSet 時。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="7ccd6-104">具型別<xref:System.Data.DataSet>是衍生自類別<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7ccd6-105">因此，它繼承了 <xref:System.Data.DataSet> 所有的方法、事件和屬性。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7ccd6-106">此外，具型別<xref:System.Data.DataSet>提供強型別的方法、 事件和屬性。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="7ccd6-107">這表示，您可以依照名稱存取資料表和資料行，而不需要使用以集合為基礎的方法。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="7ccd6-108">這讓查詢更簡單且更方便讀取。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="7ccd6-109">如需詳細資訊，請參閱 < [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-109">For more information, see [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="7ccd6-110">LINQ to DataSet 也支援查詢具型別<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-110">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7ccd6-111">使用具型別<xref:System.Data.DataSet>，您就不必在使用泛型<xref:System.Data.DataRowExtensions.Field%2A>方法或<xref:System.Data.DataRowExtensions.SetField%2A>方法來存取資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="7ccd6-112">系統會在編譯時期提供屬性名稱，因為型別資訊包含在 <xref:System.Data.DataSet> 中。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7ccd6-113">LINQ to DataSet 提供存取資料行值為正確的類型，讓程式碼會編譯而不是在執行階段時攔截類型不符的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-113">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="7ccd6-114">您可以開始查詢具型別之前<xref:System.Data.DataSet>，您必須使用來產生類別**DataSet 設計工具**Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="7ccd6-115">如需詳細資訊，請參閱 <<c0> [ 建立和設定資料集](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="7ccd6-115">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="7ccd6-116">範例</span><span class="sxs-lookup"><span data-stu-id="7ccd6-116">Example</span></span>

<span data-ttu-id="7ccd6-117">下列範例將顯示具型別 <xref:System.Data.DataSet> 的查詢：</span><span class="sxs-lookup"><span data-stu-id="7ccd6-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7ccd6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ccd6-118">See also</span></span>

- [<span data-ttu-id="7ccd6-119">查詢資料集</span><span class="sxs-lookup"><span data-stu-id="7ccd6-119">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="7ccd6-120">跨資料表查詢</span><span class="sxs-lookup"><span data-stu-id="7ccd6-120">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="7ccd6-121">單一資料表查詢</span><span class="sxs-lookup"><span data-stu-id="7ccd6-121">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
