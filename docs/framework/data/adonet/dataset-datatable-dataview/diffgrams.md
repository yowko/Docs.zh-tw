---
title: DiffGram
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: aff9c2347fab51d853e19bd9dc16666c4ed549b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172797"
---
# <a name="diffgrams"></a>DiffGram

DiffGram 是 XML 格式，可用來識別資料項目的目前和原始版本。 <xref:System.Data.DataSet> 使用 DiffGram 格式以載入保存內容，並將內容序列化以透過網路連接傳輸。 當 <xref:System.Data.DataSet> 寫入為 diffgram 時，它會將所有必要的資訊填入 diffgram，以精確地重新建立的內容，而不是的架構， <xref:System.Data.DataSet> 包括 **原始** 和 **目前** 資料列版本的資料行值、資料列錯誤資訊和資料列順序。  
  
 從 XML Web Service 傳送和擷取 <xref:System.Data.DataSet> 時，會隱含使用 DiffGram 格式。 此外，當 <xref:System.Data.DataSet> 您使用**ReadXml**方法從 xml 載入的內容，或在使用 WriteXml 方法來撰寫 xml 的內容時， <xref:System.Data.DataSet> 可以**WriteXml**指定以 DiffGram 的形式讀取或寫入內容。 如需詳細資訊，請參閱 [從 Xml 載入資料集](loading-a-dataset-from-xml.md) ，並將 [資料集內容寫入為 xml 資料](writing-dataset-contents-as-xml-data.md)。  
  
 雖然 DiffGram 格式在 .NET Framework 中主要是用來當做 <xref:System.Data.DataSet> 內容的序列化格式，您也可以使用 DiffGrams 修改 Microsoft SQL Server 資料庫中的資料表資料。  
  
 Diffgram 是藉由將所有資料表的內容寫入專案來產生的 **\<diffgram>** 。  
  
### <a name="to-generate-a-diffgram"></a>若要產生 Diffgram  
  
1. 產生根資料表 (即不具任何父項目的資料表) 的清單。  
  
2. 針對清單中的每個資料表及其子代 (Descendant)，在 Diffgram 的第一個區段中寫出所有資料列的目前版本。  
  
3. 針對中的每個資料表 <xref:System.Data.DataSet> ，在 Diffgram 的區段中寫出所有資料列的原始版本（如果有的話） **\<before>** 。  
  
4. 針對有錯誤的資料列，在 Diffgram 的區段中寫入錯誤內容 **\<errors>** 。  
  
 Diffgram 會從 XML 檔案的開頭依序處理到結尾。  
  
### <a name="to-process-a-diffgram"></a>若要處理 Diffgram  
  
1. 處理 Diffgram 的第一個區段，其中包含資料列的目前版本。  
  
2. 處理第二個或 **\<before>** 區段，其中包含已修改和已刪除資料列的原始資料列版本。  
  
    > [!NOTE]
    > 如果資料列標示為已刪除，則刪除作業可能也會刪除該資料列的子代，根據目前 `Cascade` 的 <xref:System.Data.DataSet> 屬性而定。  
  
3. 處理 **\<errors>** 區段。 針對此區段中每個項目的指定資料列和資料行設定錯誤資訊。  
  
> [!NOTE]
> 如果將 <xref:System.Data.XmlWriteMode> 設定為 Diffgram，則目標 <xref:System.Data.DataSet> 和原始 <xref:System.Data.DataSet> 的內容可能不同。  
  
## <a name="diffgram-format"></a>DiffGram 格式  

 DiffGram 格式分成三個區段：目前資料、原始 (或「過去」) 資料和錯誤區段，如下列範例所示。  
  
