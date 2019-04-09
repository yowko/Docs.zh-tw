---
title: 建立資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d2d17056e6dcd29ef9b5c5e8c3024a32fce32bd5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118179"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="d44a4-102">建立資料集</span><span class="sxs-lookup"><span data-stu-id="d44a4-102">Creating a DataSet</span></span>
<span data-ttu-id="d44a4-103">您可呼叫 <xref:System.Data.DataSet> 建構函式 (Constructor) 來建立 <xref:System.Data.DataSet> 的執行個體 (Instance)。</span><span class="sxs-lookup"><span data-stu-id="d44a4-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="d44a4-104">選擇性地指定名稱引數。</span><span class="sxs-lookup"><span data-stu-id="d44a4-104">Optionally specify a name argument.</span></span> <span data-ttu-id="d44a4-105">如果您不指定 <xref:System.Data.DataSet> 的名稱，則名稱會設定為 "NewDataSet"。</span><span class="sxs-lookup"><span data-stu-id="d44a4-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="d44a4-106">您也可以根據現有的 <xref:System.Data.DataSet> 建立新的 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="d44a4-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d44a4-107">新的 <xref:System.Data.DataSet> 可以是：現有 <xref:System.Data.DataSet> 的完整複本；<xref:System.Data.DataSet> 的複製，該項目複製關聯式架構或結構描述，但是不包含任何來自現有 <xref:System.Data.DataSet> 的資料；或 <xref:System.Data.DataSet> 的子集，其中只包含來自現有的 <xref:System.Data.DataSet> 且使用 <xref:System.Data.DataSet.GetChanges%2A> 方法修改過的資料列。</span><span class="sxs-lookup"><span data-stu-id="d44a4-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="d44a4-108">如需詳細資訊，請參閱 <<c0> [ 複製的資料集內容](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="d44a4-108">For more information, see [Copying DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="d44a4-109">下列程式碼範例示範如何建構 <xref:System.Data.DataSet> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d44a4-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="d44a4-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d44a4-110">See also</span></span>

- [<span data-ttu-id="d44a4-111">從 DataAdapter 填入資料集</span><span class="sxs-lookup"><span data-stu-id="d44a4-111">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="d44a4-112">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="d44a4-112">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="d44a4-113">ADO.NET Managed 提供者和DataSet開發人員中心</span><span class="sxs-lookup"><span data-stu-id="d44a4-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
