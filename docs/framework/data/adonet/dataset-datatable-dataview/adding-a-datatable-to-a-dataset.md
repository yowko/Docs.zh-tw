---
title: "將 DataTable 加入至資料集"
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
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f70292794866530de5b7abf7dac1edd09d300c94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="adding-a-datatable-to-a-dataset"></a><span data-ttu-id="a5034-102">將 DataTable 加入至資料集</span><span class="sxs-lookup"><span data-stu-id="a5034-102">Adding a DataTable to a DataSet</span></span>
<span data-ttu-id="a5034-103">ADO.NET 可讓您建立 <xref:System.Data.DataTable> 物件，並將它們加入現有的 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="a5034-103">ADO.NET enables you to create <xref:System.Data.DataTable> objects and add them to an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="a5034-104">您可以使用 <xref:System.Data.DataTable> 和 <xref:System.Data.DataTable.PrimaryKey%2A> 屬性，為 <xref:System.Data.DataColumn.Unique%2A> 設定條件約束 (Constraint) 資訊。</span><span class="sxs-lookup"><span data-stu-id="a5034-104">You can set constraint information for a <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.PrimaryKey%2A> and <xref:System.Data.DataColumn.Unique%2A> properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5034-105">範例</span><span class="sxs-lookup"><span data-stu-id="a5034-105">Example</span></span>  
 <span data-ttu-id="a5034-106">下列範例會建構 <xref:System.Data.DataSet>、將新的 <xref:System.Data.DataTable> 物件加入至 <xref:System.Data.DataSet>，然後再將三個 <xref:System.Data.DataColumn> 物件加入至資料表。</span><span class="sxs-lookup"><span data-stu-id="a5034-106">The following example constructs a <xref:System.Data.DataSet>, adds a new <xref:System.Data.DataTable> object to the <xref:System.Data.DataSet>, and then adds three <xref:System.Data.DataColumn> objects to the table.</span></span> <span data-ttu-id="a5034-107">最後，程式碼會將一個資料行設定為主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="a5034-107">Finally, the code sets one column as the primary key column.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a><span data-ttu-id="a5034-108">區分大小寫</span><span class="sxs-lookup"><span data-stu-id="a5034-108">Case Sensitivity</span></span>  
 <span data-ttu-id="a5034-109"><xref:System.Data.DataSet> 中可能有兩個或兩個以上具有相同名稱，但不同大小寫的資料表或關聯。</span><span class="sxs-lookup"><span data-stu-id="a5034-109">Two or more tables or relations with the same name, but different casing, can exist in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="a5034-110">在這種情況下，按照資料表和關聯名稱進行參考時是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="a5034-110">In such cases, references by name to tables and relations are case sensitive.</span></span> <span data-ttu-id="a5034-111">例如，如果<xref:System.Data.DataSet>**資料集**包含資料表**Table1**和**table1**，您應該要參考**Table1**使用名稱做為**dataSet.Tables["Table1"]**，和**table1**為**dataSet.Tables["table1"]**。</span><span class="sxs-lookup"><span data-stu-id="a5034-111">For example, if the <xref:System.Data.DataSet> **dataSet** contains tables **Table1** and **table1**, you would reference **Table1** by name as **dataSet.Tables["Table1"]**, and **table1** as **dataSet.Tables["table1"]**.</span></span> <span data-ttu-id="a5034-112">嘗試參考的資料表做為**dataSet.Tables["TABLE1"]**仍會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a5034-112">Attempting to reference either of the tables as **dataSet.Tables["TABLE1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="a5034-113">如果只有一個具有特定名稱的資料表或關聯，則不適用區分大小寫規則。</span><span class="sxs-lookup"><span data-stu-id="a5034-113">The case-sensitivity behavior does not apply if only one table or relation has a particular name.</span></span> <span data-ttu-id="a5034-114">例如，如果<xref:System.Data.DataSet>只剩**Table1**，您可以參考使用**dataSet.Tables["TABLE1"]**。</span><span class="sxs-lookup"><span data-stu-id="a5034-114">For example, if the <xref:System.Data.DataSet> has only **Table1**, you can reference it using **dataSet.Tables["TABLE1"]**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5034-115"><xref:System.Data.DataSet.CaseSensitive%2A> 的 <xref:System.Data.DataSet> 屬性不會影響這項行為。</span><span class="sxs-lookup"><span data-stu-id="a5034-115">The <xref:System.Data.DataSet.CaseSensitive%2A> property of the <xref:System.Data.DataSet> does not affect this behavior.</span></span> <span data-ttu-id="a5034-116"><xref:System.Data.DataSet.CaseSensitive%2A> 屬性會套用至 <xref:System.Data.DataSet> 內的資料，並影響排序、搜尋、篩選、強制執行條件約束等方面。</span><span class="sxs-lookup"><span data-stu-id="a5034-116">The <xref:System.Data.DataSet.CaseSensitive%2A> property applies to the data in the <xref:System.Data.DataSet> and affects sorting, searching, filtering, enforcing constraints, and so on.</span></span>  
  
## <a name="namespace-support"></a><span data-ttu-id="a5034-117">命名空間支援 </span><span class="sxs-lookup"><span data-stu-id="a5034-117">Namespace Support</span></span>  
 <span data-ttu-id="a5034-118">在 2.0 之前的 ADO.NET 版本中，兩個資料表不能有相同的名稱，即使它們在不同的命名空間也一樣。</span><span class="sxs-lookup"><span data-stu-id="a5034-118">In versions of ADO.NET earlier than 2.0, two tables could not have the same name, even if they were in different namespaces.</span></span> <span data-ttu-id="a5034-119">ADO.NET 2.0 已移除這項限制。</span><span class="sxs-lookup"><span data-stu-id="a5034-119">This limitation was removed in ADO.NET 2.0.</span></span> <span data-ttu-id="a5034-120"><xref:System.Data.DataSet> 可能會包含兩個 <xref:System.Data.DataTable.TableName%2A> 屬性值相同，但 <xref:System.Data.DataTable.Namespace%2A> 屬性值不同的資料表。</span><span class="sxs-lookup"><span data-stu-id="a5034-120">A <xref:System.Data.DataSet> can contain two tables that have the same <xref:System.Data.DataTable.TableName%2A> property value but different <xref:System.Data.DataTable.Namespace%2A> property values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5034-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5034-121">See Also</span></span>  
 [<span data-ttu-id="a5034-122">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="a5034-122">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="a5034-123">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="a5034-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
