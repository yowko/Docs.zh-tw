---
title: 程式設計手冊 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
ms.openlocfilehash: c971f0a92829df40a14631aaff353a268f277f11
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783200"
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="53bd9-102">程式設計手冊 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="53bd9-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="53bd9-103">本節提供使用 LINQ to DataSet 進行程式設計的概念性資訊和範例。</span><span class="sxs-lookup"><span data-stu-id="53bd9-103">This section provides conceptual information and examples for programming with LINQ to DataSet.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53bd9-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="53bd9-104">In This Section</span></span>  
 [<span data-ttu-id="53bd9-105">LINQ to DataSet 中的查詢</span><span class="sxs-lookup"><span data-stu-id="53bd9-105">Queries in LINQ to DataSet</span></span>](queries-in-linq-to-dataset.md)  
 <span data-ttu-id="53bd9-106">提供如何撰寫 LINQ to DataSet 查詢的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="53bd9-106">Provides information about how to write LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="53bd9-107">查詢資料集</span><span class="sxs-lookup"><span data-stu-id="53bd9-107">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="53bd9-108">說明如何查詢 <xref:System.Data.DataSet> 物件。</span><span class="sxs-lookup"><span data-stu-id="53bd9-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="53bd9-109">比較 DataRow</span><span class="sxs-lookup"><span data-stu-id="53bd9-109">Comparing DataRows</span></span>](comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="53bd9-110">說明如何使用 <xref:System.Data.DataRowComparer> 物件來比較資料列。</span><span class="sxs-lookup"><span data-stu-id="53bd9-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="53bd9-111">從查詢建立 DataTable</span><span class="sxs-lookup"><span data-stu-id="53bd9-111">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="53bd9-112">提供有關<xref:System.Data.DataTable> <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>使用方法從 LINQ to DataSet 查詢建立的資訊。</span><span class="sxs-lookup"><span data-stu-id="53bd9-112">Provides information about creating a <xref:System.Data.DataTable> from a LINQ to DataSet query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="53bd9-113">如何：在泛型\<類型 t 不是 DataRow 的情況下，執行 CopyToDataTable T ></span><span class="sxs-lookup"><span data-stu-id="53bd9-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="53bd9-114">描述如何實作通用參數 T 不是 `CopyToDataTable<T>` 型別的自訂 <xref:System.Data.DataRow> 方法。</span><span class="sxs-lookup"><span data-stu-id="53bd9-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="53bd9-115">泛型 Field 和 SetField 方法</span><span class="sxs-lookup"><span data-stu-id="53bd9-115">Generic Field and SetField Methods</span></span>](generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="53bd9-116">提供有關泛型 <xref:System.Data.DataRowExtensions.Field%2A> 和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法的資訊。</span><span class="sxs-lookup"><span data-stu-id="53bd9-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="53bd9-117">資料繫結和 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="53bd9-117">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="53bd9-118">說明如何使用 <xref:System.Data.DataView> 物件進行資料繫結。</span><span class="sxs-lookup"><span data-stu-id="53bd9-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="53bd9-119">偵錯 LINQ to DataSet 查詢</span><span class="sxs-lookup"><span data-stu-id="53bd9-119">Debugging LINQ to DataSet Queries</span></span>](debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="53bd9-120">提供有關 LINQ to DataSet 查詢的調試和疑難排解的資訊。</span><span class="sxs-lookup"><span data-stu-id="53bd9-120">Provides information about debugging and troubleshooting LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="53bd9-121">Security</span><span class="sxs-lookup"><span data-stu-id="53bd9-121">Security</span></span>](security-linq-to-dataset.md)  
 <span data-ttu-id="53bd9-122">說明 LINQ to DataSet 中的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="53bd9-122">Describes security issues in LINQ to DataSet.</span></span>  
  
 [<span data-ttu-id="53bd9-123">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="53bd9-123">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)  
 <span data-ttu-id="53bd9-124">提供使用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 運算子的查詢範例。</span><span class="sxs-lookup"><span data-stu-id="53bd9-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="53bd9-125">參考資料</span><span class="sxs-lookup"><span data-stu-id="53bd9-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="53bd9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53bd9-126">See also</span></span>

- [<span data-ttu-id="53bd9-127">LINQ 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="53bd9-127">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="53bd9-128">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="53bd9-128">Language Integrated Query (LINQ)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
