---
title: "從 XML 載入 DataSet 結構描述資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 從 XML 載入 DataSet 結構描述資訊
<xref:System.Data.DataSet> 的結構描述 \(其資料表、資料行、關聯和條件約束\) 可以利用程式設計方式進行定義、由 <xref:System.Data.Common.DataAdapter> 的 **Fill** 或 **FillSchema** 方法建立，或從 XML 文件中載入。  若要從 XML 文件載入 **DataSet** 結構描述資訊，您可以使用 **DataSet** 的 **ReadXmlSchema** 或 **InferXmlSchema** 方法。  **ReadXmlSchema** 可讓您從包含 XML 結構描述定義語言 \(XSD\) 結構描述的文件，或具有內嵌 XML 結構描述的 XML 文件，來載入或推斷 **DataSet** 結構描述資訊。  **InferXmlSchema** 可讓您從 XML 文件推斷結構描述，並同時忽略您指定的特定 XML 命名空間。  
  
> [!NOTE]
>  當您使用 Web 服務或 XML 序列化 \(Serialization\)，來傳送使用 XSD 建構 \(例如巢狀關聯\) 在記憶體中建立的 **DataSet** 時，**DataSet** 中的資料表排序可能無法保留。  因此在這種情況下，**DataSet** 的收件者不應該仰賴資料表的排序。  不過，如果傳送的 **DataSet** 的結構描述是從 XSD 檔案中讀取，而不是在記憶體中建立，則資料表排序一定會保留。  
  
## ReadXmlSchema  
 若要從 XML 文件載入 **DataSet** 的結構描述，而不載入任何資料，可以使用 **DataSet** 的 **ReadXmlSchema** 方法。  **ReadXmlSchema** 建立使用 XML 結構描述定義語言 \(XSD\) 結構描述所定義的 **DataSet** 結構描述。  
  
 **ReadXmlSchema** 方法採用檔案名稱、資料流或包含要載入 XML 文件的 **XmlReader** 做為單一引數。  XML 文件只能包含結構描述或是內嵌於包含資料的 XML 項目的結構描述。  如需將內嵌結構描述撰寫為 XML 結構描述的詳細資訊，請參閱 [從 XML 結構描述 \(XSD\) 衍生 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)。  
  
 如果傳遞給 **ReadXmlSchema** 的 XML 文件不包含內嵌結構描述資訊，則 **ReadXmlSchema** 會從 XML 文件中的項目推斷結構描述。  如果 **DataSet** 已經包含結構描述，則目前的結構描述會藉由加入新資料表 \(若尚無資料表\) 而擴充。  新的資料行將不會加入現有的資料表。  如果加入的資料行已經存在於 **DataSet**，但其型別與 XML 中的資料行不相容，則會擲回例外狀況。  如需 **ReadXmlSchema** 如何從 XML 文件推斷結構描述的詳細資訊，請參閱 [從 XML 推斷 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。  
  
 雖然 **ReadXmlSchema** 只載入或推斷 **DataSet** 的結構描述，而 **DataSet** 的 **ReadXml** 方法會載入或推斷 XML 文件中包含的結構描述和資料。  如需詳細資訊，請參閱[從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)。  
  
 下列程式碼範例顯示如何從 XML 文件或資料流載入 **DataSet** 結構描述。  第一個範例顯示 XML 結構描述檔案名稱被傳遞給 **ReadXmlSchema** 方法。  第二個範例顯示 **System.IO.StreamReader**。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## InferXmlSchema  
 您也可以指示 **DataSet** 使用 **DataSet** 的 **InferXmlSchema** 方法從 XML 文件推斷其結構描述。  **InferXmlSchema** 的功能等於 **ReadXml** 加上 **InferSchema** 的 **XmlReadMode** \(載入資料和推斷結構描述\)，而在被讀取的文件不包含內嵌結構描述時，也等於 **ReadXmlSchema**；  不過 **InferXmlSchema** 還提供其他功能，可讓您指定在推斷結構描述時要忽略的特定 XML 命名空間。  **InferXmlSchema** 有兩個必要引數：由檔案名稱、資料流或 **XmlReader** 指定的 XML 文件位置，以及作業所忽略的 XML 命名空間的字串陣列。  
  
 例如，請考量下列 XML：  
  
```  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>   
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>   
  <Description od:adotype="203">Soft drinks and teas</Description>   
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>   
  <ReorderLevel od:adotype="3">10</ReorderLevel>   
  <Discontinued od:adotype="11">0</Discontinued>   
</Products>  
</NewDataSet>  
```  
  
 由於針對前一個 XML 文件中之項目所指定的屬性，**ReadXmlSchema** 方法與 **ReadXml** 方法加上 **InferSchema** 的 **XmlReadMode**，將會為文件中的每個項目建立資料表：**Categories**、**CategoryID**、**CategoryName**、**Description**、**Products**、**ProductID**、**ReorderLevel** 和 **Discontinued**。  \(如需詳細資訊，請參閱 [從 XML 推斷 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)\)。但是，比較適當的結構是只建立 **Categories** 和 **Products** 資料表，然後在 **Categories** 資料表中建立 **CategoryID**、**CategoryName** 和 **Description** 資料行，以及在 **Products** 資料表中建立 **ProductID**、**ReorderLevel** 和 **Discontinued** 資料行。  若要確保推斷的結構描述忽略 XML 項目中指定的屬性，請使用 **InferXmlSchema** 方法，並指定 **officedata** 要忽略的 XML 命名空間，如下列範例所示。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## 請參閱  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [從 XML 結構描述 \(XSD\) 衍生 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)   
 [從 XML 推斷 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)