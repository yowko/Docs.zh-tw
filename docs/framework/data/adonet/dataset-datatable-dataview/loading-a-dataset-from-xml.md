---
title: 從 XML 載入資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 3a781f17ac3cabebce17955b9a7e2edda4d4fd4b
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365883"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="63c73-102">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="63c73-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="63c73-103">可以從 XML 資料流或文件建立 ADO.NET <xref:System.Data.DataSet> 的內容。</span><span class="sxs-lookup"><span data-stu-id="63c73-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="63c73-104">此外，使用 .NET Framework 可讓您在決定從 XML 載入何種資訊，以及如何建立 <xref:System.Data.DataSet> 的結構描述或關聯式結構時，擁有相當大的彈性。</span><span class="sxs-lookup"><span data-stu-id="63c73-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="63c73-105">若要填滿<xref:System.Data.DataSet>從 XML 資料，使用**ReadXml**方法<xref:System.Data.DataSet>物件。</span><span class="sxs-lookup"><span data-stu-id="63c73-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="63c73-106">**ReadXml**方法會讀取檔案時，資料流，或有**XmlReader**，並會當作引數的 XML 加上選擇性來源**XmlReadMode**引數。</span><span class="sxs-lookup"><span data-stu-id="63c73-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="63c73-107">(如需詳細資訊**XmlReader**，請參閱[NIB： 使用 XmlTextReader 讀取 XML 資料](https://msdn.microsoft.com/library/762c069b-b50c-41b8-936e-39eacfb0d540)。)**ReadXml**方法讀取 XML 資料流或文件，以載入內容<xref:System.Data.DataSet>資料。</span><span class="sxs-lookup"><span data-stu-id="63c73-107">(For more information about the **XmlReader**, see [NIB: Reading XML Data with XmlTextReader](https://msdn.microsoft.com/library/762c069b-b50c-41b8-936e-39eacfb0d540).) The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="63c73-108">它也會建立的關聯式結構描述<xref:System.Data.DataSet>取決於**XmlReadMode**指定且是否關聯式結構描述已經存在。</span><span class="sxs-lookup"><span data-stu-id="63c73-108">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="63c73-109">下表描述的選項**XmlReadMode**引數。</span><span class="sxs-lookup"><span data-stu-id="63c73-109">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="63c73-110">選項</span><span class="sxs-lookup"><span data-stu-id="63c73-110">Option</span></span>|<span data-ttu-id="63c73-111">描述</span><span class="sxs-lookup"><span data-stu-id="63c73-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="63c73-112">**Auto**</span><span class="sxs-lookup"><span data-stu-id="63c73-112">**Auto**</span></span>|<span data-ttu-id="63c73-113">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="63c73-113">This is the default.</span></span> <span data-ttu-id="63c73-114">檢查 XML 並依下列順序選擇最適當的選項：</span><span class="sxs-lookup"><span data-stu-id="63c73-114">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="63c73-115">-如果 XML 為 DiffGram， **DiffGram**用。</span><span class="sxs-lookup"><span data-stu-id="63c73-115">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="63c73-116">-如果<xref:System.Data.DataSet>包含結構描述或 XML 包含內嵌結構描述**ReadSchema**用。</span><span class="sxs-lookup"><span data-stu-id="63c73-116">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="63c73-117">-如果<xref:System.Data.DataSet>不包含結構描述，且 XML 不包含內嵌結構描述**InferSchema**用。</span><span class="sxs-lookup"><span data-stu-id="63c73-117">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="63c73-118">如果您知道要讀取的 XML 格式，為了達到最佳效能建議您設定的明確**XmlReadMode**，而不是接受**自動**預設值。</span><span class="sxs-lookup"><span data-stu-id="63c73-118">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="63c73-119">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="63c73-119">**ReadSchema**</span></span>|<span data-ttu-id="63c73-120">讀取任何內嵌結構描述，並載入資料和結構描述。</span><span class="sxs-lookup"><span data-stu-id="63c73-120">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="63c73-121">如果 <xref:System.Data.DataSet> 已經包含結構描述，則會將新資料表從內嵌結構描述加入 <xref:System.Data.DataSet> 的現有結構描述中。</span><span class="sxs-lookup"><span data-stu-id="63c73-121">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="63c73-122">如果內嵌結構描述中的任何資料表已經存在於 <xref:System.Data.DataSet> 中，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="63c73-122">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="63c73-123">您不能修改現有的資料表使用的結構描述**XmlReadMode.ReadSchema**。</span><span class="sxs-lookup"><span data-stu-id="63c73-123">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="63c73-124">如果 <xref:System.Data.DataSet> 不包含結構描述，且沒有內嵌結構描述，則不會讀取任何資料。</span><span class="sxs-lookup"><span data-stu-id="63c73-124">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="63c73-125">內嵌結構描述可使用 XML 結構描述定義語言 (XSD) 的結構描述來定義。</span><span class="sxs-lookup"><span data-stu-id="63c73-125">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="63c73-126">如需有關撰寫為 XML 結構描述的內嵌結構描述的詳細資訊，請參閱 <<c0> [ 衍生資料集關聯式結構從 XML 結構描述 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)。</span><span class="sxs-lookup"><span data-stu-id="63c73-126">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="63c73-127">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="63c73-127">**IgnoreSchema**</span></span>|<span data-ttu-id="63c73-128">忽略任何內嵌結構描述，並將資料載入現有的 <xref:System.Data.DataSet> 結構描述中。</span><span class="sxs-lookup"><span data-stu-id="63c73-128">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="63c73-129">任何與現有結構描述不相符的資料會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="63c73-129">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="63c73-130">如果 <xref:System.Data.DataSet> 中沒有結構描述，則不會載入任何資料。</span><span class="sxs-lookup"><span data-stu-id="63c73-130">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="63c73-131">如果資料是 DiffGram， **IgnoreSchema**有相同的功能**DiffGram** *。*</span><span class="sxs-lookup"><span data-stu-id="63c73-131">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="63c73-132">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="63c73-132">**InferSchema**</span></span>|<span data-ttu-id="63c73-133">忽略任何內嵌結構描述，並推斷每個 XML 資料結構的結構描述，然後載入資料。</span><span class="sxs-lookup"><span data-stu-id="63c73-133">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="63c73-134">如果 <xref:System.Data.DataSet> 已經包含結構描述，則會將資料行加入現有的資料表來擴充目前的結構描述。</span><span class="sxs-lookup"><span data-stu-id="63c73-134">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="63c73-135">如果沒有現有的資料表，則不會加入額外的資料表。</span><span class="sxs-lookup"><span data-stu-id="63c73-135">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="63c73-136">如果推斷資料表已經存在但使用不同的命名空間，或者任何推斷的資料行與現有資料行衝突，便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="63c73-136">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="63c73-137">如需詳細資訊，瞭解**ReadXmlSchema**推斷結構描述從 XML 文件，請參閱[推斷資料集關聯式結構從 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="63c73-137">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="63c73-138">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="63c73-138">**DiffGram**</span></span>|<span data-ttu-id="63c73-139">讀取 DiffGram 並將資料加入目前的結構描述。</span><span class="sxs-lookup"><span data-stu-id="63c73-139">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="63c73-140">**DiffGram**合併現有的資料列的唯一識別碼值相符之處的新資料列。</span><span class="sxs-lookup"><span data-stu-id="63c73-140">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="63c73-141">請參閱這個主題結尾處＜從 XML 合併資料＞。</span><span class="sxs-lookup"><span data-stu-id="63c73-141">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="63c73-142">如需有關 Diffgram 的詳細資訊，請參閱[DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)。</span><span class="sxs-lookup"><span data-stu-id="63c73-142">For more information about DiffGrams, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>|  
|<span data-ttu-id="63c73-143">**片段**</span><span class="sxs-lookup"><span data-stu-id="63c73-143">**Fragment**</span></span>|<span data-ttu-id="63c73-144">繼續讀取多個 XML 片段，直到到達資料流末。</span><span class="sxs-lookup"><span data-stu-id="63c73-144">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="63c73-145">與 <xref:System.Data.DataSet> 結構描述相符的片段會附加至適當的資料表。</span><span class="sxs-lookup"><span data-stu-id="63c73-145">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="63c73-146">與 <xref:System.Data.DataSet> 結構描述不相符的片段則會捨棄。</span><span class="sxs-lookup"><span data-stu-id="63c73-146">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="63c73-147">如果您傳遞**XmlReader**要**ReadXml**定位的一部分的 XML 文件的方式**ReadXml**將讀取的下一個項目節點，並將它視為根項目，項目節點的結尾。</span><span class="sxs-lookup"><span data-stu-id="63c73-147">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="63c73-148">這不會套用如果您指定**XmlReadMode.Fragment**。</span><span class="sxs-lookup"><span data-stu-id="63c73-148">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="63c73-149">DTD 實體</span><span class="sxs-lookup"><span data-stu-id="63c73-149">DTD Entities</span></span>  
 <span data-ttu-id="63c73-150">如果您嘗試載入，如果您的 XML 包含文件類型定義 (DTD) 結構描述中定義的實體，則擲回例外狀況<xref:System.Data.DataSet>藉由傳遞的檔案名稱、 資料流，或未驗證**XmlReader**到**ReadXml**。</span><span class="sxs-lookup"><span data-stu-id="63c73-150">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="63c73-151">相反地，您必須建立**XmlValidatingReader**，以**EntityHandling**設定為**EntityHandling.ExpandEntities**，並傳遞您**XmlValidatingReader**要**ReadXml**。</span><span class="sxs-lookup"><span data-stu-id="63c73-151">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="63c73-152">**XmlValidatingReader**將會擴充之前讀取實體<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="63c73-152">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="63c73-153">下列程式碼範例顯示如何從 XML 資料流載入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="63c73-153">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="63c73-154">第一個範例顯示檔案名稱被傳遞給**ReadXml**方法。</span><span class="sxs-lookup"><span data-stu-id="63c73-154">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="63c73-155">第二個範例顯示內含使用 <xref:System.IO.StringReader> 所載入之 XML 的字串。</span><span class="sxs-lookup"><span data-stu-id="63c73-155">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
>  <span data-ttu-id="63c73-156">如果您呼叫**ReadXml**載入非常大的檔案，您可能會遇到效能變慢。</span><span class="sxs-lookup"><span data-stu-id="63c73-156">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="63c73-157">若要確保最佳效能**ReadXml**，在大型檔案上呼叫<xref:System.Data.DataTable.BeginLoadData%2A>方法中每個資料表<xref:System.Data.DataSet>，然後呼叫**ReadXml**。</span><span class="sxs-lookup"><span data-stu-id="63c73-157">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="63c73-158">最後再針對 <xref:System.Data.DataTable.EndLoadData%2A> 的每個資料表呼叫 <xref:System.Data.DataSet> (如下列範例所示)。</span><span class="sxs-lookup"><span data-stu-id="63c73-158">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");   
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
>  <span data-ttu-id="63c73-159">如果的 XSD 結構描述您<xref:System.Data.DataSet>包含**targetNamespace**，可能不會讀取資料，並呼叫時，您可能會遇到例外狀況**ReadXml**載入<xref:System.Data.DataSet>包含的 xml非限定命名空間的項目。</span><span class="sxs-lookup"><span data-stu-id="63c73-159">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="63c73-160">若要在此情況下讀取不合格的項目，設定**elementFormDefault**等於"qualified"中的 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="63c73-160">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="63c73-161">例如: </span><span class="sxs-lookup"><span data-stu-id="63c73-161">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="63c73-162">從 XML 合併資料</span><span class="sxs-lookup"><span data-stu-id="63c73-162">Merging Data from XML</span></span>  
 <span data-ttu-id="63c73-163">如果 <xref:System.Data.DataSet> 已經包含資料，則會將 XML 的新資料加入 <xref:System.Data.DataSet> 中已出現的資料中。</span><span class="sxs-lookup"><span data-stu-id="63c73-163">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="63c73-164">**ReadXml**不會合併從 XML 載入<xref:System.Data.DataSet>任何資料列以相符的主索引鍵的資訊。</span><span class="sxs-lookup"><span data-stu-id="63c73-164">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="63c73-165">若要覆寫現有的資料列資訊，以從 XML 的新資訊，請使用**ReadXml**來建立新的<xref:System.Data.DataSet>，然後<xref:System.Data.DataSet.Merge%2A>新<xref:System.Data.DataSet>至現有<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="63c73-165">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="63c73-166">請注意，載入 DiffGram using **ReadXML**具有**XmlReadMode**的**DiffGram**會合併具有相同的唯一識別項的資料列。</span><span class="sxs-lookup"><span data-stu-id="63c73-166">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c73-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63c73-167">See Also</span></span>  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="63c73-168">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="63c73-168">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="63c73-169">DiffGram</span><span class="sxs-lookup"><span data-stu-id="63c73-169">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [<span data-ttu-id="63c73-170">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="63c73-170">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="63c73-171">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="63c73-171">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="63c73-172">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="63c73-172">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="63c73-173">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="63c73-173">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="63c73-174">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="63c73-174">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
