---
title: "程式設計手冊 (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1332bf297dae4baae62d2abd731d236ad49be4ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="2607a-102">程式設計手冊 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="2607a-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="2607a-103">本節提供使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 進行程式設計的概念性資訊和範例。</span><span class="sxs-lookup"><span data-stu-id="2607a-103">This section provides conceptual information and examples for programming with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2607a-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="2607a-104">In This Section</span></span>  
 [<span data-ttu-id="2607a-105">在 LINQ to DataSet 查詢</span><span class="sxs-lookup"><span data-stu-id="2607a-105">Queries in LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)  
 <span data-ttu-id="2607a-106">提供有關如何撰寫 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢的資訊。</span><span class="sxs-lookup"><span data-stu-id="2607a-106">Provides information about how to write [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="2607a-107">查詢資料集</span><span class="sxs-lookup"><span data-stu-id="2607a-107">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="2607a-108">說明如何查詢 <xref:System.Data.DataSet> 物件。</span><span class="sxs-lookup"><span data-stu-id="2607a-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="2607a-109">比較 Datarow</span><span class="sxs-lookup"><span data-stu-id="2607a-109">Comparing DataRows</span></span>](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="2607a-110">說明如何使用 <xref:System.Data.DataRowComparer> 物件來比較資料列。</span><span class="sxs-lookup"><span data-stu-id="2607a-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="2607a-111">從查詢建立 DataTable</span><span class="sxs-lookup"><span data-stu-id="2607a-111">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="2607a-112">提供有關建立<xref:System.Data.DataTable>從[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢使用<xref:System.Data.DataTableExtensions.CopyToDataTable%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2607a-112">Provides information about creating a <xref:System.Data.DataTable> from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="2607a-113">如何： 實作 CopyToDataTable\<T > 其中泛型型別 T 不是 DataRow</span><span class="sxs-lookup"><span data-stu-id="2607a-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="2607a-114">描述如何實作通用參數 T 不是 `CopyToDataTable<T>` 型別的自訂 <xref:System.Data.DataRow> 方法。</span><span class="sxs-lookup"><span data-stu-id="2607a-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="2607a-115">泛型 Field 和 SetField 方法</span><span class="sxs-lookup"><span data-stu-id="2607a-115">Generic Field and SetField Methods</span></span>](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="2607a-116">提供有關泛型 <xref:System.Data.DataRowExtensions.Field%2A> 和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法的資訊。</span><span class="sxs-lookup"><span data-stu-id="2607a-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="2607a-117">資料繫結和 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="2607a-117">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="2607a-118">說明如何使用 <xref:System.Data.DataView> 物件進行資料繫結。</span><span class="sxs-lookup"><span data-stu-id="2607a-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="2607a-119">偵錯 LINQ to DataSet 查詢</span><span class="sxs-lookup"><span data-stu-id="2607a-119">Debugging LINQ to DataSet Queries</span></span>](../../../../docs/framework/data/adonet/debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="2607a-120">提供有關偵錯和疑難排解資訊[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="2607a-120">Provides information about debugging and troubleshooting [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="2607a-121">安全性</span><span class="sxs-lookup"><span data-stu-id="2607a-121">Security</span></span>](../../../../docs/framework/data/adonet/security-linq-to-dataset.md)  
 <span data-ttu-id="2607a-122">說明 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 中的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="2607a-122">Describes security issues in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
 [<span data-ttu-id="2607a-123">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="2607a-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 <span data-ttu-id="2607a-124">提供使用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 運算子的查詢範例。</span><span class="sxs-lookup"><span data-stu-id="2607a-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2607a-125">參考資料</span><span class="sxs-lookup"><span data-stu-id="2607a-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="2607a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2607a-126">See Also</span></span>  
 [<span data-ttu-id="2607a-127">LINQ to ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2607a-127">LINQ to ADO.NET</span></span>](http://msdn.microsoft.com/en-us/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 [<span data-ttu-id="2607a-128">不在組建中： LINQ 一般程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2607a-128">NOT IN BUILD: LINQ General Programming Guide</span></span>](http://msdn.microsoft.com/en-us/609c7a6b-cbdd-429d-99f3-78d13d3bc049)  
 [<span data-ttu-id="2607a-129">LINQ 架構</span><span class="sxs-lookup"><span data-stu-id="2607a-129">LINQ Framework</span></span>](http://msdn.microsoft.com/en-us/897ea0fc-40db-4694-bbe5-7dd339d5bf94)
