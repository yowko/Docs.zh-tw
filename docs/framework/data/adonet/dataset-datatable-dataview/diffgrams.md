---
title: "DiffGram | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DiffGram
DiffGram 是 XML 格式，可用來識別資料項目的目前和原始版本。  <xref:System.Data.DataSet> 使用 DiffGram 格式以載入保存內容，並將內容序列化以透過網路連接傳輸。  將 <xref:System.Data.DataSet> 寫為 DiffGram 時，會把所有必要資訊填入 DiffGram，以正確重新建立 <xref:System.Data.DataSet> 的內容 \(而非結構描述\)，包括來自 **Original** 和 **Current** 資料列版本的資料行值、資料列錯誤資訊和資料列順序。  
  
 從 XML Web Service 傳送和擷取 <xref:System.Data.DataSet> 時，會隱含使用 DiffGram 格式。  此外，使用 **ReadXml** 方法從 XML 載入 <xref:System.Data.DataSet> 的內容，或使用 **WriteXml** 方法在 XML 中寫入 <xref:System.Data.DataSet> 的內容時，您可以指定將內容當做 DiffGram 來讀取或寫入。  如需詳細資訊，請參閱[從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)與[將 DataSet 內容撰寫成 XML 資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)。  
  
 雖然 DiffGram 格式在 .NET Framework 中主要是用來當做 <xref:System.Data.DataSet> 內容的序列化格式，您也可以使用 DiffGrams 修改 Microsoft SQL Server 資料庫中的資料表資料。  
  
 Diffgram 是藉由將所有資料表的內容寫入至 **\<diffgram\>** 項目而產生。  
  
### 若要產生 Diffgram  
  
1.  產生根資料表 \(即不具任何父項目的資料表\) 的清單。  
  
2.  針對清單中的每個資料表及其子代 \(Descendant\)，在 Diffgram 的第一個區段中寫出所有資料列的目前版本。  
  
3.  針對 <xref:System.Data.DataSet> 中的每個資料表，在 Diffgram 的 **\<before\>** 區段中寫出所有資料列的原始版本 \(若有\)。  
  
4.  針對有錯誤的資料列，在 Diffgram 的 **\<errors\>** 區段中寫入錯誤內容。  
  
 Diffgram 會從 XML 檔案的開頭依序處理到結尾。  
  
### 若要處理 Diffgram  
  
1.  處理 Diffgram 的第一個區段，其中包含資料列的目前版本。  
  
2.  處理第二個或 **\<before\>** 區段，這些區段中包含已修改和已刪除資料列的原始資料列版本。  
  
    > [!NOTE]
    >  如果資料列標示為已刪除，則刪除作業可能也會刪除該資料列的子代，根據目前 <xref:System.Data.DataSet> 的 `Cascade` 屬性而定。  
  
3.  處理 **\<errors\>** 區段。  針對此區段中每個項目的指定資料列和資料行設定錯誤資訊。  
  
> [!NOTE]
>  如果將 <xref:System.Data.XmlWriteMode> 設定為 Diffgram，則目標 <xref:System.Data.DataSet> 和原始 <xref:System.Data.DataSet> 的內容可能不同。  
  
## DiffGram 格式  
 DiffGram 格式分成三個區段：目前資料、原始 \(或「過去」\) 資料和錯誤區段，如下列範例所示。  
  
