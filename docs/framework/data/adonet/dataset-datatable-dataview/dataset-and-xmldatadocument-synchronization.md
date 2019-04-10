---
title: 資料集和 XmlDataDocument 同步處理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: ea597d7caca3174b17ce16a1e9d70c022e3e75c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164732"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>資料集和 XmlDataDocument 同步處理
ADO.NET <xref:System.Data.DataSet> 提供資料的關聯式表示。 若要存取階層式資料，可以使用 .NET Framework 中提供的 XML 類別。 過去，這兩個資料表示一直是分開使用； 不過，.NET Framework 可讓您透過資料的關聯式和階層式表示的即時、 同步存取**資料集**物件和<xref:System.Xml.XmlDataDocument>物件，分別。  
  
 當**資料集**會與同步處理**XmlDataDocument**，這兩個物件正在使用單一的資料集。 這表示，如果變更**資料集**，此變更會反映在**XmlDataDocument**，反之亦然。 之間的關聯性**資料集**並**XmlDataDocument**藉由使用單一應用程式，使用單一的資料集，來存取內建服務的整個套件建立絕佳的彈性周圍**資料集**（例如 Web Form 和 Windows Form 控制項和 Visual Studio.NET 設計工具），以及 XML 服務，包括 Extensible Stylesheet Language (XSL)、 XSL 轉換 (XSLT) 和 XML 路徑的套件語言 (XPath)。 您不用替應用程式選擇要將哪一組服務當成目標，因為這兩個服務都可以使用。  
  
 有數種方式，您可以同步處理**資料集**具有**XmlDataDocument**。 您可以：  
  
-   填入**資料集**結構描述 （也就是關聯式結構） 和資料，然後使用新的同步處理**XmlDataDocument**。 如此便能提供現有關聯式資料的階層式檢視。 例如:   
  
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
  
-   填入**資料集**只含結構描述 (例如強型別**資料集**)，同步處理搭配**XmlDataDocument**，然後載入**XmlDataDocument**從 XML 文件。 如此能提供現有階層式資料的關聯式檢視。 資料表名稱和資料行名稱，在您**資料集**結構描述必須符合您想要與一起同步處理之 XML 項目的名稱。 這項比對是區分大小寫的。  
  
     請注意，結構描述**資料集**只需要以符合您想要公開在關聯式檢視中的 XML 項目。 如此，您可能會有非常大的 XML 文件，但文件中可能會有非常小的關聯式「視窗」。 **XmlDataDocument**會保留整個 XML 文件時，即使**DataSet**只會公開它的一小部分。 (如這個詳細的範例，請參閱[將 DataSet 與 XmlDataDocument 同步處理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)。)  
  
     下列程式碼範例顯示建立的步驟**資料集**，並填入其結構描述，然後同步處理搭配**XmlDataDocument**。 請注意，**資料集**結構描述只需要符合的項目**XmlDataDocument**您想要使用公開 （expose）**資料集**。  
  
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
  
     無法載入**XmlDataDocument**如果它與同步處理**DataSet**包含資料。 且會擲回例外狀況。  
  
-   建立新**XmlDataDocument**並將它從 XML 文件，載入，然後存取 使用資料的關聯式檢視**資料集**屬性**XmlDataDocument**。 您需要設定的結構描述**資料集**您可以檢視任何資料之前**XmlDataDocument**使用**資料集**。 同樣地，資料表名稱和資料行名稱在您**資料集**結構描述必須符合您想要與一起同步處理之 XML 項目的名稱。 這項比對是區分大小寫的。  
  
     下列程式碼範例示範如何存取中的資料的關聯式檢視**XmlDataDocument**。  
  
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
  
 同步處理的另一個優點**XmlDataDocument**具有**DataSet**是保留的 XML 文件的精確度。 如果**資料集**使用您建立 XML 文件中會填入**ReadXml**，當資料寫回為 XML 文件使用**WriteXml**它可能大幅不同於原始的 XML 文件。 這是因為**資料集**不會維護格式，例如空白字元或階層式的資訊，例如元素的順序，將 XML 文件。 **資料集**也不包含 XML 文件中忽略，因為它們不符合的結構描述項目**Dataset**。 同步處理**XmlDataDocument**具有**資料集**可讓要保留在原始的 XML 文件格式和階層式項目結構**XmlDataDocument**，雖然**資料集**只包含資料和結構描述的資訊適用於**DataSet**。  
  
 同步處理時**資料集**具有**XmlDataDocument**，結果可能會有所不同，就不會您<xref:System.Data.DataRelation>巢狀物件。 如需詳細資訊，請參閱 <<c0> [ 巢狀 Datarelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 XmlDataDocument 同步處理資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 示範如何同步處理的強型別**資料集**，以最少的結構描述，具有**XmlDataDocument**。  
  
 [對資料集執行 XPath 查詢](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 示範的內容中執行 XPath 查詢**資料集**。  
  
 [將 XSLT 轉換套用至 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 示範如何將 XSLT 轉換套用至的內容**資料集**。  
  
## <a name="related-sections"></a>相關章節  
 [在資料集中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 描述如何**資料集**XML 當成資料來源，包括載入和保存的內容互動**DataSet**為 XML 資料。  
  
 [巢狀 DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 討論的重要性巢狀**DataRelation**物件代表的內容時**DataSet**為 XML 資料，並說明如何建立這些關聯性。  
  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 描述**資料集**以及如何使用它來管理應用程式資料，以及包括關聯式資料庫和 XML 的資料來源互動。  
  
 <xref:System.Xml.XmlDataDocument>  
 包含的相關參考資訊**XmlDataDocument**類別。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET Managed 提供者和DataSet開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