```xml  
<?xml version="1.0"?>  
<diffgr:diffgram
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  
   <DataInstance>  
   </DataInstance>  
  
  <diffgr:before>  
  </diffgr:before>  
  
  <diffgr:errors>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
 DiffGram 格式由下列資料區塊組成：  
  
 **\<**  ***DataInstance***  **>**  
 此元素的名稱 ***DataInstance***，用於本檔中的說明用途。 ***DataInstance***元素代表或的資料 <xref:System.Data.DataSet> 列 <xref:System.Data.DataTable> 。 元素會包含或的名稱，而不是 *DataInstance* <xref:System.Data.DataSet> <xref:System.Data.DataTable> 。 無論這個 DiffGram 格式區塊是否經過修改，都會包含目前的資料。 已修改的專案（或資料列）會以 **diffgr： hasChanges** 注釋來識別。  
  
 **\<diffgr:before>**  
 這個 DiffGram 格式的區塊包含資料列的原始版本。 這個區塊中的專案會使用**diffgr： id**注釋，與***DataInstance***區塊中的元素進行比對。  
  
 **\<diffgr:errors>**  
 這種 DiffGram 格式的區塊包含 ***DataInstance*** 區塊中特定資料列的錯誤資訊。 這個區塊中的專案會使用**diffgr： id**注釋，與***DataInstance***區塊中的元素進行比對。  
  
## <a name="diffgram-annotations"></a>DiffGram 註解  

 DiffGram 使用數種註釋，將來自不同 DiffGram 區塊的項目關聯起來，這些 DiffGram 區塊分別代表 <xref:System.Data.DataSet> 中的不同資料列版本或錯誤訊息。  
  
 下表說明 DiffGram 命名空間 **urn：架構-microsoft-com： xml-DiffGram-v1**中定義的 diffgram 批註。  
  
|Annotation|描述|  
|----------------|-----------------|  
|**id**|用來將和區塊中的專案與 **\<diffgr:before>** **\<diffgr:errors>** 區塊中的元素配對 **\<** ***DataInstance*** **>** 。 具有 **diffgr： id** 注釋的值格式為 *[TableName] [rowidentifier 格式]*。 例如：`<Customers diffgr:id="Customers1">`。|  
|**parentId**|識別區塊中的哪個元素 **\<** ***DataInstance*** **>** 是目前專案的父元素。 具有 **diffgr： parentId** 注釋的值格式為 *[TableName] [rowidentifier 格式]*。 例如：`<Orders diffgr:parentId="Customers1">`。|  
|**hasChanges**|將區塊中的資料列識別 **\<** ***DataInstance*** **>** 為已修改。 **HasChanges**批註可以有下列兩個值的其中一個：<br /><br /> **插入**<br /> 識別 **新增** 的資料列。<br /><br /> **已修改**<br /> 識別 **已修改** 的資料列，其中包含區塊中的 **原始** 資料列版本 **\<diffgr:before>** 。 請注意， **已刪除** 的資料列在區塊中會有 **原始** 的資料列版本 **\<diffgr:before>** ，但區塊中不會有標注的元素 **\<** ***DataInstance*** **>** 。|  
|**hasErrors**|使用 RowError 來識別區塊中的 **\<** ***DataInstance*** **>** 資料**RowError**列。 Error 元素會放置在區塊中 **\<diffgr:errors>** 。|  
|**錯誤**|包含區塊中特定元素的 **RowError** 文字 **\<diffgr:errors>** 。|  
  
 <xref:System.Data.DataSet> 將其內容讀取或寫為 DiffGram 時，亦會包含其他附註。 下表說明這些會在命名空間 **urn：架構-msdata**中定義的其他批註。  
  
|Annotation|描述|  
|----------------|-----------------|  
|**RowOrder**|保留原始資料的資料列順序，並識別特定 <xref:System.Data.DataTable> 中資料列的索引。|  
|**Hidden**|將 **ColumnMapping** 屬性設定為 **MappingType**時，識別資料行。 以 **msdata： hidden** *[ColumnName]*= "*value*" 格式寫入屬性。 例如：`<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`。<br /><br /> 請注意，隱藏的資料行只有在包含資料時才會寫為 DiffGram 屬性。 否則會予以忽略。|  
  
## <a name="sample-diffgram"></a>範例 DiffGram  

 以下是 DiffGram 格式的範例。 這個範例顯示在確認變更前，資料表中資料列的更新結果。 CustomerID 為 "ALFKI" 的資料列已經修改，但尚未更新。 如此一來，區塊中會有**diffgr： id**為 "Customers1" 的**目前** **\<** ***DataInstance*** **>** 資料列，以及在區塊中具有**diffgr： id** "Customers1" 的**原始**資料列 **\<diffgr:before>** 。 CustomerID 為 "ANATR" 的資料列包含 **RowError**，因此它會加上批註， `diffgr:hasErrors="true"` 而且區塊中會有相關的元素 **\<diffgr:errors>** 。  
  
```xml  
<diffgr:diffgram xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
  <CustomerDataSet>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0" diffgr:hasChanges="modified">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>New Company</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers2" msdata:rowOrder="1" diffgram:hasErrors="true">  
      <CustomerID>ANATR</CustomerID>  
      <CompanyName>Ana Trujillo Emparedados y Helados</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers3" msdata:rowOrder="2">  
      <CustomerID>ANTON</CustomerID>  
      <CompanyName>Antonio Moreno Taquera</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers4" msdata:rowOrder="3">  
      <CustomerID>AROUT</CustomerID>  
      <CompanyName>Around the Horn</CompanyName>  
    </Customers>  
  </CustomerDataSet>  
  <diffgr:before>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>Alfreds Futterkiste</CompanyName>  
    </Customers>  
  </diffgr:before>  
  <diffgr:errors>  
    <Customers diffgr:id="Customers2" diffgr:Error="An optimistic concurrency violation has occurred for this row."/>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
## <a name="see-also"></a>另請參閱

- [在資料集中使用 XML](using-xml-in-a-dataset.md)
- [從 XML 載入資料集](loading-a-dataset-from-xml.md)
- [將資料集內容當做 XML 資料寫入](writing-dataset-contents-as-xml-data.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
