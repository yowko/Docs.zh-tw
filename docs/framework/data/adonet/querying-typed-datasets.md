---
title: 查詢具類型資料集
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 55714c4dae73cd17a849cc35681797dfa4266e3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782974"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="9e531-102">查詢具類型資料集</span><span class="sxs-lookup"><span data-stu-id="9e531-102">Query typed DataSets</span></span>

<span data-ttu-id="9e531-103">如果在應用程式設計<xref:System.Data.DataSet>時間知道的架構，我們建議您在使用 LINQ to DataSet 時使用具<xref:System.Data.DataSet>類型的。</span><span class="sxs-lookup"><span data-stu-id="9e531-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="9e531-104">具類型<xref:System.Data.DataSet>的是衍生自的<xref:System.Data.DataSet>類別。</span><span class="sxs-lookup"><span data-stu-id="9e531-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9e531-105">因此，它繼承了 <xref:System.Data.DataSet> 所有的方法、事件和屬性。</span><span class="sxs-lookup"><span data-stu-id="9e531-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9e531-106">此外，具類型<xref:System.Data.DataSet>的會提供強型別方法、事件和屬性。</span><span class="sxs-lookup"><span data-stu-id="9e531-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="9e531-107">這表示，您可以依照名稱存取資料表和資料行，而不需要使用以集合為基礎的方法。</span><span class="sxs-lookup"><span data-stu-id="9e531-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="9e531-108">這讓查詢更簡單且更方便讀取。</span><span class="sxs-lookup"><span data-stu-id="9e531-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="9e531-109">如需詳細資訊，請參閱具[類型的資料集](./dataset-datatable-dataview/typed-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="9e531-109">For more information, see [Typed DataSets](./dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="9e531-110">LINQ to DataSet 也支援對具類型<xref:System.Data.DataSet>的查詢。</span><span class="sxs-lookup"><span data-stu-id="9e531-110">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9e531-111">使用具類型<xref:System.Data.DataSet>的時，您不需要使用泛型<xref:System.Data.DataRowExtensions.Field%2A>方法或<xref:System.Data.DataRowExtensions.SetField%2A>方法來存取資料行資料。</span><span class="sxs-lookup"><span data-stu-id="9e531-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="9e531-112">系統會在編譯時期提供屬性名稱，因為型別資訊包含在 <xref:System.Data.DataSet> 中。</span><span class="sxs-lookup"><span data-stu-id="9e531-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9e531-113">LINQ to DataSet 提供資料行值的存取權做為正確的類型，因此在編譯器代碼而不是在執行時間時，會攔截到類型不符的錯誤。</span><span class="sxs-lookup"><span data-stu-id="9e531-113">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="9e531-114">在您可以開始查詢<xref:System.Data.DataSet>具型別之前，您必須使用 Visual Studio 中的**DataSet 設計**工具來產生類別。</span><span class="sxs-lookup"><span data-stu-id="9e531-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="9e531-115">如需詳細資訊，請參閱[建立和設定資料集](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="9e531-115">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="9e531-116">範例</span><span class="sxs-lookup"><span data-stu-id="9e531-116">Example</span></span>

<span data-ttu-id="9e531-117">下列範例將顯示具型別 <xref:System.Data.DataSet> 的查詢：</span><span class="sxs-lookup"><span data-stu-id="9e531-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9e531-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e531-118">See also</span></span>

- [<span data-ttu-id="9e531-119">查詢資料集</span><span class="sxs-lookup"><span data-stu-id="9e531-119">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="9e531-120">跨資料表查詢</span><span class="sxs-lookup"><span data-stu-id="9e531-120">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="9e531-121">單一資料表查詢</span><span class="sxs-lookup"><span data-stu-id="9e531-121">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)
