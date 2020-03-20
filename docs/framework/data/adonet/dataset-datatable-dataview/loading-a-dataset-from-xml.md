---
title: 從 XML 載入資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: c21ed3bb31add285d64272040680433fff4e16fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151061"
---
# <a name="loading-a-dataset-from-xml"></a>從 XML 載入資料集
可以從 XML 資料流或文件建立 ADO.NET <xref:System.Data.DataSet> 的內容。 此外，使用 .NET Framework 可讓您在決定從 XML 載入何種資訊，以及如何建立 <xref:System.Data.DataSet> 的結構描述或關聯式結構時，擁有相當大的彈性。  
  
 要用<xref:System.Data.DataSet>XML 的資料填充 ， 請使用<xref:System.Data.DataSet>物件的**ReadXml**方法。 **ReadXml**方法從檔、流或**XmlReader**讀取，並將 XML 的源加上可選的**XmlReadMode**參數作為參數。 有關**XmlReader**的詳細資訊，請參閱[使用 XmlTextReader 讀取 XML 資料](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100))。 **ReadXml**方法讀取 XML 流或文檔的內容，並<xref:System.Data.DataSet>載入資料。 它還將根據指定的**XmlReadMode**以及關係<xref:System.Data.DataSet>架構是否存在創建 的關係架構。  
  
 下表描述了**XmlReadMode**參數的選項。  
  
|選項|描述|  
|------------|-----------------|  
|**Auto**|這是預設值。 檢查 XML 並依下列順序選擇最適當的選項：<br /><br /> - 如果 XML 是 DiffGram，則使用**DiffGram。**<br />- 如果<xref:System.Data.DataSet>包含架構或 XML 包含內聯架構，則使用**ReadSchema。**<br />- 如果<xref:System.Data.DataSet>不包含架構，並且 XML 不包含內聯架構，則使用**InferSchema。**<br /><br /> 如果您知道正在讀取的 XML 的格式，建議您設置顯式**XmlReadMode，** 而不是接受**自動**預設值。|  
|**ReadSchema**|讀取任何內嵌結構描述，並載入資料和結構描述。<br /><br /> 如果 <xref:System.Data.DataSet> 已經包含結構描述，則會將新資料表從內嵌結構描述加入 <xref:System.Data.DataSet> 的現有結構描述中。 如果內嵌結構描述中的任何資料表已經存在於 <xref:System.Data.DataSet> 中，則會擲回例外狀況。 您將無法使用**XmlReadMode.ReadSchema**修改現有表的架構。<br /><br /> 如果 <xref:System.Data.DataSet> 不包含結構描述，且沒有內嵌結構描述，則不會讀取任何資料。<br /><br /> 內嵌結構描述可使用 XML 結構描述定義語言 (XSD) 的結構描述來定義。 有關將內聯架構編寫為 XML 架構的詳細資訊，請參閱[從 XML 架構 （XSD） 派生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)。|  
|**IgnoreSchema**|忽略任何內嵌結構描述，並將資料載入現有的 <xref:System.Data.DataSet> 結構描述中。 任何與現有結構描述不相符的資料會被捨棄。 如果 <xref:System.Data.DataSet> 中沒有結構描述，則不會載入任何資料。<br /><br /> 如果資料是 DiffGram，**則忽略架構**具有與**DiffGram**相同的功能 *。*|  
|**InferSchema**|忽略任何內嵌結構描述，並推斷每個 XML 資料結構的結構描述，然後載入資料。<br /><br /> 如果 <xref:System.Data.DataSet> 已經包含結構描述，則會將資料行加入現有的資料表來擴充目前的結構描述。 如果沒有現有的資料表，則不會加入額外的資料表。 如果推斷資料表已經存在但使用不同的命名空間，或者任何推斷的資料行與現有資料行衝突，便會擲回例外狀況。<br /><br /> 有關**ReadXmlSchema**如何從 XML 文檔中推斷架構的詳細資訊，請參閱[從 XML 推斷 DataSet 關聯式結構](inferring-dataset-relational-structure-from-xml.md)。|  
|**迪夫格拉姆**|讀取 DiffGram 並將資料加入目前的結構描述。 **DiffGram**將新行與唯一識別碼值匹配的現有行合併。 請參閱這個主題結尾處＜從 XML 合併資料＞。 有關差異圖的更多資訊，請參閱[差異圖](diffgrams.md)。|  
|**片段**|繼續讀取多個 XML 片段，直到到達資料流末。 與 <xref:System.Data.DataSet> 結構描述相符的片段會附加至適當的資料表。 與 <xref:System.Data.DataSet> 結構描述不相符的片段則會捨棄。|  
  
