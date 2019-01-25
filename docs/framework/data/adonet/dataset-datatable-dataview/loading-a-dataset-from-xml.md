---
title: 從 XML 載入資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 7fb00046eb9ab92ed2514cd7615c41ea40124de9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594911"
---
# <a name="loading-a-dataset-from-xml"></a>從 XML 載入資料集
可以從 XML 資料流或文件建立 ADO.NET <xref:System.Data.DataSet> 的內容。 此外，使用 .NET Framework 可讓您在決定從 XML 載入何種資訊，以及如何建立 <xref:System.Data.DataSet> 的結構描述或關聯式結構時，擁有相當大的彈性。  
  
 若要填滿<xref:System.Data.DataSet>從 XML 資料，使用**ReadXml**方法<xref:System.Data.DataSet>物件。 **ReadXml**方法會讀取檔案時，資料流，或有**XmlReader**，並會當作引數的 XML 加上選擇性來源**XmlReadMode**引數。 (如需詳細資訊**XmlReader**，請參閱[NIB:讀取 XML 資料使用 XmlTextReader](https://msdn.microsoft.com/library/762c069b-b50c-41b8-936e-39eacfb0d540)。)**ReadXml**方法讀取 XML 資料流或文件，以載入內容<xref:System.Data.DataSet>資料。 它也會建立的關聯式結構描述<xref:System.Data.DataSet>取決於**XmlReadMode**指定且是否關聯式結構描述已經存在。  
  
 下表描述的選項**XmlReadMode**引數。  
  
|選項|描述|  
|------------|-----------------|  
|**Auto**|這是預設值。 檢查 XML 並依下列順序選擇最適當的選項：<br /><br /> -如果 XML 為 DiffGram， **DiffGram**用。<br />-如果<xref:System.Data.DataSet>包含結構描述或 XML 包含內嵌結構描述**ReadSchema**用。<br />-如果<xref:System.Data.DataSet>不包含結構描述，且 XML 不包含內嵌結構描述**InferSchema**用。<br /><br /> 如果您知道要讀取的 XML 格式，為了達到最佳效能建議您設定的明確**XmlReadMode**，而不是接受**自動**預設值。|  
|**ReadSchema**|讀取任何內嵌結構描述，並載入資料和結構描述。<br /><br /> 如果 <xref:System.Data.DataSet> 已經包含結構描述，則會將新資料表從內嵌結構描述加入 <xref:System.Data.DataSet> 的現有結構描述中。 如果內嵌結構描述中的任何資料表已經存在於 <xref:System.Data.DataSet> 中，則會擲回例外狀況。 您不能修改現有的資料表使用的結構描述**XmlReadMode.ReadSchema**。<br /><br /> 如果 <xref:System.Data.DataSet> 不包含結構描述，且沒有內嵌結構描述，則不會讀取任何資料。<br /><br /> 內嵌結構描述可使用 XML 結構描述定義語言 (XSD) 的結構描述來定義。 如需有關撰寫為 XML 結構描述的內嵌結構描述的詳細資訊，請參閱 <<c0> [ 衍生資料集關聯式結構從 XML 結構描述 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)。|  
|**IgnoreSchema**|忽略任何內嵌結構描述，並將資料載入現有的 <xref:System.Data.DataSet> 結構描述中。 任何與現有結構描述不相符的資料會被捨棄。 如果 <xref:System.Data.DataSet> 中沒有結構描述，則不會載入任何資料。<br /><br /> 如果資料是 DiffGram， **IgnoreSchema**有相同的功能**DiffGram** *。*|  
|**InferSchema**|忽略任何內嵌結構描述，並推斷每個 XML 資料結構的結構描述，然後載入資料。<br /><br /> 如果 <xref:System.Data.DataSet> 已經包含結構描述，則會將資料行加入現有的資料表來擴充目前的結構描述。 如果沒有現有的資料表，則不會加入額外的資料表。 如果推斷資料表已經存在但使用不同的命名空間，或者任何推斷的資料行與現有資料行衝突，便會擲回例外狀況。<br /><br /> 如需詳細資訊，瞭解**ReadXmlSchema**推斷結構描述從 XML 文件，請參閱[推斷資料集關聯式結構從 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。|  
|**DiffGram**|讀取 DiffGram 並將資料加入目前的結構描述。 **DiffGram**合併現有的資料列的唯一識別碼值相符之處的新資料列。 請參閱這個主題結尾處＜從 XML 合併資料＞。 如需有關 Diffgram 的詳細資訊，請參閱[DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)。|  
|**片段**|繼續讀取多個 XML 片段，直到到達資料流末。 與 <xref:System.Data.DataSet> 結構描述相符的片段會附加至適當的資料表。 與 <xref:System.Data.DataSet> 結構描述不相符的片段則會捨棄。|  
  
> [!NOTE]
>  如果您傳遞**XmlReader**要**ReadXml**定位的一部分的 XML 文件的方式**ReadXml**將讀取的下一個項目節點，並將它視為根項目，項目節點的結尾。 這不會套用如果您指定**XmlReadMode.Fragment**。  
  
## <a name="dtd-entities"></a>DTD 實體  
 如果您嘗試載入，如果您的 XML 包含文件類型定義 (DTD) 結構描述中定義的實體，則擲回例外狀況<xref:System.Data.DataSet>藉由傳遞的檔案名稱、 資料流，或未驗證**XmlReader**到**ReadXml**。 相反地，您必須建立**XmlValidatingReader**，以**EntityHandling**設定為**EntityHandling.ExpandEntities**，並傳遞您**XmlValidatingReader**要**ReadXml**。 **XmlValidatingReader**將會擴充之前讀取實體<xref:System.Data.DataSet>。  
  
 下列程式碼範例顯示如何從 XML 資料流載入 <xref:System.Data.DataSet>。 第一個範例顯示檔案名稱被傳遞給**ReadXml**方法。 第二個範例顯示內含使用 <xref:System.IO.StringReader> 所載入之 XML 的字串。  
  
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
>  如果您呼叫**ReadXml**載入非常大的檔案，您可能會遇到效能變慢。 若要確保最佳效能**ReadXml**，在大型檔案上呼叫<xref:System.Data.DataTable.BeginLoadData%2A>方法中每個資料表<xref:System.Data.DataSet>，然後呼叫**ReadXml**。 最後再針對 <xref:System.Data.DataTable.EndLoadData%2A> 的每個資料表呼叫 <xref:System.Data.DataSet> (如下列範例所示)。  
  
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
>  如果的 XSD 結構描述您<xref:System.Data.DataSet>包含**targetNamespace**，可能不會讀取資料，並呼叫時，您可能會遇到例外狀況**ReadXml**載入<xref:System.Data.DataSet>包含的 xml非限定命名空間的項目。 若要在此情況下讀取不合格的項目，設定**elementFormDefault**等於"qualified"中的 XSD 結構描述。 例如:   
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>從 XML 合併資料  
 如果 <xref:System.Data.DataSet> 已經包含資料，則會將 XML 的新資料加入 <xref:System.Data.DataSet> 中已出現的資料中。 **ReadXml**不會合併從 XML 載入<xref:System.Data.DataSet>任何資料列以相符的主索引鍵的資訊。 若要覆寫現有的資料列資訊，以從 XML 的新資訊，請使用**ReadXml**來建立新的<xref:System.Data.DataSet>，然後<xref:System.Data.DataSet.Merge%2A>新<xref:System.Data.DataSet>至現有<xref:System.Data.DataSet>。 請注意，載入 DiffGram using **ReadXML**具有**XmlReadMode**的**DiffGram**會合併具有相同的唯一識別項的資料列。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)
- [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
