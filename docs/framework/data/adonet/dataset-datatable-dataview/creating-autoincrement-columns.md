---
title: 建立自動遞增資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 99c52b93cee858511d50aba2f30f2b9f96d91ccd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090936"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="1d1de-102">建立自動遞增資料行</span><span class="sxs-lookup"><span data-stu-id="1d1de-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="1d1de-103">若要確保資料行的值是唯一的，您可以在將新資料列加入至資料表時，將資料行值設為自動累加。</span><span class="sxs-lookup"><span data-stu-id="1d1de-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="1d1de-104">若要建立自動遞增<xref:System.Data.DataColumn>，將<xref:System.Data.DataColumn.AutoIncrement%2A>屬性的資料行 **，則為 true**。</span><span class="sxs-lookup"><span data-stu-id="1d1de-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="1d1de-105"><xref:System.Data.DataColumn>開頭中定義的值，然後<xref:System.Data.DataColumn.AutoIncrementSeed%2A>屬性，加入每個資料列的值**AutoIncrement**資料行中定義的值會增加<xref:System.Data.DataColumn.AutoIncrementStep%2A>資料行屬性。</span><span class="sxs-lookup"><span data-stu-id="1d1de-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="1d1de-106">針對**AutoIncrement**資料行，我們建議<xref:System.Data.DataColumn.ReadOnly%2A>屬性**DataColumn**設為**true**。</span><span class="sxs-lookup"><span data-stu-id="1d1de-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="1d1de-107">下列範例示範如何建立以 200 值做為開頭的資料行，並以增量 3 累加。</span><span class="sxs-lookup"><span data-stu-id="1d1de-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d1de-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d1de-108">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="1d1de-109">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="1d1de-109">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="1d1de-110">DataTable</span><span class="sxs-lookup"><span data-stu-id="1d1de-110">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="1d1de-111">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="1d1de-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
