---
title: 建立自動遞增資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 5972d9e3d84a236104e85e17d8df1e9ee7f56122
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="a6746-102">建立自動遞增資料行</span><span class="sxs-lookup"><span data-stu-id="a6746-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="a6746-103">若要確保資料行的值是唯一的，您可以在將新資料列加入至資料表時，將資料行值設為自動累加。</span><span class="sxs-lookup"><span data-stu-id="a6746-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="a6746-104">若要建立自動遞增<xref:System.Data.DataColumn>，將<xref:System.Data.DataColumn.AutoIncrement%2A>屬性的資料行**true**。</span><span class="sxs-lookup"><span data-stu-id="a6746-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="a6746-105"><xref:System.Data.DataColumn>開頭中定義的值，然後<xref:System.Data.DataColumn.AutoIncrementSeed%2A>屬性，並加上每個資料列的值**AutoIncrement**資料行中定義的值會增加<xref:System.Data.DataColumn.AutoIncrementStep%2A>資料行屬性。</span><span class="sxs-lookup"><span data-stu-id="a6746-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="a6746-106">如**AutoIncrement**資料行，我們建議最好讓<xref:System.Data.DataColumn.ReadOnly%2A>屬性**DataColumn**設為**true**。</span><span class="sxs-lookup"><span data-stu-id="a6746-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="a6746-107">下列範例示範如何建立以 200 值做為開頭的資料行，並以增量 3 累加。</span><span class="sxs-lookup"><span data-stu-id="a6746-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6746-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6746-108">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 [<span data-ttu-id="a6746-109">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="a6746-109">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="a6746-110">DataTable</span><span class="sxs-lookup"><span data-stu-id="a6746-110">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="a6746-111">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="a6746-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
