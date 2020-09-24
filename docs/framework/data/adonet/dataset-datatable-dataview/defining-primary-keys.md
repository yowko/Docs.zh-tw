---
title: 定義主索引鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 94b033d58061e3d2e48a352d782eec7c4202fa43
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166829"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="fb5a0-102">定義主索引鍵</span><span class="sxs-lookup"><span data-stu-id="fb5a0-102">Defining Primary Keys</span></span>

<span data-ttu-id="fb5a0-103">資料庫資料表通常會有資料行或資料行群組，可唯一識別資料表的每個資料列。</span><span class="sxs-lookup"><span data-stu-id="fb5a0-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="fb5a0-104">這個識別欄位或資料行群組又稱為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="fb5a0-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="fb5a0-105">當您將單一識別 <xref:System.Data.DataColumn> 為的時 <xref:System.Data.DataTable.PrimaryKey%2A> <xref:System.Data.DataTable> ，資料表會自動將資料行的屬性設 <xref:System.Data.DataColumn.AllowDBNull%2A> 為 **false** ，並將 <xref:System.Data.DataColumn.Unique%2A> 屬性設定為 **true**。</span><span class="sxs-lookup"><span data-stu-id="fb5a0-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="fb5a0-106">若為多重資料行主鍵，則只有 **AllowDBNull** 屬性會自動設為 **false**。</span><span class="sxs-lookup"><span data-stu-id="fb5a0-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="fb5a0-107">的 **PrimaryKey** 屬性（property <xref:System.Data.DataTable> ）會以一個或多個 **DataColumn** 物件的陣列值形式接收，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fb5a0-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="fb5a0-108">第一個範例定義單一資料行為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="fb5a0-108">The first example defines a single column as the primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 <span data-ttu-id="fb5a0-109">下列範例定義兩個資料行作為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="fb5a0-109">The following example defines two columns as a primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb5a0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb5a0-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="fb5a0-111">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="fb5a0-111">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="fb5a0-112">DataTables</span><span class="sxs-lookup"><span data-stu-id="fb5a0-112">DataTables</span></span>](datatables.md)
- <span data-ttu-id="fb5a0-113">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="fb5a0-113">[ADO.NET Overview](../ado-net-overview.md)</span></span>
