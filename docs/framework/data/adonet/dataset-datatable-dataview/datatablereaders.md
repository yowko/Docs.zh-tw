---
title: DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1559cde9cb786ccb2baf920347064b8b28d472c3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785352"
---
# <a name="datatablereaders"></a><span data-ttu-id="f7d3f-102">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="f7d3f-102">DataTableReaders</span></span>
<span data-ttu-id="f7d3f-103"><xref:System.Data.DataTableReader> 會以一個或多個唯讀順向結果集的形式來呈現 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的內容。</span><span class="sxs-lookup"><span data-stu-id="f7d3f-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="f7d3f-104">當您從**datatable**建立**DataTableReader**時，所產生的**DataTableReader**物件會包含一個結果集，其資料會與建立它的**datatable**相同，但已標示為的任何資料列除外刪除.</span><span class="sxs-lookup"><span data-stu-id="f7d3f-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="f7d3f-105">資料行會以與原始**DataTable**相同的順序出現。</span><span class="sxs-lookup"><span data-stu-id="f7d3f-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="f7d3f-106">如果**DataTableReader**是透過呼叫<xref:System.Data.DataSet.CreateDataReader%2A>來建立的，則可能包含多個結果集。</span><span class="sxs-lookup"><span data-stu-id="f7d3f-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="f7d3f-107">結果會與**資料集**物件<xref:System.Data.DataSet.Tables%2A>集合中的**datatable**順序相同。</span><span class="sxs-lookup"><span data-stu-id="f7d3f-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7d3f-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="f7d3f-108">In This Section</span></span>  
 [<span data-ttu-id="f7d3f-109">建立 DataReader</span><span class="sxs-lookup"><span data-stu-id="f7d3f-109">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="f7d3f-110">討論如何建立**DataTableReader**物件。</span><span class="sxs-lookup"><span data-stu-id="f7d3f-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="f7d3f-111">導覽 DataTable</span><span class="sxs-lookup"><span data-stu-id="f7d3f-111">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="f7d3f-112">描述如何使用**Read**方法，在**DataTableReader**的內容之間移動。</span><span class="sxs-lookup"><span data-stu-id="f7d3f-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d3f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7d3f-113">See also</span></span>

- [<span data-ttu-id="f7d3f-114">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="f7d3f-114">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="f7d3f-115">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="f7d3f-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