```  
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
  
 **\<**  ***DataInstance***  **\>**  
 項目的名稱 ***DataInstance***，是用來在這份文件中作為解釋之用。  ***DataInstance*** 項目代表 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 的資料列。  項目會包含 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 的名稱 \(而非 *DataInstance*\)。  無論這個 DiffGram 格式區塊是否經過修改，都會包含目前的資料。  已修改過的項目或資料列是以 **diffgr:hasChanges** 註釋來識別。  
  
 **\<diffgr:before\>**  
 這個 DiffGram 格式的區塊包含資料列的原始版本。  此區塊中的項目會使用 **diffgr:id** 註釋，對應至 ***DataInstance*** 區塊中的項目。  
  
 **\<diffgr:errors\>**  
 這個 DiffGram 格式的區塊包含 ***DataInstance*** 區塊中特定資料列的錯誤資訊。  此區塊中的項目會使用 **diffgr:id** 註釋，對應至 ***DataInstance*** 區塊中的項目。  
  
## DiffGram 註釋  
 DiffGram 使用數種註釋，將來自不同 DiffGram 區塊的項目關聯起來，這些 DiffGram 區塊分別代表 <xref:System.Data.DataSet> 中的不同資料列版本或錯誤訊息。  
  
 下列表格說明 DiffGram 命名空間 **urn:schemas\-microsoft\-com:xml\-diffgram\-v1** 中定義的 DiffGram 註釋。  
  
|註釋|描述|  
|--------|--------|  
|**id**|作用是將 **\<** ***DataInstance*** **\>** 區塊中的項目與 **\<diffgr:before\>** 和 **\<diffgr:errors\>** 區塊中的項目進行配對。  具有 **diffgr:id** 註釋的值使用 *\[TableName\]\[RowIdentifier\]* 格式。  例如：`<Customers diffgr:id="Customers1">`。|  
|**parentId**|識別 **\<** ***DataInstance*** **\>** 區塊中哪個項目是目前項目的父項目。  具有 **diffgr:parentId** 註釋的值使用 *\[TableName\]\[RowIdentifier\]* 格式。  例如：`<Orders diffgr:parentId="Customers1">`。|  
|**hasChanges**|將 **\<** ***DataInstance*** **\>** 區塊中的資料列識別為已修改。  **hasChanges** 註釋可以具有以下兩個值的其中之一：<br /><br /> **inserted**<br /> 識別 **Added** 資料列。<br /><br /> **modified**<br /> 識別 **\<diffgr:before\>** 區塊中包含 **Original** 資料列版本的 **Modified** 資料列。  請注意，**Deleted** 資料列會有 **\<diffgr:before\>** 區塊中的 **Original** 資料列版本，但不會有 **\<** ***DataInstance*** **\>** 區塊中的註釋項目。|  
|**hasErrors**|使用 **RowError** 識別 **\<** ***DataInstance*** **\>** 區塊中的資料列。  錯誤項目會置於 **\<diffgr:errors\>** 區塊中。|  
|**錯誤**|包含 **\<diffgr:errors\>** 區塊中特定項目的 **RowError** 文字。|  
  
 <xref:System.Data.DataSet> 將其內容讀取或寫為 DiffGram 時，亦會包含其他附註。  下列表格說明這些在命名空間 **urn:schemas\-microsoft\-com:xml\-msdata** 中定義的其他註釋。  
  
|註釋|描述|  
|--------|--------|  
|**RowOrder**|保留原始資料的資料列順序，並識別特定 <xref:System.Data.DataTable> 中資料列的索引。|  
|**Hidden**|識別 **ColumnMapping** 屬性設定為 **MappingType.Hidden** 的資料行。  屬性是以格式 **msdata:hidden** *\[ColumnName\]*\="*value*" 所撰寫。  例如：`<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`。<br /><br /> 請注意，隱藏的資料行只有在包含資料時才會寫為 DiffGram 屬性。  否則便會予以忽略。|  
  
## 範例 DiffGram  
 以下是 DiffGram 格式的範例。  這個範例顯示在確認變更前，資料表中資料列的更新結果。  CustomerID 為 "ALFKI" 的資料列已經修改，但尚未更新。  這樣一來，**\<** ***DataInstance*** **\>** 區塊中會有具 "Customers1" 之 **diffgr:id** 的 **Current** 資料列，而 **\<diffgr:before\>** 區塊中則會有具 "Customers1" 之 **diffgr:id** 的 **Original** 資料列。  CustomerID 為 "ANATR" 的資料列包括 **RowError**，所以它會加上 `diffgr:hasErrors="true"` 的附註且在 **\<diffgr:errors\>** 區塊中有相關項目。  
  
```  
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
  
## 請參閱  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [將 DataSet 內容撰寫成 XML 資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)