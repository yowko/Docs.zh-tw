---
title: 建立自動遞增資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 5e4a36829107480a44980c7210b39c21231c67f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786449"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="2a93a-102">建立自動遞增資料行</span><span class="sxs-lookup"><span data-stu-id="2a93a-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="2a93a-103">若要確保資料行的值是唯一的，您可以在將新資料列加入至資料表時，將資料行值設為自動累加。</span><span class="sxs-lookup"><span data-stu-id="2a93a-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="2a93a-104">若要建立自動遞增<xref:System.Data.DataColumn>，請<xref:System.Data.DataColumn.AutoIncrement%2A>將資料行的屬性設定為**true**。</span><span class="sxs-lookup"><span data-stu-id="2a93a-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="2a93a-105">接著會以<xref:System.Data.DataColumn.AutoIncrementSeed%2A>屬性中定義的值為開頭，而且每個資料列加上**自動遞增**資料行的值，都會隨著資料行<xref:System.Data.DataColumn.AutoIncrementStep%2A>的屬性中所定義的值而增加。 <xref:System.Data.DataColumn></span><span class="sxs-lookup"><span data-stu-id="2a93a-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="2a93a-106">針對**自動遞增**資料行，我們建議<xref:System.Data.DataColumn.ReadOnly%2A>將**DataColumn**的屬性設定為**true**。</span><span class="sxs-lookup"><span data-stu-id="2a93a-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="2a93a-107">下列範例示範如何建立以 200 值做為開頭的資料行，並以增量 3 累加。</span><span class="sxs-lookup"><span data-stu-id="2a93a-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2a93a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a93a-108">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="2a93a-109">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="2a93a-109">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="2a93a-110">DataTable</span><span class="sxs-lookup"><span data-stu-id="2a93a-110">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="2a93a-111">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="2a93a-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
