---
title: 從 XML 載入資料集
description: 瞭解如何從 XML 將內容新增至 ADO.NET 資料集。 .NET Framework 針對載入的專案和資料集結構提供彈性。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 0920acac2c82677cfce37703b7027dedce91a535
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166803"
---
# <a name="loading-a-dataset-from-xml"></a>從 XML 載入資料集

可以從 XML 資料流或文件建立 ADO.NET <xref:System.Data.DataSet> 的內容。 此外，使用 .NET Framework 可讓您在決定從 XML 載入何種資訊，以及如何建立 <xref:System.Data.DataSet> 的結構描述或關聯式結構時，擁有相當大的彈性。  
  
 若要 <xref:System.Data.DataSet> 使用 XML 中的資料填入，請使用物件的 **ReadXml** 方法 <xref:System.Data.DataSet> 。 **ReadXml**方法會從檔案、資料流程或**XmlReader**進行讀取，並將 XML 來源作為引數，再加上選擇性的**XmlReadMode**引數。 如需 **XmlReader**的詳細資訊，請參閱 [使用 XmlTextReader 讀取 XML 資料](/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100))。 **ReadXml**方法會讀取 XML 資料流程或檔的內容，並載入 <xref:System.Data.DataSet> 具有資料的。 它也會 <xref:System.Data.DataSet> 根據指定的 **XmlReadMode** ，以及是否已存在關聯式結構描述，來建立的關聯式架構。  
  
 下表描述 **XmlReadMode** 引數的選項。  
  
|選項|描述|  
|------------|-----------------|  
|**Auto**|此為預設值。 檢查 XML 並依下列順序選擇最適當的選項：<br /><br /> -如果 XML 為 DiffGram，則會使用 **diffgram** 。<br />-如果 <xref:System.Data.DataSet> 包含架構或 XML 包含內嵌架構，則會使用 **ReadSchema** 。<br />-如果不 <xref:System.Data.DataSet> 包含架構，且 XML 未包含內嵌架構，則會使用 **InferSchema** 。<br /><br /> 如果您知道要讀取的 XML 格式，建議您設定明確的 **XmlReadMode**，而不是接受 **自動** 預設值，以獲得最佳效能。|  
|**ReadSchema**|讀取任何內嵌結構描述，並載入資料和結構描述。<br /><br /> 如果 <xref:System.Data.DataSet> 已經包含結構描述，則會將新資料表從內嵌結構描述加入 <xref:System.Data.DataSet> 的現有結構描述中。 如果內嵌結構描述中的任何資料表已經存在於 <xref:System.Data.DataSet> 中，則會擲回例外狀況。 您將無法使用 **XmlReadMode. ReadSchema**修改現有資料表的架構。<br /><br /> 如果 <xref:System.Data.DataSet> 不包含結構描述，且沒有內嵌結構描述，則不會讀取任何資料。<br /><br /> 內嵌結構描述可使用 XML 結構描述定義語言 (XSD) 的結構描述來定義。 如需將內嵌架構寫為 XML 架構的詳細資訊，請參閱 [從 XML 架構衍生資料集關聯式結構 (XSD) ](deriving-dataset-relational-structure-from-xml-schema-xsd.md)。|  
|**IgnoreSchema**|忽略任何內嵌結構描述，並將資料載入現有的 <xref:System.Data.DataSet> 結構描述中。 任何與現有結構描述不相符的資料會被捨棄。 如果 <xref:System.Data.DataSet> 中沒有結構描述，則不會載入任何資料。<br /><br /> 如果資料是 DiffGram， **IgnoreSchema** 與 **diffgram**具有相同的功能 *。*|  
|**InferSchema**|忽略任何內嵌結構描述，並推斷每個 XML 資料結構的結構描述，然後載入資料。<br /><br /> 如果 <xref:System.Data.DataSet> 已經包含結構描述，則會將資料行加入現有的資料表來擴充目前的結構描述。 如果沒有現有的資料表，則不會加入額外的資料表。 如果推斷資料表已經存在但使用不同的命名空間，或者任何推斷的資料行與現有資料行衝突，便會擲回例外狀況。<br /><br /> 如需有關 **ReadXmlSchema** 如何從 xml 檔推斷架構的詳細資訊，請參閱 [從 Xml 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)。|  
|**DiffGram**|讀取 DiffGram 並將資料加入目前的結構描述。 **DiffGram** 會將新的資料列與唯一識別碼值相符的現有資料列合併。 請參閱這個主題結尾處＜從 XML 合併資料＞。 如需 Diffgram 的詳細資訊，請參閱 [diffgram](diffgrams.md)。|  
|**片段**|繼續讀取多個 XML 片段，直到到達資料流末。 與 <xref:System.Data.DataSet> 結構描述相符的片段會附加至適當的資料表。 與 <xref:System.Data.DataSet> 結構描述不相符的片段則會捨棄。|  
  
