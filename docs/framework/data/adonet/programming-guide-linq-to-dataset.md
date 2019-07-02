---
title: 程式設計手冊 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
ms.openlocfilehash: d454448771e14b1a540b5a066683bd4c747991ec
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504772"
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="c7fd3-102">程式設計手冊 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="c7fd3-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="c7fd3-103">本節提供概念性資訊和範例使用 LINQ 進行程式設計資料集。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-103">This section provides conceptual information and examples for programming with LINQ to DataSet.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7fd3-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="c7fd3-104">In This Section</span></span>  
 [<span data-ttu-id="c7fd3-105">LINQ to DataSet 中的查詢</span><span class="sxs-lookup"><span data-stu-id="c7fd3-105">Queries in LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)  
 <span data-ttu-id="c7fd3-106">提供有關如何撰寫 LINQ to DataSet 查詢資訊。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-106">Provides information about how to write LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="c7fd3-107">查詢資料集</span><span class="sxs-lookup"><span data-stu-id="c7fd3-107">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="c7fd3-108">說明如何查詢 <xref:System.Data.DataSet> 物件。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="c7fd3-109">比較 DataRow</span><span class="sxs-lookup"><span data-stu-id="c7fd3-109">Comparing DataRows</span></span>](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="c7fd3-110">說明如何使用 <xref:System.Data.DataRowComparer> 物件來比較資料列。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="c7fd3-111">從查詢建立 DataTable</span><span class="sxs-lookup"><span data-stu-id="c7fd3-111">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="c7fd3-112">提供有關建立資訊<xref:System.Data.DataTable>從 LINQ to DataSet 查詢使用<xref:System.Data.DataTableExtensions.CopyToDataTable%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-112">Provides information about creating a <xref:System.Data.DataTable> from a LINQ to DataSet query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="c7fd3-113">如何：實作 CopyToDataTable\<T > 其中泛型型別 T 不是 DataRow</span><span class="sxs-lookup"><span data-stu-id="c7fd3-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="c7fd3-114">描述如何實作通用參數 T 不是 `CopyToDataTable<T>` 型別的自訂 <xref:System.Data.DataRow> 方法。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="c7fd3-115">泛型 Field 和 SetField 方法</span><span class="sxs-lookup"><span data-stu-id="c7fd3-115">Generic Field and SetField Methods</span></span>](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="c7fd3-116">提供有關泛型 <xref:System.Data.DataRowExtensions.Field%2A> 和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法的資訊。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="c7fd3-117">資料繫結和 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="c7fd3-117">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="c7fd3-118">說明如何使用 <xref:System.Data.DataView> 物件進行資料繫結。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="c7fd3-119">偵錯 LINQ to DataSet 查詢</span><span class="sxs-lookup"><span data-stu-id="c7fd3-119">Debugging LINQ to DataSet Queries</span></span>](../../../../docs/framework/data/adonet/debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="c7fd3-120">提供偵錯和疑難排解 LINQ to DataSet 查詢的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-120">Provides information about debugging and troubleshooting LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="c7fd3-121">安全性</span><span class="sxs-lookup"><span data-stu-id="c7fd3-121">Security</span></span>](../../../../docs/framework/data/adonet/security-linq-to-dataset.md)  
 <span data-ttu-id="c7fd3-122">描述 LINQ to DataSet 中的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-122">Describes security issues in LINQ to DataSet.</span></span>  
  
 [<span data-ttu-id="c7fd3-123">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="c7fd3-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 <span data-ttu-id="c7fd3-124">提供使用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 運算子的查詢範例。</span><span class="sxs-lookup"><span data-stu-id="c7fd3-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c7fd3-125">參考資料</span><span class="sxs-lookup"><span data-stu-id="c7fd3-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="c7fd3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7fd3-126">See also</span></span>

- [<span data-ttu-id="c7fd3-127">LINQ 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c7fd3-127">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="c7fd3-128">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c7fd3-128">Language Integrated Query (LINQ)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
