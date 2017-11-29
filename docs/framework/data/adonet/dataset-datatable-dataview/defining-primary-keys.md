---
title: "定義主索引鍵"
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
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a2ba353353b52e5a866887e7f0dc4b743e336bd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="defining-primary-keys"></a><span data-ttu-id="c0ffd-102">定義主索引鍵</span><span class="sxs-lookup"><span data-stu-id="c0ffd-102">Defining Primary Keys</span></span>
<span data-ttu-id="c0ffd-103">資料庫資料表通常會有資料行或資料行群組，可唯一識別資料表的每個資料列。</span><span class="sxs-lookup"><span data-stu-id="c0ffd-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="c0ffd-104">這個識別欄位或資料行群組又稱為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c0ffd-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="c0ffd-105">當您識別單一<xref:System.Data.DataColumn>為<xref:System.Data.DataTable.PrimaryKey%2A>的<xref:System.Data.DataTable>，資料表會自動設定<xref:System.Data.DataColumn.AllowDBNull%2A>屬性的資料行**false**和<xref:System.Data.DataColumn.Unique%2A>屬性**true**。</span><span class="sxs-lookup"><span data-stu-id="c0ffd-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="c0ffd-106">多重資料行主索引鍵，只能**AllowDBNull**屬性會自動設定為**false**。</span><span class="sxs-lookup"><span data-stu-id="c0ffd-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="c0ffd-107">**PrimaryKey**屬性<xref:System.Data.DataTable>接收其值為一或多個陣列**DataColumn**物件，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c0ffd-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="c0ffd-108">第一個範例定義單一資料行為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c0ffd-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="c0ffd-109">下列範例定義兩個資料行作為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c0ffd-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0ffd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0ffd-110">See Also</span></span>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="c0ffd-111">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="c0ffd-111">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="c0ffd-112">DataTable</span><span class="sxs-lookup"><span data-stu-id="c0ffd-112">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="c0ffd-113">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="c0ffd-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