> [!NOTE]
> 如果您將 **XmlReader** 轉換成 **ReadXml** ，並將它放入 XML 檔中， **ReadXml** 將會讀取至下一個元素節點，並將該專案視為根項目，直到專案節點的結尾為止。 如果您指定 **XmlReadMode**，這並不適用。  
  
## <a name="dtd-entities"></a>DTD 實體  

 如果您的 XML 包含在檔案類型定義中所定義的實體 (DTD) 架構，則如果您嘗試將 <xref:System.Data.DataSet> 檔案名、資料流程或非驗證 **XmlReader** 傳遞給 **ReadXml**來載入，則會擲回例外狀況。 相反地，您必須建立 **XmlValidatingReader**，並將 **EntityHandling** 設定為 **EntityHandling. entityhandling.expandentities**，並將您的 **XmlValidatingReader** 傳遞給 **ReadXml**。 **XmlValidatingReader**會先展開實體，再進行讀取 <xref:System.Data.DataSet> 。  
  
 下列程式碼範例顯示如何從 XML 資料流載入 <xref:System.Data.DataSet>。 第一個範例顯示將檔案名傳遞給 **ReadXml** 方法。 第二個範例顯示內含使用 <xref:System.IO.StringReader> 所載入之 XML 的字串。  
  
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
> 如果您呼叫 **ReadXml** 載入非常大的檔案，您可能會遇到效能變慢。 若要確保 **ReadXml**的最佳效能，請在大型檔案中， <xref:System.Data.DataTable.BeginLoadData%2A> 針對中的每個資料表呼叫方法， <xref:System.Data.DataSet> 然後呼叫 **ReadXml**。 最後再針對 <xref:System.Data.DataTable.EndLoadData%2A> 的每個資料表呼叫 <xref:System.Data.DataSet> (如下列範例所示)。  
  
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
> 如果的 XSD 架構 <xref:System.Data.DataSet> 包含 **targetNamespace**，可能無法讀取資料，而且您可能會在呼叫 **ReadXml** 以載入 <xref:System.Data.DataSet> 包含沒有限定命名空間之元素的 XML 時，遇到例外狀況。 在此情況下，若要讀取不合格的元素，請將 **elementFormDefault** 設為等於 XSD 架構中的 "合格"。 例如：  
  
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

 如果 <xref:System.Data.DataSet> 已經包含資料，則會將 XML 的新資料加入 <xref:System.Data.DataSet> 中已出現的資料中。 **ReadXml** 不會從 XML 合併為 <xref:System.Data.DataSet> 具有相符主鍵的任何資料列資訊。 若要使用 XML 中的新資訊來覆寫現有的資料列資訊，請使用 **ReadXml** 建立新的 <xref:System.Data.DataSet> ，然後將 <xref:System.Data.DataSet.Merge%2A> 新的 <xref:System.Data.DataSet> 加入至現有的 <xref:System.Data.DataSet> 。 請注意，使用具有**DiffGram** **XmlReadMode**的**ReadXML**載入 DiffGram 時，將會合並具有相同唯一識別碼的資料列。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [在資料集中使用 XML](using-xml-in-a-dataset.md)
- [DiffGram](diffgrams.md)
- [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [從 XML 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)
- [從 XML 載入資料集結構描述資訊](loading-dataset-schema-information-from-xml.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
