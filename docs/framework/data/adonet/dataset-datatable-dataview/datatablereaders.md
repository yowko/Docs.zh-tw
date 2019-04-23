---
title: DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: a790335a25327563e3dab6093449345b99afd048
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213997"
---
# <a name="datatablereaders"></a><span data-ttu-id="6123b-102">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="6123b-102">DataTableReaders</span></span>
<span data-ttu-id="6123b-103"><xref:System.Data.DataTableReader> 會以一個或多個唯讀順向結果集的形式來呈現 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的內容。</span><span class="sxs-lookup"><span data-stu-id="6123b-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="6123b-104">當您建立**DataTableReader**從**DataTable**，產生**DataTableReader**物件包含一個結果集具有相同的資料為**DataTable**從它建立，除了已標示為已刪除的任何資料列。</span><span class="sxs-lookup"><span data-stu-id="6123b-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="6123b-105">資料行出現在相同的順序，與原始**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="6123b-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="6123b-106">A **DataTableReader**可能包含多個結果集，如果它藉由呼叫建立<xref:System.Data.DataSet.CreateDataReader%2A>。</span><span class="sxs-lookup"><span data-stu-id="6123b-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="6123b-107">結果是在相同的順序**DataTables**中**資料集**物件的<xref:System.Data.DataSet.Tables%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="6123b-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6123b-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="6123b-108">In This Section</span></span>  
 [<span data-ttu-id="6123b-109">建立 DataReader</span><span class="sxs-lookup"><span data-stu-id="6123b-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="6123b-110">討論如何建立**DataTableReader**物件。</span><span class="sxs-lookup"><span data-stu-id="6123b-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="6123b-111">導覽 DataTable</span><span class="sxs-lookup"><span data-stu-id="6123b-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="6123b-112">說明如何使用**讀取**方法來移動的內容**DataTableReader**。</span><span class="sxs-lookup"><span data-stu-id="6123b-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6123b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6123b-113">See also</span></span>

- [<span data-ttu-id="6123b-114">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="6123b-114">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="6123b-115">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="6123b-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
