---
title: "建立 DataReader"
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
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 169f290ba41e7efe1ceb7c57f0821fdc0a886c5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-datareader"></a><span data-ttu-id="63b12-102">建立 DataReader</span><span class="sxs-lookup"><span data-stu-id="63b12-102">Creating a DataReader</span></span>
<span data-ttu-id="63b12-103"><xref:System.Data.DataTable> 和 <xref:System.Data.DataSet> 類別 (Class) 具有 <xref:System.Data.DataTable.CreateDataReader%2A> 方法，可以用一或多個唯讀的順向結果集來傳回 <xref:System.Data.DataTable> 的內容或 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataSet.Tables%2A> 集合內容。</span><span class="sxs-lookup"><span data-stu-id="63b12-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63b12-104">範例</span><span class="sxs-lookup"><span data-stu-id="63b12-104">Example</span></span>  
 <span data-ttu-id="63b12-105">下列的主控台應用程式會建立 <xref:System.Data.DataTable> 執行個體 (Instance)。</span><span class="sxs-lookup"><span data-stu-id="63b12-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="63b12-106">此範例接著會將傳遞填<xref:System.Data.DataTable>要呼叫的程序<xref:System.Data.DataTable.CreateDataReader%2A>方法，這個方法會逐一查看包含在結果<xref:System.Data.DataTableReader>。</span><span class="sxs-lookup"><span data-stu-id="63b12-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="63b12-107">此範例會在主控台視窗中顯示以下輸出：</span><span class="sxs-lookup"><span data-stu-id="63b12-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="63b12-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="63b12-108">See Also</span></span>  
 <xref:System.Data.DataTable.CreateDataReader%2A>  
 <xref:System.Data.DataSet.CreateDataReader%2A>  
 [<span data-ttu-id="63b12-109">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="63b12-109">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [<span data-ttu-id="63b12-110">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="63b12-110">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
