---
title: 將資料行加入至 DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 892c0488588e9a5b59650f4a815ba9819493a610
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538261"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="f87b3-102">將資料行加入至 DataTable</span><span class="sxs-lookup"><span data-stu-id="f87b3-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="f87b3-103">A<xref:System.Data.DataTable>包含的集合<xref:System.Data.DataColumn>所參考的物件**資料行**資料表屬性。</span><span class="sxs-lookup"><span data-stu-id="f87b3-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="f87b3-104">這個資料行集合 (可搭配任何條件約束) 可定義資料表的結構描述 (或結構)。</span><span class="sxs-lookup"><span data-stu-id="f87b3-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="f87b3-105">您建立**DataColumn**使用資料表中的物件**DataColumn**建構函式，或藉由呼叫**新增**方法**資料行**資料表，也就是屬性<xref:System.Data.DataColumnCollection>。</span><span class="sxs-lookup"><span data-stu-id="f87b3-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="f87b3-106">**新增**方法會接受選擇性**ColumnName**， **DataType**，並**運算式**引數，並建立新**DataColumn**為集合的成員。</span><span class="sxs-lookup"><span data-stu-id="f87b3-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="f87b3-107">它也會接受現有**DataColumn**物件，並將它加入至集合中，並傳回的參考加入**DataColumn**如果要求。</span><span class="sxs-lookup"><span data-stu-id="f87b3-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="f87b3-108">因為**DataTable**物件並非特定用於任何資料來源、 指定的資料類型時，會使用.NET Framework 型別**DataColumn**。</span><span class="sxs-lookup"><span data-stu-id="f87b3-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="f87b3-109">下列範例會將四個資料行**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="f87b3-109">The following example adds four columns to a **DataTable**.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 <span data-ttu-id="f87b3-110">在範例中，請注意，屬性**CustID**資料行設定為不允許**DBNull**值並限制為唯一的值。</span><span class="sxs-lookup"><span data-stu-id="f87b3-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="f87b3-111">不過，如果您定義**CustID**資料行做為資料表的主索引鍵資料行**AllowDBNull**屬性會自動設為**false**和**Unique**屬性會自動設為 **，則為 true**。</span><span class="sxs-lookup"><span data-stu-id="f87b3-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="f87b3-112">如需詳細資訊，請參閱 <<c0> [ 定義主索引鍵](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="f87b3-112">For more information, see [Defining Primary Keys](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f87b3-113">如果資料行名稱未提供資料行中，指定資料行的資料行的遞增預設名稱*N* "Column1"從開始，當它加入**DataColumnCollection**。</span><span class="sxs-lookup"><span data-stu-id="f87b3-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="f87b3-114">我們建議您避免命名慣例 」 資料行*N*「 當您提供的資料行名稱，因為您提供的名稱可能會與在現有的預設資料行名稱衝突**DataColumnCollection**。</span><span class="sxs-lookup"><span data-stu-id="f87b3-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="f87b3-115">如果提供的名稱已經存在，便會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f87b3-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="f87b3-116">如果您要使用 <xref:System.Xml.Linq.XElement> 當做 <xref:System.Data.DataColumn.DataType%2A> 中 <xref:System.Data.DataColumn> 的 <xref:System.Data.DataTable>，當您讀入資料時，XML 序列化將無法運作。</span><span class="sxs-lookup"><span data-stu-id="f87b3-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="f87b3-117">例如，如果您使用 <xref:System.Xml.XmlDocument> 方法來寫出 `DataTable.WriteXml`，在序列化至 XML 時，<xref:System.Xml.Linq.XElement> 就會存在額外的父節點。</span><span class="sxs-lookup"><span data-stu-id="f87b3-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="f87b3-118">若要解決此問題，請使用 <xref:System.Data.SqlTypes.SqlXml> 型別而非 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="f87b3-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="f87b3-119">`ReadXml` 和 `WriteXml` 會搭配 <xref:System.Data.SqlTypes.SqlXml> 正確運作。</span><span class="sxs-lookup"><span data-stu-id="f87b3-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f87b3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f87b3-120">See also</span></span>
- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="f87b3-121">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="f87b3-121">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="f87b3-122">DataTable</span><span class="sxs-lookup"><span data-stu-id="f87b3-122">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="f87b3-123">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="f87b3-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
