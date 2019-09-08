---
title: DiffGram
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: dd70c8d238ba47744eec6ab4a4c6bc1e80a3d0b3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784663"
---
# <a name="diffgrams"></a>DiffGram
DiffGram 是 XML 格式，可用來識別資料項目的目前和原始版本。 <xref:System.Data.DataSet> 使用 DiffGram 格式以載入保存內容，並將內容序列化以透過網路連接傳輸。 當寫入為 diffgram 時，它會將所有必要資訊填入 diffgram，以正確重新建立的內容（但不是架構<xref:System.Data.DataSet>），包括來自**原始**和的資料行值。 <xref:System.Data.DataSet> **目前**的資料列版本、資料列錯誤資訊和資料列順序。  
  
 從 XML Web Service 傳送和擷取 <xref:System.Data.DataSet> 時，會隱含使用 DiffGram 格式。 此外，當您<xref:System.Data.DataSet>使用**ReadXml**方法從 xml 載入的內容，或使用<xref:System.Data.DataSet> **WriteXml**方法在 xml 中寫入的內容時，您可以指定將內容讀取或寫入為 DiffGram。 如需詳細資訊，請參閱[從 Xml 載入資料集](loading-a-dataset-from-xml.md)和將[資料集內容當做 xml 資料寫入](writing-dataset-contents-as-xml-data.md)。  
  
 雖然 DiffGram 格式在 .NET Framework 中主要是用來當做 <xref:System.Data.DataSet> 內容的序列化格式，您也可以使用 DiffGrams 修改 Microsoft SQL Server 資料庫中的資料表資料。  
  
 Diffgram 是藉由將所有資料表的內容寫入至 **\<diffgram >** 元素而產生的。  
  
### <a name="to-generate-a-diffgram"></a>若要產生 Diffgram  
  
1. 產生根資料表 (即不具任何父項目的資料表) 的清單。  
  
2. 針對清單中的每個資料表及其子代 (Descendant)，在 Diffgram 的第一個區段中寫出所有資料列的目前版本。  
  
3. 每個資料表中<xref:System.Data.DataSet>，寫出的所有資料列，原始的版本，如果有的話，請在 **\<之前>** Diffgram 的區段。  
  
4. 如有錯誤，資料列寫入錯誤內容中 **\<錯誤>** Diffgram 的區段。  
  
 Diffgram 會從 XML 檔案的開頭依序處理到結尾。  
  
### <a name="to-process-a-diffgram"></a>若要處理 Diffgram  
  
1. 處理 Diffgram 的第一個區段，其中包含資料列的目前版本。  
  
2. 處理第二個或 **\<之前>** 區段，其中包含原始資料列版本的修改和刪除資料列。  
  
    > [!NOTE]
    > 如果資料列標示為已刪除，則刪除作業可能也會刪除該資料列的子代，根據目前 `Cascade` 的 <xref:System.Data.DataSet> 屬性而定。  
  
3. 處理程序 **\<錯誤>** 一節。 針對此區段中每個項目的指定資料列和資料行設定錯誤資訊。  
  
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
 此元素的名稱***DataInstance***是用於本檔中的說明。 ***DataInstance***元素代表<xref:System.Data.DataSet>的或資料列。 <xref:System.Data.DataTable> 元素會包含<xref:System.Data.DataSet>或<xref:System.Data.DataTable>的名稱，而不是 DataInstance。 無論這個 DiffGram 格式區塊是否經過修改，都會包含目前的資料。 已修改的元素或資料列是以**diffgr： hasChanges**注釋來識別。  
  
 **\<diffgr:before>**  
 這個 DiffGram 格式的區塊包含資料列的原始版本。 在這個區塊中的項目與進行比對中的項目 ***DataInstance*** 封鎖使用**diffgr: id**註釋。  
  
 **\<diffgr:errors>**  
 這個 DiffGram 格式的區塊包含***DataInstance***區塊中特定資料列的錯誤資訊。 在這個區塊中的項目與進行比對中的項目 ***DataInstance*** 封鎖使用**diffgr: id**註釋。  
  
