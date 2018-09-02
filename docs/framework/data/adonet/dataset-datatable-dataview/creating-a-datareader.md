---
title: 建立 DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 1ede51ed9119051a647fd27d8d02cd2c93e61bbb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442716"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="b6eeb-102">建立 DataReader</span><span class="sxs-lookup"><span data-stu-id="b6eeb-102">Creating a DataReader</span></span>
<span data-ttu-id="b6eeb-103"><xref:System.Data.DataTable> 和 <xref:System.Data.DataSet> 類別 (Class) 具有 <xref:System.Data.DataTable.CreateDataReader%2A> 方法，可以用一或多個唯讀的順向結果集來傳回 <xref:System.Data.DataTable> 的內容或 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataSet.Tables%2A> 集合內容。</span><span class="sxs-lookup"><span data-stu-id="b6eeb-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6eeb-104">範例</span><span class="sxs-lookup"><span data-stu-id="b6eeb-104">Example</span></span>  
 <span data-ttu-id="b6eeb-105">下列的主控台應用程式會建立 <xref:System.Data.DataTable> 執行個體 (Instance)。</span><span class="sxs-lookup"><span data-stu-id="b6eeb-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="b6eeb-106">範例接著會傳遞將填滿<xref:System.Data.DataTable>要呼叫的程序<xref:System.Data.DataTable.CreateDataReader%2A>方法，這個方法會逐一查看包含在結果<xref:System.Data.DataTableReader>。</span><span class="sxs-lookup"><span data-stu-id="b6eeb-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="b6eeb-107">此範例會在主控台視窗中顯示以下輸出：</span><span class="sxs-lookup"><span data-stu-id="b6eeb-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6eeb-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6eeb-108">See Also</span></span>  
 <xref:System.Data.DataTable.CreateDataReader%2A>  
 <xref:System.Data.DataSet.CreateDataReader%2A>  
 [<span data-ttu-id="b6eeb-109">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="b6eeb-109">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [<span data-ttu-id="b6eeb-110">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b6eeb-110">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
