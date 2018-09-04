---
title: 從 XML 載入資料集結構描述資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: a076dcbbe79a7ec0dfbd727e0d0c752bd4675eef
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515978"
---
# <a name="loading-dataset-schema-information-from-xml"></a>從 XML 載入資料集結構描述資訊
結構描述<xref:System.Data.DataSet>（其資料表、 資料行、 關聯和條件約束） 可以定義以程式設計的方式，由**填滿**或是**FillSchema**方法<xref:System.Data.Common.DataAdapter>，或從載入XML 文件。 載入**資料集**結構描述資訊從 XML 文件，您可以使用**ReadXmlSchema**或**InferXmlSchema**方法**的資料集**. **ReadXmlSchema**可讓您載入或推斷**資料集**從包含 XML 結構描述定義語言 (XSD) 結構描述或內嵌 XML 結構描述的 XML 文件的文件的結構描述資訊。 **InferXmlSchema**可讓您來推斷 XML 文件的結構描述，但略過您指定特定 XML 命名空間。  
  
> [!NOTE]
>  資料表中的順序**資料集**可能不會保留當您將使用 Web 服務或 XML 序列化**DataSet**建立記憶體中使用 XSD 建構 （例如巢狀關聯）。 因此，收件者**資料集**不應該相依於資料表的排序在此情況下。 不過，資料表排序一定會保留如果的結構描述**資料集**傳輸已讀取從 XSD 檔案，而不是建立於記憶體中。  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 若要載入的結構描述**資料集**從 XML 文件不載入任何資料，您可以使用**ReadXmlSchema**方法**資料集**。 **ReadXmlSchema**會建立**資料集**使用 XML 結構描述定義語言 (XSD) 結構描述定義的結構描述。  
  
 **ReadXmlSchema**方法接受單一引數的檔案名稱、 資料流，或有**XmlReader**包含要載入之 XML 文件。 XML 文件只能包含結構描述或是內嵌於包含資料的 XML 項目的結構描述。 如需有關撰寫為 XML 結構描述的內嵌結構描述的詳細資訊，請參閱 <<c0> [ 衍生資料集關聯式結構從 XML 結構描述 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)。  
  
 如果 XML 文件傳遞至**ReadXmlSchema**不包含內嵌結構描述資訊， **ReadXmlSchema**會推斷的結構描述，從 XML 文件中的項目。 如果**資料集**已經包含結構描述、 目前的結構描述將延伸加入新的資料表，如果它們尚不存在。 新的資料行將不會加入現有的資料表。 如果要新增資料行已經存在於**資料集**但其不相容的類型與資料行在 XML 中，會擲回例外狀況。 如需詳細資訊，瞭解**ReadXmlSchema**推斷結構描述從 XML 文件，請參閱[推斷資料集關聯式結構從 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。  
  
 雖然**ReadXmlSchema**載入或推斷的結構描述**資料集**，則**ReadXml**方法**DataSet**載入或推斷兩者結構描述和 XML 文件中所包含的資料。 如需詳細資訊，請參閱 <<c0> [ 從 XML 載入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)。  
  
 下列程式碼範例示範如何載入**資料集**從 XML 文件或資料流的結構描述。 第一個範例顯示 XML 結構描述檔案名稱被傳遞給**ReadXmlSchema**方法。 第二個範例所示**System.IO.StreamReader**。  
  
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
  
## <a name="inferxmlschema"></a>InferXmlSchema  
 您也可以指示**資料集**推斷 XML 文件使用其結構描述**InferXmlSchema**方法**資料集**。 **InferXmlSchema**運作方式進行這兩項**ReadXml**具有**XmlReadMode**的**InferSchema** （載入資料，以及推斷結構描述），並**ReadXmlSchema**如果正在讀取的文件包含內嵌結構描述。 不過， **InferXmlSchema**提供其他功能，可讓您指定在推斷結構描述時要忽略特定的 XML 命名空間。 **InferXmlSchema**兩個必要引數： 由檔案名稱、 資料流中，指定的 XML 文件的位置或有**XmlReader**; 以及作業所忽略的 XML 命名空間的字串陣列。  
  
 例如，請考量下列 XML：  
  
```xml  
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
  
 因為在上述的 XML 文件中的項目指定的屬性同時**ReadXmlSchema**方法並**ReadXml**方法**XmlReadMode**的**InferSchema**會在文件中建立資料表的每個項目：**分類**， **CategoryID**， **CategoryName**，**描述**，**產品**， **ProductID**， **ReorderLevel**，以及**停止**. (如需詳細資訊，請參閱 <<c0> [ 推斷資料集關聯式結構從 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。)不過，更適當的結構是只建立**分類**並**產品**資料表，然後再建立**CategoryID**，**類別名稱**，並**描述**中的資料行**類別**資料表中，並**ProductID**， **ReorderLevel**，和**Discontinued**中的資料行**產品**資料表。 若要確保推斷的結構描述會忽略 XML 項目中指定的屬性，請使用**InferXmlSchema**方法並指定的 XML 命名空間**officedata**被忽略，如中所示下列範例。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>另請參閱  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
