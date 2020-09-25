---
title: 建立 DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 3af6ae3a8f4ecc3ec34c186ce55c1c77c27514a9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202327"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="35da1-102">建立 DataReader</span><span class="sxs-lookup"><span data-stu-id="35da1-102">Creating a DataReader</span></span>

<span data-ttu-id="35da1-103"><xref:System.Data.DataTable> 和 <xref:System.Data.DataSet> 類別 (Class) 具有 <xref:System.Data.DataTable.CreateDataReader%2A> 方法，可以用一或多個唯讀的順向結果集來傳回 <xref:System.Data.DataTable> 的內容或 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataSet.Tables%2A> 集合內容。</span><span class="sxs-lookup"><span data-stu-id="35da1-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35da1-104">範例</span><span class="sxs-lookup"><span data-stu-id="35da1-104">Example</span></span>  

 <span data-ttu-id="35da1-105">下列的主控台應用程式會建立 <xref:System.Data.DataTable> 執行個體 (Instance)。</span><span class="sxs-lookup"><span data-stu-id="35da1-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="35da1-106">然後，此範例會將填入的 <xref:System.Data.DataTable> 程式傳遞至呼叫 <xref:System.Data.DataTable.CreateDataReader%2A> 方法的程式，此方法會逐一查看中包含的結果 <xref:System.Data.DataTableReader> 。</span><span class="sxs-lookup"><span data-stu-id="35da1-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="35da1-107">此範例會在主控台視窗中顯示以下輸出：</span><span class="sxs-lookup"><span data-stu-id="35da1-107">The example displays the following output in the console window:</span></span>  
  
```output  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="35da1-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35da1-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="35da1-109">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="35da1-109">DataTableReaders</span></span>](datatablereaders.md)
- <span data-ttu-id="35da1-110">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="35da1-110">[ADO.NET Overview](../ado-net-overview.md)</span></span>
