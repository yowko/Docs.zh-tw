---
title: "建立 DataTable"
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
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 923d19e9539c6d93f3714efcdaa6fe7a5da843ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-datatable"></a><span data-ttu-id="5e095-102">建立 DataTable</span><span class="sxs-lookup"><span data-stu-id="5e095-102">Creating a DataTable</span></span>
<span data-ttu-id="5e095-103"><xref:System.Data.DataTable> 表示記憶體中關聯式資料的某個資料表，它可以單獨建立及使用，也可以由其他 .NET Framework 物件所使用，而它最常見用法是做為 <xref:System.Data.DataSet> 的成員。</span><span class="sxs-lookup"><span data-stu-id="5e095-103">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="5e095-104">您可以建立**DataTable**物件使用適當的**DataTable**建構函式。</span><span class="sxs-lookup"><span data-stu-id="5e095-104">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="5e095-105">您可以將它加入至**資料集**使用**新增**方法將它加入至**DataTable**物件的**資料表**集合。</span><span class="sxs-lookup"><span data-stu-id="5e095-105">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="5e095-106">您也可以建立**DataTable**物件內**資料集**使用**填滿**或**FillSchema**方法**DataAdapter**物件，或從預先定義或推斷 XML 結構描述使用**ReadXml**， **ReadXmlSchema**，或**InferXmlSchema**方法的**資料集**。</span><span class="sxs-lookup"><span data-stu-id="5e095-106">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="5e095-107">請注意，當您加入**DataTable**成員的身分**資料表**的其中一個集合**資料集**，您無法加入資料表的任何其他集合**資料集**。</span><span class="sxs-lookup"><span data-stu-id="5e095-107">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="5e095-108">當您第一次建立**DataTable**，它並沒有結構描述 （亦即結構）。</span><span class="sxs-lookup"><span data-stu-id="5e095-108">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="5e095-109">若要定義資料表的結構描述，您必須建立並新增<xref:System.Data.DataColumn>物件加入至**資料行**資料表的集合。</span><span class="sxs-lookup"><span data-stu-id="5e095-109">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="5e095-110">您也可以定義資料表的主索引鍵資料行和建立及新增**條件約束**物件加入至**條件約束**資料表的集合。</span><span class="sxs-lookup"><span data-stu-id="5e095-110">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="5e095-111">您定義的結構描述之後**DataTable**，您可以加入資料列的資料表加入**DataRow**物件加入至**列**資料表的集合。</span><span class="sxs-lookup"><span data-stu-id="5e095-111">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="5e095-112">您不需要提供的值<xref:System.Data.DataTable.TableName%2A>屬性，當您建立**DataTable**; 您可以在其他時候，指定的屬性，或您可以將它保留空白。</span><span class="sxs-lookup"><span data-stu-id="5e095-112">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="5e095-113">不過，當您加入的資料表沒有**TableName**值設定為**資料集**，資料表會指定資料表的累加預設名稱*N*，從"Table"開始 （table0)。</span><span class="sxs-lookup"><span data-stu-id="5e095-113">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e095-114">我們建議您避免 「 資料表*N*"命名慣例，當您提供**TableName**值，因為您提供的名稱可能與現有的預設資料表名稱中衝突**資料集**.</span><span class="sxs-lookup"><span data-stu-id="5e095-114">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="5e095-115">如果提供的名稱已經存在，便會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5e095-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="5e095-116">下列範例會建立的執行個體**DataTable**物件，並將其指派的名稱 「 客戶 」。</span><span class="sxs-lookup"><span data-stu-id="5e095-116">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="5e095-117">下列範例會建立的執行個體**DataTable**將它加入至**資料表**集合**資料集**。</span><span class="sxs-lookup"><span data-stu-id="5e095-117">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e095-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e095-118">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [<span data-ttu-id="5e095-119">DataTable</span><span class="sxs-lookup"><span data-stu-id="5e095-119">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="5e095-120">從 DataAdapter 填入 DataSet</span><span class="sxs-lookup"><span data-stu-id="5e095-120">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="5e095-121">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="5e095-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="5e095-122">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="5e095-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="5e095-123">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="5e095-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
