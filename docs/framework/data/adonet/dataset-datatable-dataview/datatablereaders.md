---
title: DataTableReader
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0e3f3da6554239b4f04e244d3339a4280e1add85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="datatablereaders"></a><span data-ttu-id="0bbad-102">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="0bbad-102">DataTableReaders</span></span>
<span data-ttu-id="0bbad-103"><xref:System.Data.DataTableReader> 會以一個或多個唯讀順向結果集的形式來呈現 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的內容。</span><span class="sxs-lookup"><span data-stu-id="0bbad-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="0bbad-104">當您建立**DataTableReader**從**DataTable**，產生**DataTableReader**物件包含一個結果集具有相同的資料為**DataTable**它是用來建立，除了已標示為已刪除的任何資料列。</span><span class="sxs-lookup"><span data-stu-id="0bbad-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="0bbad-105">資料行出現在相同的順序，與原始**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="0bbad-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="0bbad-106">A **DataTableReader**可能包含多個結果集，如果它由呼叫建立<xref:System.Data.DataSet.CreateDataReader%2A>。</span><span class="sxs-lookup"><span data-stu-id="0bbad-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="0bbad-107">結果會依照相同順序**Datatable**中**資料集**物件的<xref:System.Data.DataSet.Tables%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="0bbad-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0bbad-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="0bbad-108">In This Section</span></span>  
 [<span data-ttu-id="0bbad-109">建立 DataReader</span><span class="sxs-lookup"><span data-stu-id="0bbad-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="0bbad-110">討論如何建立**DataTableReader**物件。</span><span class="sxs-lookup"><span data-stu-id="0bbad-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="0bbad-111">導覽 DataTable</span><span class="sxs-lookup"><span data-stu-id="0bbad-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="0bbad-112">說明如何使用**讀取**方法來移動的內容**DataTableReader**。</span><span class="sxs-lookup"><span data-stu-id="0bbad-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bbad-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="0bbad-113">See Also</span></span>  
 [<span data-ttu-id="0bbad-114">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="0bbad-114">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="0bbad-115">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="0bbad-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
