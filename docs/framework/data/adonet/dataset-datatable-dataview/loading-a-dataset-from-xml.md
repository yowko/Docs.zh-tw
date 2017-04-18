---
title: "從 XML 載入 DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 從 XML 載入 DataSet
可以從 XML 資料流或文件建立 ADO.NET <xref:System.Data.DataSet> 的內容。  此外，使用 .NET Framework 可讓您在決定從 XML 載入何種資訊，以及如何建立 <xref:System.Data.DataSet> 的結構描述或關聯式結構時，擁有相當大的彈性。  
  
 若要使用於自 XML 的資料填入 <xref:System.Data.DataSet>，請使用 <xref:System.Data.DataSet> 物件的 **ReadXml** 方法。  **ReadXml** 方法會從檔案、資料流或 **XmlReader** 進行讀取，並將 XML 來源當成引數，加上選擇性的 **XmlReadMode** 引數   \(如需 **XmlReader** 的詳細資訊，請參閱 [NIB: Reading XML Data with XmlTextReader](http://msdn.microsoft.com/zh-tw/762c069b-b50c-41b8-936e-39eacfb0d540)\)。**ReadXml** 方法讀取 XML 資料流或文件的內容，並載入具有資料的 <xref:System.Data.DataSet>。  它也根據指定的 **XmlReadMode** 以及是否已經有關聯式結構描述，建立 <xref:System.Data.DataSet> 的關聯式結構描述。  
  
 下列表格描述 **XmlReadMode** 引數的選項。  
  
|選項|描述|  
|--------|--------|  
|**Auto**|這是預設值。  檢查 XML 並依下列順序選擇最適當的選項：<br /><br /> -   如果 XML 為 DiffGram，則使用 **DiffGram**。<br />-   如果 <xref:System.Data.DataSet> 包含結構描述或 XML 包含內嵌結構描述，則使用 **ReadSchema**。<br />-   如果 <xref:System.Data.DataSet> 不包含結構描述，且 XML 不包含內嵌結構描述，則使用 **InferSchema**。<br /><br /> 如果您知道要讀取的 XML 格式，則為了達到最佳效能，建議您設定外顯的 **XmlReadMode**，而不是接受 **Auto** 預設值。|  
|**ReadSchema**|讀取任何內嵌結構描述，並載入資料和結構描述。<br /><br /> 如果 <xref:System.Data.DataSet> 已經包含結構描述，則會將新資料表從內嵌結構描述加入 <xref:System.Data.DataSet> 的現有結構描述中。  如果內嵌結構描述中的任何資料表已經存在於 <xref:System.Data.DataSet> 中，則會擲回例外狀況。  您將無法使用 **XmlReadMode.ReadSchema** 修改現有資料表的結構描述。<br /><br /> 如果 <xref:System.Data.DataSet> 不包含結構描述，且沒有內嵌結構描述，則不會讀取任何資料。<br /><br /> 內嵌結構描述可使用 XML 結構描述定義語言 \(XSD\) 的結構描述來定義。  如需將內嵌結構描述撰寫為 XML 結構描述的詳細資訊，請參閱 [從 XML 結構描述 \(XSD\) 衍生 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)。|  
|**IgnoreSchema**|忽略任何內嵌結構描述，並將資料載入現有的 <xref:System.Data.DataSet> 結構描述中。  任何與現有結構描述不相符的資料會被捨棄。  如果 <xref:System.Data.DataSet> 中沒有結構描述，則不會載入任何資料。<br /><br /> 如果資料是 DiffGram，**IgnoreSchema** 會具有和 **DiffGram** 相同的功能。|  
|**InferSchema**|忽略任何內嵌結構描述，並推斷每個 XML 資料結構的結構描述，然後載入資料。<br /><br /> 如果 <xref:System.Data.DataSet> 已經包含結構描述，則會將資料行加入現有的資料表來擴充目前的結構描述。  如果沒有現有的資料表，則不會加入額外的資料表。  如果推斷資料表已經存在但使用不同的命名空間，或者任何推斷的資料行與現有資料行衝突，便會擲回例外狀況。<br /><br /> 如需 **ReadXmlSchema** 如何從 XML 文件推斷結構描述的詳細資訊，請參閱 [從 XML 推斷 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。|  
|**DiffGram**|讀取 DiffGram 並將資料加入目前的結構描述。  **DiffGram** 將新資料列與唯一識別項值相符的現有資料列合併。  請參閱這個主題結尾處＜從 XML 合併資料＞。  如需 DiffGram 的詳細資訊，請參閱 [DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)。|  
|**Fragment**|繼續讀取多個 XML 片段，直到到達資料流末。  與 <xref:System.Data.DataSet> 結構描述相符的片段會附加至適當的資料表。  與 <xref:System.Data.DataSet> 結構描述不相符的片段則會捨棄。|  
  
> [!NOTE]
>  如果您將 **XmlReader** 傳遞給位於 XML 文件內的 **ReadXml**，則 **ReadXml** 會讀到下一個項目節點並將它視為根項目，並只讀至該項目節點的結尾。  如果您指定 **XmlReadMode.Fragment** 則不會發生這種情況。  
  
## DTD 實體  
 如果您的 XML 包含在文件類型定義 \(DTD\) 結構描述中所定義的實體，而您嘗試將檔案名稱、資料流或非驗證的 **XmlReader** 傳遞給 **ReadXml** 以載入 <xref:System.Data.DataSet>，則會擲回例外狀況。  因此，您必須建立 **XmlValidatingReader**，其中 **EntityHandling** 設定為 **EntityHandling.ExpandEntities**，並將您的 **XmlValidatingReader** 傳遞給 **ReadXml**。  **XmlValidatingReader** 會在由 <xref:System.Data.DataSet> 進行讀取前，先展開實體。  
  
 下列程式碼範例顯示如何從 XML 資料流載入 <xref:System.Data.DataSet>。  第一個範例顯示檔案名稱被傳遞給 **ReadXml** 方法。  第二個範例顯示內含使用 <xref:System.IO.StringReader> 所載入之 XML 的字串。  
  
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
>  如果要呼叫 **ReadXml** 來載入一個非常大的檔案，將會使效能降低。  為了確保 **ReadXml** 的最佳效能，請在大型檔案上對 <xref:System.Data.DataSet> 的每個資料表呼叫 <xref:System.Data.DataTable.BeginLoadData%2A> 方法，再呼叫 **ReadXml**。  最後再針對 <xref:System.Data.DataSet> 的每個資料表呼叫 <xref:System.Data.DataTable.EndLoadData%2A> \(如下列範例所示\)。  
  
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
>  如果 <xref:System.Data.DataSet> 的 XSD 結構描述包括 **targetNamespace**，則不會讀取資料，而且在呼叫 **ReadXml** 以載入具有 XML \(其內含非限定命名空間的項目\) 的 <xref:System.Data.DataSet> 時，也會遇到例外狀況。  若要在此例中讀取不合格的項目，請在 XSD 結構描述中，將 **elementFormDefault** 設定等於 "qualified"。  例如：  
  
```  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## 從 XML 合併資料  
 如果 <xref:System.Data.DataSet> 已經包含資料，則會將 XML 的新資料加入 <xref:System.Data.DataSet> 中已出現的資料中。  **ReadXml** 不會將任何具有相符之主索引鍵的資料列資訊，從 XML 合併至 <xref:System.Data.DataSet> 中。  若要使用 XML 的新資訊覆寫現有的資料列資訊，請使用 **ReadXml** 建立新的 <xref:System.Data.DataSet>，然後將新的 <xref:System.Data.DataSet> <xref:System.Data.DataSet.Merge%2A> 至現有的 <xref:System.Data.DataSet>。  請注意，使用 **XmlReadMode** 為 **DiffGram** 的 **ReadXML** 載入 DiffGram 時，將會合併具有相同唯一識別項的資料列。  
  
## 請參閱  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=fullName>   
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)   
 [從 XML 結構描述 \(XSD\) 衍生 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)   
 [從 XML 推斷 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [從 XML 載入 DataSet 結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)