> [!NOTE]
> 如果將**XmlReader**傳遞給將**XmlReader**定位到 XML 文檔中的一部分，**則 ReadXml**將讀取到下一個元素節點，並將其視為根項目，唯讀取到元素節點結束。 如果指定**XmlReadMode.片段**，則不適用。  
  
## <a name="dtd-entities"></a>DTD 實體  
 如果 XML 包含在文件類型定義 （DTD） 架構中定義的實體），則如果嘗試<xref:System.Data.DataSet>通過將檔案名、流或非驗證**XmlReader**傳遞到**ReadXml**來載入 ，將引發異常。 相反，您必須創建一個**Xml 驗證讀取器**，其中**實體處理**設置為**實體處理.展開實體**，並將**您的 Xml 驗證讀取器**傳遞給**ReadXml**。 在 讀取 之前 **，XmlValidingReader**將展開實體<xref:System.Data.DataSet>。  
  
 下列程式碼範例顯示如何從 XML 資料流載入 <xref:System.Data.DataSet>。 第一個示例顯示檔案名傳遞給**ReadXml**方法。 第二個範例顯示內含使用 <xref:System.IO.StringReader> 所載入之 XML 的字串。  
  
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
> 如果調用**ReadXml**載入非常大的檔，則可能會遇到性能降低的問題。 為了確保**ReadXml**在大型檔中的最佳性能，請調用 中<xref:System.Data.DataTable.BeginLoadData%2A>每個表<xref:System.Data.DataSet>的方法，然後調用**ReadXml**。 最後再針對 <xref:System.Data.DataTable.EndLoadData%2A> 的每個資料表呼叫 <xref:System.Data.DataSet> (如下列範例所示)。  
  
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
> 如果您的<xref:System.Data.DataSet>XSD 架構包含**目標命名空間**，則資料可能無法讀取，並且在調用**ReadXml**以載入<xref:System.Data.DataSet>包含沒有限定命名空間的元素時可能會遇到異常。 在這種情況下，要讀取非限定元素，請將**元素FormDefault**設置為 XSD 架構中的"合格"。 例如：  
  
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
 如果 <xref:System.Data.DataSet> 已經包含資料，則會將 XML 的新資料加入 <xref:System.Data.DataSet> 中已出現的資料中。 **ReadXml**不會從 XML 合併到<xref:System.Data.DataSet>具有匹配主鍵的任何行資訊中。 要用 XML 中的新資訊覆蓋現有行資訊，請使用**ReadXml**創建新<xref:System.Data.DataSet>的<xref:System.Data.DataSet.Merge%2A>，然後將<xref:System.Data.DataSet>新資訊寫入<xref:System.Data.DataSet>現有 。 請注意，使用**ReadXML**使用**DiffGram**的**XmlReadMode**載入 DiffGram 將合併具有相同唯一識別碼的行。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [在資料集中使用 XML](using-xml-in-a-dataset.md)
- [DiffGram](diffgrams.md)
- [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [從 XML 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)
- [從 XML 載入資料集結構描述資訊](loading-dataset-schema-information-from-xml.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
