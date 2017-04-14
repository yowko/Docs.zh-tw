---
title: "DataSet 和 XmlDataDocument 同步處理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataSet 和 XmlDataDocument 同步處理
ADO.NET <xref:System.Data.DataSet> 提供資料的關聯式表示。  若要存取階層式資料，可以使用 .NET Framework 中提供的 XML 類別。  過去，這兩個資料表示一直是分開使用；  然而，.NET Framework 會個別透過 **DataSet** 物件和 <xref:System.Xml.XmlDataDocument> 物件，啟用即時、同步存取關聯式及階層式表示的資料。  
  
 **DataSet** 與 **XmlDataDocument** 同步處理時，這兩個物件使用同一組資料；  也就是說，如果 **DataSet** 有變更，則變更也會反映至 **XmlDataDocument**，反之亦然。  **DataSet** 和 **XmlDataDocument** 間的關聯性製造了相當大的彈性；單一應用程式使用同一組資料，即可存取 **DataSet** 上建置的整套服務 \(例如 Web Form、Windows Form 控制項和 Visual Studio .NET 設計工具\)，也能存取整套 XML 服務 \(包括可延伸樣式表語言 \(XSL\)、XSL 轉換 \(XSLT\) 和 XML 路徑語言 \(XPath\)\)。  您不用替應用程式選擇要將哪一組服務當成目標，因為這兩個服務都可以使用。  
  
 將 **DataSet** 與 **XmlDataDocument** 同步處理的方法有下列幾種。  您可以：  
  
-   使用結構描述 \(也就是關聯式結構\) 和資料填入 **DataSet**，然後將它與新的 **XmlDataDocument** 同步處理。  如此便能提供現有關聯式資料的階層式檢視。  例如：  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
-   只使用結構描述填入 **DataSet** \(例如強型別 **DataSet**\)，將該 DataSet 與 **XmlDataDocument** 同步處理，然後從 XML 文件載入 **XmlDataDocument**。  如此能提供現有階層式資料的關聯式檢視。  您 **DataSet** 結構描述中的資料表名稱和資料行名稱必須要與一起同步處理 XML 項目的名稱相符。  這項比對是區分大小寫的。  
  
     請注意，**DataSet** 的結構描述只需要與要公開在關聯式檢視中的 XML 項目相符。  如此，您可能會有非常大的 XML 文件，但文件中可能會有非常小的關聯式「視窗」。  即使 **DataSet** 只公開文件的一小部分，**XmlDataDocument** 仍會保留整份 XML 文件   \(如需此文件的詳細範例，請參閱 [使用 XmlDataDocument 同步處理 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)\)\(英文\)。  
  
     下列程式碼範例顯示建立 **DataSet**、填入其結構描述，然後將它與 **XmlDataDocument** 同步處理的步驟。  請注意，**DataSet** 結構描述只需與您要使用 **DataSet** 所公開的 **XmlDataDocument** 項目相符。  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     如果 **XmlDataDocument** 與包含資料的 **DataSet** 同步處理，您便無法將其載入，  且會擲回例外狀況。  
  
-   建立新的 **XmlDataDocument** 並從 XML 文件載入它，然後使用 **XmlDataDocument** 的 **DataSet** 屬性來存取資料的關聯式檢視。  您需要先設定 **DataSet** 的結構描述，才能使用 **DataSet** 檢視 **XmlDataDocument** 中的任何資料。  同樣的，您 **DataSet** 結構描述中的資料表名稱和資料行名稱，必須與要和它們一起同步處理的 XML 項目的名稱相符。  這項比對是區分大小寫的。  
  
     下列程式碼範例顯示如何存取 **XmlDataDocument** 中資料的關聯式檢視。  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 將 **XmlDataDocument** 與 **DataSet** 同步處理的另一個好處是可以保留原始 XML 文件的架構。  如果 **DataSet** 是使用 **ReadXml** 從 XML 文件填入，則您使用 **WriteXml** 將資料寫回為 XML 文件時，資料可能與原始 XML 文件有相當大的出入。  這是因為 **DataSet** 不會維護來自 XML 文件的泛空白字元或階層式資訊 \(如項目順序\) 的格式。  **DataSet** 也不包含來自 XML 文件的被忽略項目，因為它們與 **Dataset** 的結構描述不符。  將 **DataSet** 與 **XmlDataDocument** 同步處理，可讓原始 XML 文件的格式和階層式項目結構保留在 **XmlDataDocument** 內，同時 **DataSet** 只包含 **DataSet** 適用的資料和結構描述資訊。  
  
 將 **DataSet** 與 **XmlDataDocument** 同步處理時，結果可能視您的 <xref:System.Data.DataRelation> 物件是否為巢狀化而有所不同。  如需詳細資訊，請參閱[巢狀 DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)。  
  
## 在本節中  
 [使用 XmlDataDocument 同步處理 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 示範將具有最小結構描述的強型別 **DataSet** 與 **XmlDataDocument** 同步處理。  
  
 [在 DataSet 上執行 XPath 查詢](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 示範如何在 **DataSet** 內容上執行 XPath 查詢。  
  
 [將 XSLT 轉換套用至 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 示範如何將 XSLT 轉換套用到 **DataSet** 內容。  
  
## 相關章節  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 說明 **DataSet** 如何將 XML 當成資料來源進行互動，包括將 **DataSet** 的內容載入和保存為 XML 資料。  
  
 [巢狀 DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 討論將 **DataSet** 的內容表示為 XML 資料時，巢狀 **DataRelation** 物件的重要性，並描述如何建立這些關聯性。  
  
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 說明 **DataSet** 以及如何用它來管理應用程式資料和與關聯式資料庫和 XML 等資料來源互動。  
  
 [XmlDataDocument 類別](frlrfSystemXmlXmlDataDocumentClassTopic)  
 包含 **XmlDataDocument** 類別的相關參考資訊。  
  
## 請參閱  
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)