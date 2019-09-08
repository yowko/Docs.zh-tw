---
title: 資料集和 XmlDataDocument 同步處理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: e76e81153cb7d074fe975744c6b6041ee04be90f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785423"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>資料集和 XmlDataDocument 同步處理
ADO.NET <xref:System.Data.DataSet> 提供資料的關聯式表示。 若要存取階層式資料，可以使用 .NET Framework 中提供的 XML 類別。 過去，這兩個資料表示一直是分開使用； 不過，.NET Framework 會分別透過**DataSet**物件和<xref:System.Xml.XmlDataDocument>物件，啟用即時、同步存取關聯式和階層式的資料標記法。  
  
 當**資料集**與**XmlDataDocument**同步處理時，這兩個物件都會使用單一資料集。 這表示，如果對**資料集**進行變更，變更就會反映在**XmlDataDocument**中，反之亦然。 **資料集**和**XmlDataDocument**之間的關聯性可讓單一應用程式（使用單一資料集）存取以**資料集**為基礎的整個服務套件（例如 Web form 和），以建立極大的彈性。Windows Forms 控制項和 Visual Studio .NET 設計工具），以及 XML 服務的套件，包括可延伸樣式表語言（XSL）、XSL 轉換（XSLT）和 XML 路徑語言（XPath）。 您不用替應用程式選擇要將哪一組服務當成目標，因為這兩個服務都可以使用。  
  
 有數種方式可讓您將**資料集**與**XmlDataDocument**同步處理。 您可以：  
  
- 使用架構（也就是關聯式結構）和資料填入資料**集**，然後將它與新的**XmlDataDocument**同步處理。 如此便能提供現有關聯式資料的階層式檢視。 例如：  
  
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
  
- 僅以架構填入**資料集**（例如強型別**資料集**），將它與**XmlDataDocument**同步處理，然後從 XML 檔載入**XmlDataDocument** 。 如此能提供現有階層式資料的關聯式檢視。 DataSet 架構中的資料表名稱和**資料**行名稱，必須與您想要同步處理的 XML 元素名稱相符。 這項比對是區分大小寫的。  
  
     請注意，**資料集**的架構只需要符合您想要在關聯式視圖中公開的 XML 元素。 如此，您可能會有非常大的 XML 文件，但文件中可能會有非常小的關聯式「視窗」。 即使**資料集**只公開其中的一小部分， **XmlDataDocument**還是會保留整個 XML 檔。 （如需這項工作的詳細範例，請參閱[同步處理資料集與 XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md)）。  
  
     下列程式碼範例示範如何建立**資料集**並填入其架構，然後將它與**XmlDataDocument**同步處理的步驟。 請注意，**資料集**架構只需要符合您想要使用**資料集**公開之**XmlDataDocument**中的元素。  
  
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
  
     如果**XmlDataDocument**與包含資料的**DataSet**同步處理，您就無法載入它。 且會擲回例外狀況。  
  
- 建立新的**XmlDataDocument** ，並從 XML 檔載入它，然後使用**XmlDataDocument**的**DataSet**屬性來存取資料的關聯式視圖。 您必須先設定**資料集**的架構，才能使用**資料集**來查看**XmlDataDocument**中的任何資料。 同樣地，DataSet 架構中的資料表名稱和**資料**行名稱，必須與您想要與之同步處理的 XML 元素名稱相符。 這項比對是區分大小寫的。  
  
     下列程式碼範例顯示如何在**XmlDataDocument**中存取資料的關聯式視圖。  
  
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
  
 將**XmlDataDocument**與**資料集**同步處理的另一個優點是，會保留 XML 檔的精確度。 如果資料**集**是使用**ReadXml**從 xml 檔填入，則在使用**WriteXml**將資料寫回為 xml 檔時，可能會與原始 XML 檔有相當大的差異。 這是因為**資料集**不會維護 XML 檔中的格式，例如空白字元或階層式資訊，例如元素順序。 **DataSet**也不包含 XML 檔中已忽略的元素，因為它們不符合**資料集**的架構。 同步處理**XmlDataDocument**與**資料集**，可讓原始 XML 檔的格式設定和階層式元素結構在**XmlDataDocument**中維護，而**資料集**只包含資料和適用于**資料集**的架構資訊。  
  
 將**資料集**與**XmlDataDocument**同步處理時，結果可能會根據您<xref:System.Data.DataRelation>的物件是否已嵌套而有所不同。 如需詳細資訊，請參閱 <<c0>嵌套 datarelation。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 XmlDataDocument 同步處理資料集](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 示範如何使用**XmlDataDocument**來同步處理強型別**資料集**與最少的架構。  
  
 [對資料集執行 XPath 查詢](performing-an-xpath-query-on-a-dataset.md)  
 示範對**資料集**的內容執行 XPath 查詢。  
  
 [將 XSLT 轉換套用至資料集](applying-an-xslt-transform-to-a-dataset.md)  
 示範如何將 XSLT 轉換套用至**資料集**的內容。  
  
## <a name="related-sections"></a>相關章節  
 [在 DataSet 中使用 XML](using-xml-in-a-dataset.md)  
 描述**資料集**如何與 xml 做為資料來源互動，包括將**資料集**的內容載入和保存為 xml 資料。  
  
 [巢狀 DataRelation](nesting-datarelations.md)  
 討論將**資料集**的內容表示為 XML 資料時，嵌套**DataRelation**物件的重要性，並描述如何建立這些關聯性。  
  
 [DataSet、DataTable 和 DataView](index.md)  
 描述**資料集**以及如何使用它來管理應用程式資料，以及與資料來源互動，包括關係資料庫和 XML。  
  
 <xref:System.Xml.XmlDataDocument>  
 包含**XmlDataDocument**類別的參考資訊。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](../ado-net-overview.md)
