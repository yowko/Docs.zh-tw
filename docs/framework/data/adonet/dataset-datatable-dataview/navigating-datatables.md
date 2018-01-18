---
title: "導覽 DataTable"
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
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2233beeab5bc613966375f9a8ccf18c333e9f4c6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="navigating-datatables"></a><span data-ttu-id="0ae66-102">導覽 DataTable</span><span class="sxs-lookup"><span data-stu-id="0ae66-102">Navigating DataTables</span></span>
<span data-ttu-id="0ae66-103"><xref:System.Data.DataTableReader> 會以一或多個唯讀、順向結果集的形式，取得一或多個 <xref:System.Data.DataTable> 物件的內容。</span><span class="sxs-lookup"><span data-stu-id="0ae66-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="0ae66-104">如果 <xref:System.Data.DataTableReader> 是使用 <xref:System.Data.DataSet.CreateDataReader%2A> 方法而建立，則可能包含多個結果集。</span><span class="sxs-lookup"><span data-stu-id="0ae66-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="0ae66-105">有多個結果集時，<xref:System.Data.DataTableReader.NextResult%2A> 方法會將游標移到下一個結果集。</span><span class="sxs-lookup"><span data-stu-id="0ae66-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="0ae66-106">這是順向的處理序。</span><span class="sxs-lookup"><span data-stu-id="0ae66-106">This is a forward-only process.</span></span> <span data-ttu-id="0ae66-107">且不可能返回前一個結果集。</span><span class="sxs-lookup"><span data-stu-id="0ae66-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ae66-108">範例</span><span class="sxs-lookup"><span data-stu-id="0ae66-108">Example</span></span>  
 <span data-ttu-id="0ae66-109">在下列範例中，`TestConstructor`方法會建立兩個<xref:System.Data.DataTable>執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ae66-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="0ae66-110">為了示範這個建構函式<xref:System.Data.DataTableReader>類別，此範例會建立新**DataTableReader**基礎陣列，其中包含兩個**Datatable**，並執行簡單的作業，第一個的幾個資料行的內容列印至主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="0ae66-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0ae66-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ae66-111">See Also</span></span>  
 [<span data-ttu-id="0ae66-112">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="0ae66-112">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [<span data-ttu-id="0ae66-113">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="0ae66-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