## <a name="diffgram-annotations"></a>DiffGram 註釋  
 DiffGram 使用數種註釋，將來自不同 DiffGram 區塊的項目關聯起來，這些 DiffGram 區塊分別代表 <xref:System.Data.DataSet> 中的不同資料列版本或錯誤訊息。  
  
 下表描述 DiffGram 命名空間**urn：架構-microsoft-com： xml-DiffGram-v1**中定義的 diffgram 注釋。  
  
|註釋|描述|  
|----------------|-----------------|  
|**id**|用來在項目進行配對 **\<before>：之前>** 並 **\<diffgr:errors>** 區塊中的項目 **\<** ***DataInstance*** **>** 區塊。 具有**diffgr： id**注釋的值是以 *[TableName] [rowidentifier 格式]* 格式呈現。 例如：`<Customers diffgr:id="Customers1">`。|  
|**parentId**|識別哪個項目 **\<** ***DataInstance*** **>** 區塊是目前項目的父項目。 具有**diffgr： parentId**注釋的值是以 *[TableName] [rowidentifier 格式]* 格式呈現。 例如：`<Orders diffgr:parentId="Customers1">`。|  
|**hasChanges**|識別中的資料列 **\<** ***DataInstance*** **>** 封鎖，因為修改。 **HasChanges**注釋可以有下列兩個值的其中一個：<br /><br /> **inserted**<br /> 識別**已加入**的資料列。<br /><br /> **被**<br /> 識別**Modified**包含資料列 **原始** 中的資料列版本 **\<before>：之前>** 區塊。 請注意， **Deleted**資料列會有**原始**中的資料列版本 **\<before>：之前>** 區塊，但會在沒有註釋項目 **\<** ***DataInstance*** **>** 區塊。|  
|**hasErrors**|識別中的資料列 **\<** ***DataInstance*** **>** 區塊**RowError**。 錯誤項目會置於 **\<diffgr:errors>** 區塊。|  
|**錯誤**|包含 diffgr 中特定元素之**RowError**的文字 **\<： [錯誤 >** ] 區塊中。|  
  
 <xref:System.Data.DataSet> 將其內容讀取或寫為 DiffGram 時，亦會包含其他附註。 下表描述這些額外的注釋，這些批註定義于命名空間**urn：架構-microsoft-com： xml-msdata**中。  
  
|註釋|描述|  
|----------------|-----------------|  
|**RowOrder**|保留原始資料的資料列順序，並識別特定 <xref:System.Data.DataTable> 中資料列的索引。|  
|**隱含**|將**ColumnMapping**屬性設定為 MappingType 時，將資料行識別為**Hidden**。 屬性會以**msdata： hidden** *[ColumnName]* = "*value*" 的格式撰寫。 例如：`<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`。<br /><br /> 請注意，隱藏的資料行只有在包含資料時才會寫為 DiffGram 屬性。 否則便會予以忽略。|  
  
## <a name="sample-diffgram"></a>範例 DiffGram  
 以下是 DiffGram 格式的範例。 這個範例顯示在確認變更前，資料表中資料列的更新結果。 CustomerID 為 "ALFKI" 的資料列已經修改，但尚未更新。 如此一來，還有**目前**資料列**diffgr: id**具"customers1"中 **\<** ***DataInstance*** **>** 區塊中，並有**原始**資料列**diffgr: id**具"customers1"中 **\<before>：之前>** 區塊。 CustomerID 為 "ANATR" 的資料列包含**RowError**，因此會加`diffgr:hasErrors="true"`上批註，而且 **\<diffgr： errors >** 區塊中會有相關的元素。  
  
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

- [在 DataSet 中使用 XML](using-xml-in-a-dataset.md)
- [從 XML 載入資料集](loading-a-dataset-from-xml.md)
- [將資料集內容當作 XML 資料寫入](writing-dataset-contents-as-xml-data.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md)
