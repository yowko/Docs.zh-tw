---
title: 定義主索引鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 159b23eb4ef5ca38ebce6e488080d315ec3be081
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151178"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="a05d1-102">定義主索引鍵</span><span class="sxs-lookup"><span data-stu-id="a05d1-102">Defining Primary Keys</span></span>
<span data-ttu-id="a05d1-103">資料庫資料表通常會有資料行或資料行群組，可唯一識別資料表的每個資料列。</span><span class="sxs-lookup"><span data-stu-id="a05d1-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="a05d1-104">這個識別欄位或資料行群組又稱為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a05d1-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="a05d1-105">當您將單個<xref:System.Data.DataColumn><xref:System.Data.DataTable.PrimaryKey%2A>標識為 的 時<xref:System.Data.DataTable>，表會自動將列的屬性<xref:System.Data.DataColumn.AllowDBNull%2A>設置為**false，** 將<xref:System.Data.DataColumn.Unique%2A>屬性設置為**true**。</span><span class="sxs-lookup"><span data-stu-id="a05d1-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="a05d1-106">對於多列主鍵，只有**AllowDBNull**屬性將自動設置為**false**。</span><span class="sxs-lookup"><span data-stu-id="a05d1-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="a05d1-107">的主**鍵**屬性<xref:System.Data.DataTable>接收一個或多個**DataColumn**物件的陣列作為其值，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="a05d1-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="a05d1-108">第一個範例定義單一資料行為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a05d1-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="a05d1-109">下列範例定義兩個資料行作為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a05d1-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a05d1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a05d1-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="a05d1-111">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="a05d1-111">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="a05d1-112">DataTable</span><span class="sxs-lookup"><span data-stu-id="a05d1-112">DataTables</span></span>](datatables.md)
- <span data-ttu-id="a05d1-113">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="a05d1-113">[ADO.NET Overview](../ado-net-overview.md)</span></span>
