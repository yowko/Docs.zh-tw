---
title: DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 911a45dad3d5d82ab5e5752b1c12f7d8a6ab1563
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202314"
---
# <a name="datatablereaders"></a><span data-ttu-id="0ffd5-102">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="0ffd5-102">DataTableReaders</span></span>

<span data-ttu-id="0ffd5-103"><xref:System.Data.DataTableReader> 會以一個或多個唯讀順向結果集的形式來呈現 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的內容。</span><span class="sxs-lookup"><span data-stu-id="0ffd5-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="0ffd5-104">當您從**DataTable**建立**DataTableReader**時，產生的**DataTableReader**物件會包含一個結果集，其中包含與建立它的**datatable**相同的資料，但已標示為已刪除的任何資料列除外。</span><span class="sxs-lookup"><span data-stu-id="0ffd5-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="0ffd5-105">資料行的顯示順序與原始 **DataTable**中的順序相同。</span><span class="sxs-lookup"><span data-stu-id="0ffd5-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="0ffd5-106">**DataTableReader**可能包含多個結果集（如果是藉由呼叫來建立） <xref:System.Data.DataSet.CreateDataReader%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0ffd5-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="0ffd5-107">結果會與**資料集**物件集合中的**datatable**順序相同 <xref:System.Data.DataSet.Tables%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0ffd5-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ffd5-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="0ffd5-108">In This Section</span></span>  

 [<span data-ttu-id="0ffd5-109">建立 DataReader</span><span class="sxs-lookup"><span data-stu-id="0ffd5-109">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="0ffd5-110">討論如何建立 **DataTableReader** 物件。</span><span class="sxs-lookup"><span data-stu-id="0ffd5-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="0ffd5-111">導覽 DataTable</span><span class="sxs-lookup"><span data-stu-id="0ffd5-111">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="0ffd5-112">描述如何使用 **Read** 方法來移動 **DataTableReader**的內容。</span><span class="sxs-lookup"><span data-stu-id="0ffd5-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ffd5-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ffd5-113">See also</span></span>

- [<span data-ttu-id="0ffd5-114">在 ADO.NET 中傳送和修改資料</span><span class="sxs-lookup"><span data-stu-id="0ffd5-114">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- <span data-ttu-id="0ffd5-115">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="0ffd5-115">[ADO.NET Overview](../ado-net-overview.md)</span></span>
