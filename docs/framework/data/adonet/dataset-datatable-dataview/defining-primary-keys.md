---
title: 定義主索引鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 84c84cb8fc0ee484b09c69c72571a19c335b58f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230625"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="929bb-102">定義主索引鍵</span><span class="sxs-lookup"><span data-stu-id="929bb-102">Defining Primary Keys</span></span>
<span data-ttu-id="929bb-103">資料庫資料表通常會有資料行或資料行群組，可唯一識別資料表的每個資料列。</span><span class="sxs-lookup"><span data-stu-id="929bb-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="929bb-104">這個識別欄位或資料行群組又稱為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="929bb-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="929bb-105">當您找出單一<xref:System.Data.DataColumn>做為<xref:System.Data.DataTable.PrimaryKey%2A>如<xref:System.Data.DataTable>，資料表會自動設定<xref:System.Data.DataColumn.AllowDBNull%2A>的資料行的屬性**false**和<xref:System.Data.DataColumn.Unique%2A>屬性設**true**。</span><span class="sxs-lookup"><span data-stu-id="929bb-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="929bb-106">針對多個資料行主要金鑰時，只有**AllowDBNull**屬性會自動設為**false**。</span><span class="sxs-lookup"><span data-stu-id="929bb-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="929bb-107">**PrimaryKey**屬性<xref:System.Data.DataTable>做為其值會接收一或多個陣列**DataColumn**物件，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="929bb-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="929bb-108">第一個範例定義單一資料行為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="929bb-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="929bb-109">下列範例定義兩個資料行作為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="929bb-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="929bb-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="929bb-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="929bb-111">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="929bb-111">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="929bb-112">DataTables</span><span class="sxs-lookup"><span data-stu-id="929bb-112">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="929bb-113">ADO.NET Managed 提供者和DataSet開發人員中心</span><span class="sxs-lookup"><span data-stu-id="929bb-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
