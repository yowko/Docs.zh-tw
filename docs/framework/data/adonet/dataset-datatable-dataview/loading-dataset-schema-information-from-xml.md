---
title: "從 XML 載入資料集結構描述資訊"
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
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e41eb1168774a5ebfc17147f65901de0e432789f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="feba9-102">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="feba9-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="feba9-103">結構描述的<xref:System.Data.DataSet>（其資料表、 資料行、 關聯和條件約束） 可以定義以程式設計的方式，建立由**填滿**或**FillSchema**方法<xref:System.Data.Common.DataAdapter>，或從載入XML 文件。</span><span class="sxs-lookup"><span data-stu-id="feba9-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="feba9-104">若要載入**資料集**結構描述資訊從 XML 文件，您可以使用**ReadXmlSchema**或**InferXmlSchema**方法**資料集**.</span><span class="sxs-lookup"><span data-stu-id="feba9-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="feba9-105">**ReadXmlSchema**可讓您載入或推斷**資料集**從包含 XML 結構描述定義語言 (XSD) 結構描述或內嵌 XML 結構描述的 XML 文件的文件結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="feba9-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="feba9-106">**InferXmlSchema**可讓您從 XML 文件結構描述推斷同時忽略您指定特定 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="feba9-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="feba9-107">資料表中的順序**資料集**可能不會保留當您使用 Web 服務或 XML 序列化傳輸**資料集**中建立記憶體中使用 XSD 建構 （例如巢狀關聯）。</span><span class="sxs-lookup"><span data-stu-id="feba9-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="feba9-108">因此，收件者的**資料集**不應依賴在此情況下排序資料表。</span><span class="sxs-lookup"><span data-stu-id="feba9-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="feba9-109">不過，資料表排序一定會保留如果結構描述的**資料集**傳輸已讀取從 XSD 檔案，而不建立的記憶體中。</span><span class="sxs-lookup"><span data-stu-id="feba9-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="feba9-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="feba9-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="feba9-111">若要載入的結構描述**資料集**從 XML 文件不載入任何資料，您可以使用**ReadXmlSchema**方法**資料集**。</span><span class="sxs-lookup"><span data-stu-id="feba9-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="feba9-112">**ReadXmlSchema**建立**資料集**定義使用 XML 結構描述定義語言 (XSD) 結構描述的結構描述。</span><span class="sxs-lookup"><span data-stu-id="feba9-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="feba9-113">**ReadXmlSchema**方法接受單一引數的檔案名稱、 資料流，或**XmlReader**包含要載入之 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="feba9-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="feba9-114">XML 文件只能包含結構描述或是內嵌於包含資料的 XML 項目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="feba9-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="feba9-115">如需有關撰寫為 XML 結構描述的內嵌結構描述的詳細資訊，請參閱[衍生資料集關聯式結構從 XML 結構描述 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)。</span><span class="sxs-lookup"><span data-stu-id="feba9-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="feba9-116">如果 XML 文件傳遞至**ReadXmlSchema**不包含內嵌結構描述資訊， **ReadXmlSchema**會推斷的結構描述的 XML 文件中的項目。</span><span class="sxs-lookup"><span data-stu-id="feba9-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="feba9-117">如果**資料集**已經包含結構描述、 目前的結構描述會擴充以新增新的資料表，如果它們尚不存在。</span><span class="sxs-lookup"><span data-stu-id="feba9-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="feba9-118">新的資料行將不會加入現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="feba9-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="feba9-119">如果已加入的資料行存在於**資料集**但不相容的類型與資料行發現在 XML 中，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="feba9-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="feba9-120">如需詳細資訊，關於如何**ReadXmlSchema**推斷結構描述從 XML 文件，請參閱[推斷資料集關聯式結構與 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="feba9-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="feba9-121">雖然**ReadXmlSchema**載入或推斷的結構描述**資料集**、 **ReadXml**方法**資料集**載入或推斷兩者結構描述和 XML 文件中所包含的資料。</span><span class="sxs-lookup"><span data-stu-id="feba9-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="feba9-122">如需詳細資訊，請參閱[從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="feba9-122">For more information, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="feba9-123">下列程式碼範例顯示如何載入**資料集**從 XML 文件或資料流的結構描述。</span><span class="sxs-lookup"><span data-stu-id="feba9-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="feba9-124">第一個範例顯示 XML 結構描述檔案名稱被傳遞給**ReadXmlSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="feba9-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="feba9-125">第二個範例顯示**System.IO.StreamReader**。</span><span class="sxs-lookup"><span data-stu-id="feba9-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a><span data-ttu-id="feba9-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="feba9-126">InferXmlSchema</span></span>  
 <span data-ttu-id="feba9-127">您也可以指示**資料集**推斷其結構描述從 XML 文件使用**InferXmlSchema**方法**資料集**。</span><span class="sxs-lookup"><span data-stu-id="feba9-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="feba9-128">**InferXmlSchema**函式相同，兩者皆為**ReadXml**與**XmlReadMode**的**InferSchema** （載入資料，以及推斷結構描述），和**ReadXmlSchema**如果正在讀取的文件包含內嵌結構描述。</span><span class="sxs-lookup"><span data-stu-id="feba9-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="feba9-129">不過， **InferXmlSchema**提供可讓您指定特定的 XML 命名空間推斷的結構描述時，會忽略其他的功能。</span><span class="sxs-lookup"><span data-stu-id="feba9-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="feba9-130">**InferXmlSchema**兩個必要引數： 由檔案名稱、 資料流中，指定的 XML 文件的位置或**XmlReader**; 以及作業所忽略的 XML 命名空間的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="feba9-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="feba9-131">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="feba9-131">For example, consider the following XML:</span></span>  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>   
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>   
  <Description od:adotype="203">Soft drinks and teas</Description>   
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>   
  <ReorderLevel od:adotype="3">10</ReorderLevel>   
  <Discontinued od:adotype="11">0</Discontinued>   
</Products>  
</NewDataSet>  
```  
  
 <span data-ttu-id="feba9-132">由於上述 XML 文件中的項目所指定的屬性同時**ReadXmlSchema**方法和**ReadXml**方法**XmlReadMode**的**InferSchema**會在文件中建立資料表的每個項目：**類別**， **CategoryID**， **CategoryName**，**描述**，**產品**， **ProductID**， **ReorderLevel**，和**停止**.</span><span class="sxs-lookup"><span data-stu-id="feba9-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="feba9-133">(如需詳細資訊，請參閱[推斷資料集關聯式結構與 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。)不過，若要建立僅可更適當的結構**類別**和**產品**資料表，然後再建立**CategoryID**，**類別名稱**，和**描述**中的資料行**類別**資料表，和**ProductID**， **ReorderLevel**，和**Discontinued**中的資料行**產品**資料表。</span><span class="sxs-lookup"><span data-stu-id="feba9-133">(For more information, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="feba9-134">若要確保推斷的結構描述會忽略 XML 項目中指定的屬性，請使用**InferXmlSchema**方法和指定的 XML 命名空間**officedata**被忽略，如下所示下列範例。</span><span class="sxs-lookup"><span data-stu-id="feba9-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="feba9-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="feba9-135">See Also</span></span>  
 [<span data-ttu-id="feba9-136">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="feba9-136">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="feba9-137">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="feba9-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="feba9-138">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="feba9-138">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="feba9-139">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="feba9-139">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="feba9-140">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="feba9-140">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="feba9-141">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="feba9-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
