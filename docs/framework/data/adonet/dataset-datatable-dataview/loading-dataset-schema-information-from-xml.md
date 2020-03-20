---
title: 從 XML 載入資料集結構描述資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 69994c546fea842ffef1c8c43d6d6f5bc35e0629
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151048"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="0703d-102">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="0703d-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="0703d-103">的<xref:System.Data.DataSet>架構（其表、列、關係和約束）可以以程式設計方式定義、由<xref:System.Data.Common.DataAdapter>的**填充**或**填充架構**方法創建，也可以從 XML 文檔載入。</span><span class="sxs-lookup"><span data-stu-id="0703d-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="0703d-104">要從 XML 文檔載入**DataSet**架構資訊，可以使用**DataSet**的**ReadXmlSchema**或**InferXmlSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="0703d-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="0703d-105">**ReadXmlSchema**允許您從包含 XML 架構定義語言 （XSD） 架構的文檔或具有內聯 XML 架構的 XML 文檔載入或推斷**DataSet**架構資訊。</span><span class="sxs-lookup"><span data-stu-id="0703d-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="0703d-106">**InferXmlSchema**允許您從 XML 文檔中推斷架構，而忽略您指定的某些 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="0703d-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0703d-107">當您使用 Web 服務或 XML 序列化傳輸使用 XSD 構造（如嵌套關係）在記憶體中創建的**DataSet**時 **，DataSet**中的表排序可能無法保留。</span><span class="sxs-lookup"><span data-stu-id="0703d-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="0703d-108">因此，在這種情況下 **，DataSet**的收件者不應依賴于表排序。</span><span class="sxs-lookup"><span data-stu-id="0703d-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="0703d-109">但是，如果從 XSD 檔讀取要傳輸的**DataSet**的架構，而不是在記憶體中創建，則始終保留表排序。</span><span class="sxs-lookup"><span data-stu-id="0703d-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="0703d-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="0703d-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="0703d-111">要從 XML 文檔載入**DataSet**的架構而不載入任何資料，可以使用**DataSet**的**ReadXmlSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="0703d-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="0703d-112">**ReadXmlSchema**創建使用 XML 架構定義語言 （XSD） 架構定義的**資料集**架構。</span><span class="sxs-lookup"><span data-stu-id="0703d-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="0703d-113">**ReadXmlSchema**方法採用檔案名、流或**XmlReader**的單個參數，其中包含要載入的 XML 文檔。</span><span class="sxs-lookup"><span data-stu-id="0703d-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="0703d-114">XML 文件只能包含結構描述或是內嵌於包含資料的 XML 項目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0703d-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="0703d-115">有關將內聯架構編寫為 XML 架構的詳細資訊，請參閱[從 XML 架構 （XSD） 派生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)。</span><span class="sxs-lookup"><span data-stu-id="0703d-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="0703d-116">如果傳遞給**ReadXmlSchema 的**XML 文檔不包含內聯架構資訊，**則 ReadXmlSchema**將從 XML 文檔中的元素推斷架構。</span><span class="sxs-lookup"><span data-stu-id="0703d-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="0703d-117">如果**DataSet**已包含架構，則如果新表不存在，則通過添加新表來擴展當前架構。</span><span class="sxs-lookup"><span data-stu-id="0703d-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="0703d-118">新的資料行將不會加入現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="0703d-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="0703d-119">如果正在添加的列在**DataSet**中已存在，但與 XML 中找到的列的類型不相容，則引發異常。</span><span class="sxs-lookup"><span data-stu-id="0703d-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="0703d-120">有關**ReadXmlSchema**如何從 XML 文檔中推斷架構的詳細資訊，請參閱[從 XML 推斷 DataSet 關聯式結構](inferring-dataset-relational-structure-from-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="0703d-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="0703d-121">儘管**ReadXmlSchema**僅載入或推斷**DataSet**的架構，但**DataSet**的**ReadXml**方法載入或推斷架構和 XML 文檔中的資料。</span><span class="sxs-lookup"><span data-stu-id="0703d-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="0703d-122">有關詳細資訊，請參閱從[XML 載入資料集](loading-a-dataset-from-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="0703d-122">For more information, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="0703d-123">以下代碼示例演示如何從 XML 文檔或流載入**DataSet**架構。</span><span class="sxs-lookup"><span data-stu-id="0703d-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="0703d-124">第一個示例顯示將 XML 架構檔案名傳遞給**ReadXmlSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="0703d-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="0703d-125">第二個示例顯示了**System.IO.StreamReader**。</span><span class="sxs-lookup"><span data-stu-id="0703d-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
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
  
## <a name="inferxmlschema"></a><span data-ttu-id="0703d-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="0703d-126">InferXmlSchema</span></span>  
 <span data-ttu-id="0703d-127">您還可以指示**DataSet**使用**DataSet**的**InferXmlSchema**方法從 XML 文檔中推斷其架構。</span><span class="sxs-lookup"><span data-stu-id="0703d-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="0703d-128">**InferXml 架構**的功能與使用**推斷模式\*\*\*\*的 XmlReadMode**的**ReadXml（** 載入資料以及推斷架構）的功能相同，如果正在讀取的文檔不包含內聯架構，則**ReadXmlSchema**的功能相同。</span><span class="sxs-lookup"><span data-stu-id="0703d-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="0703d-129">但是 **，InferXmlSchema**提供了一種附加功能，允許您指定在推斷架構時要忽略的特定 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="0703d-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="0703d-130">**inferXmlSchema**採用兩個必需的參數：XML 文檔的位置，由檔案名、流或**XmlReader**指定;以及要由操作忽略的 XML 命名空間的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="0703d-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="0703d-131">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="0703d-131">For example, consider the following XML:</span></span>  
  
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
  
 <span data-ttu-id="0703d-132">由於為前面的XML文檔中的元素指定的屬性 **，ReadXmlSchema**方法和具有**InferSchema** Xml 的**ReadXml** **XmlReadMode**方法都將為文檔中的每個元素創建表：**類別**、**類別 ID、\*\*\*\*類別名稱**、**描述**、**產品**、產品**ID、\*\*\*\*重新排序級別**和**已停產**。</span><span class="sxs-lookup"><span data-stu-id="0703d-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="0703d-133">（有關詳細資訊，請參閱從[XML 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)。但是，更合適的結構是只創建 **"類別**和**產品**"表，然後在 **"類別"** 表中創建**類別 ID、\*\*\*\*類別名稱**和**說明**列，並在 **"產品**"表中創建 **"產品識別碼"、"\*\*\*\*重新排序級別\*\*\*\*"和"停產**"列。</span><span class="sxs-lookup"><span data-stu-id="0703d-133">(For more information, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="0703d-134">為確保推斷的架構忽略 XML 元素中指定的屬性，請使用**InferXmlSchema**方法並指定要忽略**的 Officedata 的**XML 命名空間，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="0703d-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="0703d-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0703d-135">See also</span></span>

- [<span data-ttu-id="0703d-136">在資料集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="0703d-136">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="0703d-137">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="0703d-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="0703d-138">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="0703d-138">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="0703d-139">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="0703d-139">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="0703d-140">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="0703d-140">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="0703d-141">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="0703d-141">[ADO.NET Overview](../ado-net-overview.md)</span></span>
