---
title: 將資料集內容當做 XML 資料寫入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: 9a63e79b2fce137ba9d21db861850a471cb42b9f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833960"
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="87edb-102">將資料集內容當做 XML 資料寫入</span><span class="sxs-lookup"><span data-stu-id="87edb-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="87edb-103">在 ADO.NET 中，您可以寫入使用 XML 形式的 <xref:System.Data.DataSet>，具有或不具有其結構描述皆可。</span><span class="sxs-lookup"><span data-stu-id="87edb-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="87edb-104">如果結構描述資訊是以 XML 內嵌的，它就會以 XML 結構描述定義語言 (XSD) 寫入。</span><span class="sxs-lookup"><span data-stu-id="87edb-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="87edb-105">結構描述包含 <xref:System.Data.DataSet> 的資料表定義，以及關聯性和條件約束定義。</span><span class="sxs-lookup"><span data-stu-id="87edb-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="87edb-106">將 <xref:System.Data.DataSet> 寫為 XML 資料時，<xref:System.Data.DataSet> 中的資料列會以其目前版本寫入。</span><span class="sxs-lookup"><span data-stu-id="87edb-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="87edb-107">不過，<xref:System.Data.DataSet> 也可寫入為 DiffGram，如此便能夠包含資料列的目前和原始值。</span><span class="sxs-lookup"><span data-stu-id="87edb-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="87edb-108">@No__t-0 的 XML 標記法可以寫入檔案、資料流程、 **XmlWriter**或字串中。</span><span class="sxs-lookup"><span data-stu-id="87edb-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="87edb-109">這些選擇在您要傳輸 XML 形式的 <xref:System.Data.DataSet> 時，可提供相當大的彈性。</span><span class="sxs-lookup"><span data-stu-id="87edb-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="87edb-110">若要以字串形式取得 <xref:System.Data.DataSet> 的 XML 標記法，請使用**GetXml**方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="87edb-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="87edb-111">**GetXml**會傳回不含架構資訊 <xref:System.Data.DataSet> 的 XML 標記法。</span><span class="sxs-lookup"><span data-stu-id="87edb-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="87edb-112">若要將 <xref:System.Data.DataSet> （XML 架構）的架構資訊寫入字串，請使用**GetXmlSchema**。</span><span class="sxs-lookup"><span data-stu-id="87edb-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="87edb-113">若要將 <xref:System.Data.DataSet> 寫入檔案、資料流程或**XmlWriter**，請使用**WriteXml**方法。</span><span class="sxs-lookup"><span data-stu-id="87edb-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="87edb-114">您傳遞至**WriteXml**的第一個參數是 XML 輸出的目的地。</span><span class="sxs-lookup"><span data-stu-id="87edb-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="87edb-115">例如，傳遞包含檔案名、system.servicemodel 物件等的字串，**依此類推。**</span><span class="sxs-lookup"><span data-stu-id="87edb-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="87edb-116">您可以傳遞**XmlWriteMode**的選擇性第二個參數，以指定寫入 XML 輸出的方式。</span><span class="sxs-lookup"><span data-stu-id="87edb-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="87edb-117">下表顯示**XmlWriteMode**的選項。</span><span class="sxs-lookup"><span data-stu-id="87edb-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="87edb-118">XmlWriteMode 選項</span><span class="sxs-lookup"><span data-stu-id="87edb-118">XmlWriteMode option</span></span>|<span data-ttu-id="87edb-119">描述</span><span class="sxs-lookup"><span data-stu-id="87edb-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="87edb-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="87edb-120">**IgnoreSchema**</span></span>|<span data-ttu-id="87edb-121">將 <xref:System.Data.DataSet> 目前的內容寫入為 XML 資料，其中不包含 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="87edb-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="87edb-122">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="87edb-122">This is the default.</span></span>|  
|<span data-ttu-id="87edb-123">**WriteSchema**</span><span class="sxs-lookup"><span data-stu-id="87edb-123">**WriteSchema**</span></span>|<span data-ttu-id="87edb-124">將 <xref:System.Data.DataSet> 目前的內容寫入為 XML 資料，它會將關聯式結構做為內嵌 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="87edb-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="87edb-125">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="87edb-125">**DiffGram**</span></span>|<span data-ttu-id="87edb-126">將整個 <xref:System.Data.DataSet> 寫入為 DiffGram (包括原始值和目前值)。</span><span class="sxs-lookup"><span data-stu-id="87edb-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="87edb-127">如需詳細資訊，請參閱[diffgram](diffgrams.md)。</span><span class="sxs-lookup"><span data-stu-id="87edb-127">For more information, see [DiffGrams](diffgrams.md).</span></span>|  
  
 <span data-ttu-id="87edb-128">撰寫包含**DataRelation**物件之 <xref:System.Data.DataSet> 的 XML 表示時，您很可能會想要產生的 xml 將每個關聯的子資料列都放在其相關的父項目內。</span><span class="sxs-lookup"><span data-stu-id="87edb-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="87edb-129">若要完成這項操作，請**將 datarelation 的** **Nested**屬性設為**true** ，並將**datarelation**新增至 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="87edb-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="87edb-130">如需詳細資訊，請參閱 <<c0>嵌套 datarelation。</span><span class="sxs-lookup"><span data-stu-id="87edb-130">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="87edb-131">以下是兩個範例，說明如何將 <xref:System.Data.DataSet> 的 XML 表示寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="87edb-131">The following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="87edb-132">第一個範例會將產生的 XML 檔案名當做字串傳遞給**WriteXml**。</span><span class="sxs-lookup"><span data-stu-id="87edb-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="87edb-133">第二個範例會傳遞**StreamWriter**物件。</span><span class="sxs-lookup"><span data-stu-id="87edb-133">The second example passes a **System.IO.StreamWriter** object.</span></span>
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="87edb-134">對應資料行至 XML 項目、屬性和文字</span><span class="sxs-lookup"><span data-stu-id="87edb-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="87edb-135">您可以使用**DataColumn**物件的**ColumnMapping**屬性，指定資料表中的資料行如何以 XML 表示。</span><span class="sxs-lookup"><span data-stu-id="87edb-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="87edb-136">下表顯示資料表資料行之**ColumnMapping**屬性的不同**MappingType**值，以及所產生的 XML。</span><span class="sxs-lookup"><span data-stu-id="87edb-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="87edb-137">MappingType 值</span><span class="sxs-lookup"><span data-stu-id="87edb-137">MappingType value</span></span>|<span data-ttu-id="87edb-138">描述</span><span class="sxs-lookup"><span data-stu-id="87edb-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="87edb-139">**目**</span><span class="sxs-lookup"><span data-stu-id="87edb-139">**Element**</span></span>|<span data-ttu-id="87edb-140">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="87edb-140">This is the default.</span></span> <span data-ttu-id="87edb-141">資料行會寫為 XML 項目，其中 ColumnName 為項目名稱，並且資料行內容會寫為項目文字。</span><span class="sxs-lookup"><span data-stu-id="87edb-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="87edb-142">例如:</span><span class="sxs-lookup"><span data-stu-id="87edb-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="87edb-143">**屬性**</span><span class="sxs-lookup"><span data-stu-id="87edb-143">**Attribute**</span></span>|<span data-ttu-id="87edb-144">資料行會寫為目前資料行 XML 項目的 XML 屬性，其中 ColumnName 是屬性名稱，且資料行內容會寫為屬性值。</span><span class="sxs-lookup"><span data-stu-id="87edb-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="87edb-145">例如:</span><span class="sxs-lookup"><span data-stu-id="87edb-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="87edb-146">**SimpleContent**</span><span class="sxs-lookup"><span data-stu-id="87edb-146">**SimpleContent**</span></span>|<span data-ttu-id="87edb-147">資料行內容會寫為目前資料行 XML 項目中的文字。</span><span class="sxs-lookup"><span data-stu-id="87edb-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="87edb-148">例如:</span><span class="sxs-lookup"><span data-stu-id="87edb-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="87edb-149">請注意，如果資料表的資料行具有**元素**資料行或嵌套關聯，則無法設定**SimpleContent** 。</span><span class="sxs-lookup"><span data-stu-id="87edb-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="87edb-150">**隱含**</span><span class="sxs-lookup"><span data-stu-id="87edb-150">**Hidden**</span></span>|<span data-ttu-id="87edb-151">XML 輸出中不會寫入資料行。</span><span class="sxs-lookup"><span data-stu-id="87edb-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87edb-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87edb-152">See also</span></span>

- [<span data-ttu-id="87edb-153">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="87edb-153">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="87edb-154">DiffGram</span><span class="sxs-lookup"><span data-stu-id="87edb-154">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="87edb-155">巢狀 DataRelation</span><span class="sxs-lookup"><span data-stu-id="87edb-155">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="87edb-156">將資料集結構描述資訊當作 XSD 寫入</span><span class="sxs-lookup"><span data-stu-id="87edb-156">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)
- [<span data-ttu-id="87edb-157">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="87edb-157">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="87edb-158">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="87edb-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
