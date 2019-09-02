---
title: DataTableReader
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1ff7868b59c6fdc4e6c443be1b831accc84f36a6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203814"
---
# <a name="datatablereaders"></a><span data-ttu-id="cceeb-102">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="cceeb-102">DataTableReaders</span></span>
<span data-ttu-id="cceeb-103"><xref:System.Data.DataTableReader> 會以一個或多個唯讀順向結果集的形式來呈現 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 的內容。</span><span class="sxs-lookup"><span data-stu-id="cceeb-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="cceeb-104">當您從**datatable**建立**DataTableReader**時, 所產生的**DataTableReader**物件會包含一個結果集, 其資料會與建立它的**datatable**相同, 但已標示為的任何資料列除外刪除.</span><span class="sxs-lookup"><span data-stu-id="cceeb-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="cceeb-105">資料行會以與原始**DataTable**相同的順序出現。</span><span class="sxs-lookup"><span data-stu-id="cceeb-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="cceeb-106">如果**DataTableReader**是透過呼叫<xref:System.Data.DataSet.CreateDataReader%2A>來建立的, 則可能包含多個結果集。</span><span class="sxs-lookup"><span data-stu-id="cceeb-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="cceeb-107">結果會與**資料集**物件<xref:System.Data.DataSet.Tables%2A>集合中的**datatable**順序相同。</span><span class="sxs-lookup"><span data-stu-id="cceeb-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cceeb-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="cceeb-108">In This Section</span></span>  
 [<span data-ttu-id="cceeb-109">建立 DataReader</span><span class="sxs-lookup"><span data-stu-id="cceeb-109">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="cceeb-110">討論如何建立**DataTableReader**物件。</span><span class="sxs-lookup"><span data-stu-id="cceeb-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="cceeb-111">導覽 DataTable</span><span class="sxs-lookup"><span data-stu-id="cceeb-111">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="cceeb-112">描述如何使用**Read**方法, 在**DataTableReader**的內容之間移動。</span><span class="sxs-lookup"><span data-stu-id="cceeb-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cceeb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cceeb-113">See also</span></span>

- [<span data-ttu-id="cceeb-114">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="cceeb-114">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="cceeb-115">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="cceeb-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
