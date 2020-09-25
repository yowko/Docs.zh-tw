---
title: 建立 DataTable
description: 瞭解如何在 ADO.NET 中建立 DataTable，以代表記憶體中關聯式資料的一個資料表，以獨立或其他 .NET Framework 物件使用。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: 75c9bcf0e0b6180030825b4d1e7dd9e1f9686712
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198635"
---
# <a name="creating-a-datatable"></a><span data-ttu-id="24db9-103">建立 DataTable</span><span class="sxs-lookup"><span data-stu-id="24db9-103">Creating a DataTable</span></span>

<span data-ttu-id="24db9-104"><xref:System.Data.DataTable> 表示記憶體中關聯式資料的某個資料表，它可以單獨建立及使用，也可以由其他 .NET Framework 物件所使用，而它最常見用法是做為 <xref:System.Data.DataSet> 的成員。</span><span class="sxs-lookup"><span data-stu-id="24db9-104">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="24db9-105">您可以使用適當的**datatable**函式來建立**datatable**物件。</span><span class="sxs-lookup"><span data-stu-id="24db9-105">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="24db9-106">您可以使用**add**方法，將它加入至**DataTable**物件的**Tables**集合，以將它加入至**資料集**。</span><span class="sxs-lookup"><span data-stu-id="24db9-106">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="24db9-107">您也可以使用**DataAdapter**物件的**Fill**或**FillSchema**方法，或使用**資料集**的**ReadXml**、 **READXMLSCHEMA**或**InferXmlSchema**方法，從預先定義或推斷的 XML 架構建立**資料集**內的**DataTable**物件。</span><span class="sxs-lookup"><span data-stu-id="24db9-107">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="24db9-108">請注意，在您將**DataTable**加入為一個**資料集**之**tables**集合的成員之後，就無法將它加入至任何其他**資料集**的資料表集合。</span><span class="sxs-lookup"><span data-stu-id="24db9-108">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="24db9-109">當您第一次建立 **DataTable**時，它沒有架構 (也就是結構) 。</span><span class="sxs-lookup"><span data-stu-id="24db9-109">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="24db9-110">若要定義資料表的架構，您必須建立物件，並將 <xref:System.Data.DataColumn> 物件加入至資料表的資料 **行** 集合。</span><span class="sxs-lookup"><span data-stu-id="24db9-110">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="24db9-111">您也可以定義資料表的主鍵資料行，並建立 **條件約束** 物件，並將其加入至資料表的 **條件約束** 集合。</span><span class="sxs-lookup"><span data-stu-id="24db9-111">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="24db9-112">定義 **DataTable**的架構之後，您可以將 **DataRow** 物件加入至資料表的 **rows** 集合，藉以將資料列加入至資料表。</span><span class="sxs-lookup"><span data-stu-id="24db9-112">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="24db9-113"><xref:System.Data.DataTable.TableName%2A>當您建立**DataTable**時，不需要提供屬性的值; 您可以在另一次指定屬性，也可以將它保留空白。</span><span class="sxs-lookup"><span data-stu-id="24db9-113">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="24db9-114">但是，當您將沒有 **TableName** 值的資料表加入至 **資料集**時，資料表將會獲得資料表*N*的累加預設名稱，開頭為 "table" 表示 Table0。</span><span class="sxs-lookup"><span data-stu-id="24db9-114">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24db9-115">當您提供**TableName**值時，建議您避免使用「資料表*N*」命名慣例，因為您所提供的名稱可能會與**資料集中**現有的預設資料表名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="24db9-115">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="24db9-116">如果提供的名稱已經存在，便會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="24db9-116">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="24db9-117">下列範例會建立 **DataTable** 物件的實例，並為其指派「客戶」名稱。</span><span class="sxs-lookup"><span data-stu-id="24db9-117">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="24db9-118">下列範例會建立**DataTable**的實例，方法是將它加入至**資料集**的**資料表**集合。</span><span class="sxs-lookup"><span data-stu-id="24db9-118">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="24db9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24db9-119">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [<span data-ttu-id="24db9-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="24db9-120">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="24db9-121">從 DataAdapter 填入資料集</span><span class="sxs-lookup"><span data-stu-id="24db9-121">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="24db9-122">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="24db9-122">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="24db9-123">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="24db9-123">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- <span data-ttu-id="24db9-124">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="24db9-124">[ADO.NET Overview](../ado-net-overview.md)</span></span>
