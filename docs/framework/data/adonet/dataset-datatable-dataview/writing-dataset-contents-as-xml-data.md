---
title: 將資料集內容當做 XML 資料寫入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: bf73adff89ca5cad3a71239421ac826105a387cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785226"
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="932db-102">將資料集內容當做 XML 資料寫入</span><span class="sxs-lookup"><span data-stu-id="932db-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="932db-103">在 ADO.NET 中，您可以寫入使用 XML 形式的 <xref:System.Data.DataSet>，具有或不具有其結構描述皆可。</span><span class="sxs-lookup"><span data-stu-id="932db-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="932db-104">如果結構描述資訊是以 XML 內嵌的，它就會以 XML 結構描述定義語言 (XSD) 寫入。</span><span class="sxs-lookup"><span data-stu-id="932db-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="932db-105">結構描述包含 <xref:System.Data.DataSet> 的資料表定義，以及關聯性和條件約束定義。</span><span class="sxs-lookup"><span data-stu-id="932db-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="932db-106">將 <xref:System.Data.DataSet> 寫為 XML 資料時，<xref:System.Data.DataSet> 中的資料列會以其目前版本寫入。</span><span class="sxs-lookup"><span data-stu-id="932db-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="932db-107">不過，<xref:System.Data.DataSet> 也可寫入為 DiffGram，如此便能夠包含資料列的目前和原始值。</span><span class="sxs-lookup"><span data-stu-id="932db-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="932db-108">的 XML 標記法<xref:System.Data.DataSet>可以寫入檔案、資料流程、 **XmlWriter**或字串中。</span><span class="sxs-lookup"><span data-stu-id="932db-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="932db-109">這些選擇在您要傳輸 XML 形式的 <xref:System.Data.DataSet> 時，可提供相當大的彈性。</span><span class="sxs-lookup"><span data-stu-id="932db-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="932db-110">若要以字串形式取得的<xref:System.Data.DataSet> XML 表示，請使用**GetXml**方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="932db-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="932db-111">**GetXml** <xref:System.Data.DataSet>會傳回沒有架構資訊的 XML 標記法。</span><span class="sxs-lookup"><span data-stu-id="932db-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="932db-112">若要將架構資訊從<xref:System.Data.DataSet> （XML 架構）寫入字串，請使用**GetXmlSchema**。</span><span class="sxs-lookup"><span data-stu-id="932db-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="932db-113">若要將<xref:System.Data.DataSet>寫入檔案、資料流程或**XmlWriter**，請使用**WriteXml**方法。</span><span class="sxs-lookup"><span data-stu-id="932db-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="932db-114">您傳遞至**WriteXml**的第一個參數是 XML 輸出的目的地。</span><span class="sxs-lookup"><span data-stu-id="932db-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="932db-115">例如，傳遞包含檔案名、system.servicemodel 物件等的字串，**依此類推。**</span><span class="sxs-lookup"><span data-stu-id="932db-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="932db-116">您可以傳遞**XmlWriteMode**的選擇性第二個參數，以指定寫入 XML 輸出的方式。</span><span class="sxs-lookup"><span data-stu-id="932db-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="932db-117">下表顯示**XmlWriteMode**的選項。</span><span class="sxs-lookup"><span data-stu-id="932db-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="932db-118">XmlWriteMode 選項</span><span class="sxs-lookup"><span data-stu-id="932db-118">XmlWriteMode option</span></span>|<span data-ttu-id="932db-119">說明</span><span class="sxs-lookup"><span data-stu-id="932db-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="932db-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="932db-120">**IgnoreSchema**</span></span>|<span data-ttu-id="932db-121">將 <xref:System.Data.DataSet> 目前的內容寫入為 XML 資料，其中不包含 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="932db-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="932db-122">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="932db-122">This is the default.</span></span>|  
|<span data-ttu-id="932db-123">**WriteSchema**</span><span class="sxs-lookup"><span data-stu-id="932db-123">**WriteSchema**</span></span>|<span data-ttu-id="932db-124">將 <xref:System.Data.DataSet> 目前的內容寫入為 XML 資料，它會將關聯式結構做為內嵌 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="932db-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="932db-125">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="932db-125">**DiffGram**</span></span>|<span data-ttu-id="932db-126">將整個 <xref:System.Data.DataSet> 寫入為 DiffGram (包括原始值和目前值)。</span><span class="sxs-lookup"><span data-stu-id="932db-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="932db-127">如需詳細資訊，請參閱[diffgram](diffgrams.md)。</span><span class="sxs-lookup"><span data-stu-id="932db-127">For more information, see [DiffGrams](diffgrams.md).</span></span>|  
  
 <span data-ttu-id="932db-128">撰寫包含<xref:System.Data.DataSet> **DataRelation**物件之的 XML 表示時，您很可能會想要產生的 xml 將每個關聯的子資料列都放在其相關的父項目內。</span><span class="sxs-lookup"><span data-stu-id="932db-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="932db-129">若要完成<xref:System.Data.DataSet>這項操作，請在將**datarelation**加入至時，將**datarelation**的**Nested**屬性設定為**true** 。</span><span class="sxs-lookup"><span data-stu-id="932db-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="932db-130">如需詳細資訊，請參閱 <<c0>嵌套 datarelation。</span><span class="sxs-lookup"><span data-stu-id="932db-130">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="932db-131">下列兩個範例說明如何將 XML 形式的 <xref:System.Data.DataSet> 寫入檔案中。</span><span class="sxs-lookup"><span data-stu-id="932db-131">Following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="932db-132">第一個範例會將產生的 XML 檔案名當做字串傳遞給**WriteXml**。</span><span class="sxs-lookup"><span data-stu-id="932db-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="932db-133">第二個範例會傳遞**StreamWriter**物件。</span><span class="sxs-lookup"><span data-stu-id="932db-133">The second example passes a **System.IO.StreamWriter** object.</span></span>  
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="932db-134">對應資料行至 XML 項目、屬性和文字</span><span class="sxs-lookup"><span data-stu-id="932db-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="932db-135">您可以使用**DataColumn**物件的**ColumnMapping**屬性，指定資料表中的資料行如何以 XML 表示。</span><span class="sxs-lookup"><span data-stu-id="932db-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="932db-136">下表顯示資料表資料行之**ColumnMapping**屬性的不同**MappingType**值，以及所產生的 XML。</span><span class="sxs-lookup"><span data-stu-id="932db-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="932db-137">MappingType 值</span><span class="sxs-lookup"><span data-stu-id="932db-137">MappingType value</span></span>|<span data-ttu-id="932db-138">說明</span><span class="sxs-lookup"><span data-stu-id="932db-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="932db-139">**目**</span><span class="sxs-lookup"><span data-stu-id="932db-139">**Element**</span></span>|<span data-ttu-id="932db-140">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="932db-140">This is the default.</span></span> <span data-ttu-id="932db-141">資料行會寫為 XML 項目，其中 ColumnName 為項目名稱，並且資料行內容會寫為項目文字。</span><span class="sxs-lookup"><span data-stu-id="932db-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="932db-142">例如：</span><span class="sxs-lookup"><span data-stu-id="932db-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="932db-143">**屬性**</span><span class="sxs-lookup"><span data-stu-id="932db-143">**Attribute**</span></span>|<span data-ttu-id="932db-144">資料行會寫為目前資料行 XML 項目的 XML 屬性，其中 ColumnName 是屬性名稱，且資料行內容會寫為屬性值。</span><span class="sxs-lookup"><span data-stu-id="932db-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="932db-145">例如：</span><span class="sxs-lookup"><span data-stu-id="932db-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="932db-146">**SimpleContent**</span><span class="sxs-lookup"><span data-stu-id="932db-146">**SimpleContent**</span></span>|<span data-ttu-id="932db-147">資料行內容會寫為目前資料行 XML 項目中的文字。</span><span class="sxs-lookup"><span data-stu-id="932db-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="932db-148">例如：</span><span class="sxs-lookup"><span data-stu-id="932db-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="932db-149">請注意，如果資料表的資料行具有**元素**資料行或嵌套關聯，則無法設定**SimpleContent** 。</span><span class="sxs-lookup"><span data-stu-id="932db-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="932db-150">**隱含**</span><span class="sxs-lookup"><span data-stu-id="932db-150">**Hidden**</span></span>|<span data-ttu-id="932db-151">XML 輸出中不會寫入資料行。</span><span class="sxs-lookup"><span data-stu-id="932db-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="932db-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="932db-152">See also</span></span>

- [<span data-ttu-id="932db-153">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="932db-153">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="932db-154">DiffGram</span><span class="sxs-lookup"><span data-stu-id="932db-154">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="932db-155">巢狀 DataRelation</span><span class="sxs-lookup"><span data-stu-id="932db-155">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="932db-156">將資料集結構描述資訊當作 XSD 寫入</span><span class="sxs-lookup"><span data-stu-id="932db-156">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)
- [<span data-ttu-id="932db-157">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="932db-157">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="932db-158">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="932db-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
