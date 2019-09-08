---
title: 建立 DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 79cb2ce7ffae81aeba9aaca557e37ba566a8370c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784760"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="68c43-102">建立 DataReader</span><span class="sxs-lookup"><span data-stu-id="68c43-102">Creating a DataReader</span></span>
<span data-ttu-id="68c43-103"><xref:System.Data.DataTable> 和 <xref:System.Data.DataSet> 類別 (Class) 具有 <xref:System.Data.DataTable.CreateDataReader%2A> 方法，可以用一或多個唯讀的順向結果集來傳回 <xref:System.Data.DataTable> 的內容或 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataSet.Tables%2A> 集合內容。</span><span class="sxs-lookup"><span data-stu-id="68c43-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68c43-104">範例</span><span class="sxs-lookup"><span data-stu-id="68c43-104">Example</span></span>  
 <span data-ttu-id="68c43-105">下列的主控台應用程式會建立 <xref:System.Data.DataTable> 執行個體 (Instance)。</span><span class="sxs-lookup"><span data-stu-id="68c43-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="68c43-106">然後，此範例會將<xref:System.Data.DataTable>填滿的加入至<xref:System.Data.DataTable.CreateDataReader%2A>呼叫方法的程式，以逐一查看包含在內<xref:System.Data.DataTableReader>的結果。</span><span class="sxs-lookup"><span data-stu-id="68c43-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="68c43-107">此範例會在主控台視窗中顯示以下輸出：</span><span class="sxs-lookup"><span data-stu-id="68c43-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="68c43-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68c43-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="68c43-109">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="68c43-109">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="68c43-110">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="68c43-110">ADO.NET Overview</span></span>](../ado-net-overview.md)
