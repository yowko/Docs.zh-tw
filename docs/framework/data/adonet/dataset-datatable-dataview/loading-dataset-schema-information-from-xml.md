---
title: 從 XML 載入資料集結構描述資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 4eb211ed13b5f2fe066cd7570c97ae324b187b34
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203504"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="21083-102">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="21083-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="21083-103">的架構<xref:System.Data.DataSet> (其資料表、資料行、關聯和條件約束) 可以透過程式設計方式定義、由的**Fill**或**FillSchema**方法<xref:System.Data.Common.DataAdapter>建立, 或是從 XML 檔載入。</span><span class="sxs-lookup"><span data-stu-id="21083-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="21083-104">若要從 XML 檔載入**資料集**架構資訊, 您可以使用**資料集**的**ReadXmlSchema**或**InferXmlSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="21083-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="21083-105">**ReadXmlSchema**可讓您從包含 xml 架構定義語言 (XSD) 架構的檔, 或具有內嵌 xml 架構的 xml 檔, 載入或推斷**資料集**架構資訊。</span><span class="sxs-lookup"><span data-stu-id="21083-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="21083-106">**InferXmlSchema**可讓您從 XML 檔推斷架構, 同時忽略您指定的特定 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="21083-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21083-107">當您使用 Web 服務或 XML 序列化來傳送使用 XSD 結構 (例如, 嵌套關聯) 在記憶體中建立的**資料集**時, 可能不會保留**資料集**內的資料表順序。</span><span class="sxs-lookup"><span data-stu-id="21083-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="21083-108">因此, 在此情況下,**資料集**的收件者不應該相依于資料表排序。</span><span class="sxs-lookup"><span data-stu-id="21083-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="21083-109">不過, 如果要傳送之**資料集**的架構是從 XSD 檔案讀取, 而不是在記憶體中建立, 則一律會保留資料表順序。</span><span class="sxs-lookup"><span data-stu-id="21083-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="21083-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="21083-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="21083-111">若要從 XML 檔載入**資料集**的架構, 而不載入任何資料, 您可以使用**DataSet**的**ReadXmlSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="21083-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="21083-112">**ReadXmlSchema**會使用 XML 架構定義語言 (XSD) 架構來建立定義的**資料集**架構。</span><span class="sxs-lookup"><span data-stu-id="21083-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="21083-113">**ReadXmlSchema**方法會接受檔案名、資料流程或包含要載入之 XML 檔的**XmlReader**的單一引數。</span><span class="sxs-lookup"><span data-stu-id="21083-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="21083-114">XML 文件只能包含結構描述或是內嵌於包含資料的 XML 項目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="21083-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="21083-115">如需將內嵌架構撰寫為 XML 架構的詳細資訊, 請參閱[從 XML 架構 (XSD) 衍生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)。</span><span class="sxs-lookup"><span data-stu-id="21083-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="21083-116">如果傳遞至**ReadXmlSchema**的 XML 檔不包含內嵌架構資訊, 則**READXMLSCHEMA**會從 XML 檔中的元素推斷架構。</span><span class="sxs-lookup"><span data-stu-id="21083-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="21083-117">如果**資料集**已經包含架構, 則會藉由加入新的資料表 (如果尚未存在) 來擴充目前的架構。</span><span class="sxs-lookup"><span data-stu-id="21083-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="21083-118">新的資料行將不會加入現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="21083-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="21083-119">如果加入的資料行已經存在於 DataSet 中, 但其類型與在 XML 中找到的**資料**行不相容, 則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="21083-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="21083-120">如需**ReadXmlSchema**如何從 xml 檔推斷架構的詳細資訊, 請參閱[從 Xml 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="21083-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="21083-121">雖然**ReadXmlSchema**只會載入或推斷**資料集**的架構, 但**資料集**的**ReadXml**方法會載入或推斷 XML 檔中所包含的架構和資料。</span><span class="sxs-lookup"><span data-stu-id="21083-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="21083-122">如需詳細資訊, 請參閱[從 XML 載入資料集](loading-a-dataset-from-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="21083-122">For more information, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="21083-123">下列程式碼範例示範如何從 XML 檔或資料流程載入**DataSet**架構。</span><span class="sxs-lookup"><span data-stu-id="21083-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="21083-124">第一個範例顯示將 XML 架構檔案名傳遞至**ReadXmlSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="21083-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="21083-125">第二個範例會顯示**StreamReader**。</span><span class="sxs-lookup"><span data-stu-id="21083-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
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
  
## <a name="inferxmlschema"></a><span data-ttu-id="21083-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="21083-126">InferXmlSchema</span></span>  
 <span data-ttu-id="21083-127">您也可以使用**資料集**的**InferXmlSchema**方法, 指示**資料集**從 XML 檔推斷其架構。</span><span class="sxs-lookup"><span data-stu-id="21083-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="21083-128">**InferXmlSchema**的運作方式與使用**XmlReadMode** **InferSchema** (載入資料和推斷架構) 的**ReadXml**相同, 如果所讀取的檔未包含任何內嵌架構, 則**ReadXmlSchema** 。</span><span class="sxs-lookup"><span data-stu-id="21083-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="21083-129">不過, **InferXmlSchema**提供了額外的功能, 可讓您指定在推斷架構時要忽略的特定 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="21083-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="21083-130">**InferXmlSchema**會採用兩個必要的引數: XML 檔的位置 (由檔案名、資料流程或**XmlReader**指定)。以及要由作業忽略之 XML 命名空間的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="21083-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="21083-131">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="21083-131">For example, consider the following XML:</span></span>  
  
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
  
 <span data-ttu-id="21083-132">因為先前 XML 檔中的專案指定了屬性, 所以**ReadXmlSchema**方法和**ReadXml**方法 ( **XmlReadMode**為**InferSchema** ) 會針對中的每個元素建立資料表記錄**分類**、類別目錄、類別**名稱**、**描述**、**產品**、 **ProductID**、 **ReorderLevel**和已**停止**。</span><span class="sxs-lookup"><span data-stu-id="21083-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="21083-133">(如需詳細資訊, 請參閱[從 XML 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md))。不過, 更適當的結構是只建立 category 和**Products**資料表, 然後在 category 資料表中建立 [類別目錄]、[**類別名稱**] 和 [**描述**] 資料行, 以及 **Products**資料表中的 ProductID、 **ReorderLevel**和已**停止**資料行。</span><span class="sxs-lookup"><span data-stu-id="21083-133">(For more information, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="21083-134">為確保推斷的架構忽略 XML 元素中指定的屬性, 請使用**InferXmlSchema**方法, 並指定要忽略之**officedata**的 XML 命名空間, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="21083-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="21083-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21083-135">See also</span></span>

- [<span data-ttu-id="21083-136">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="21083-136">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="21083-137">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="21083-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="21083-138">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="21083-138">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="21083-139">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="21083-139">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="21083-140">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="21083-140">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="21083-141">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="21083-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
