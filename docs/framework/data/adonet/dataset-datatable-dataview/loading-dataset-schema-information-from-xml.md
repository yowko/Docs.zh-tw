---
title: 從 XML 載入資料集結構描述資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 69994c546fea842ffef1c8c43d6d6f5bc35e0629
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151048"
---
# <a name="loading-dataset-schema-information-from-xml"></a>從 XML 載入資料集結構描述資訊
的<xref:System.Data.DataSet>架構（其表、列、關係和約束）可以以程式設計方式定義、由<xref:System.Data.Common.DataAdapter>的**填充**或**填充架構**方法創建，也可以從 XML 文檔載入。 要從 XML 文檔載入**DataSet**架構資訊，可以使用**DataSet**的**ReadXmlSchema**或**InferXmlSchema**方法。 **ReadXmlSchema**允許您從包含 XML 架構定義語言 （XSD） 架構的文檔或具有內聯 XML 架構的 XML 文檔載入或推斷**DataSet**架構資訊。 **InferXmlSchema**允許您從 XML 文檔中推斷架構，而忽略您指定的某些 XML 命名空間。  
  
> [!NOTE]
> 當您使用 Web 服務或 XML 序列化傳輸使用 XSD 構造（如嵌套關係）在記憶體中創建的**DataSet**時 **，DataSet**中的表排序可能無法保留。 因此，在這種情況下 **，DataSet**的收件者不應依賴于表排序。 但是，如果從 XSD 檔讀取要傳輸的**DataSet**的架構，而不是在記憶體中創建，則始終保留表排序。  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 要從 XML 文檔載入**DataSet**的架構而不載入任何資料，可以使用**DataSet**的**ReadXmlSchema**方法。 **ReadXmlSchema**創建使用 XML 架構定義語言 （XSD） 架構定義的**資料集**架構。  
  
 **ReadXmlSchema**方法採用檔案名、流或**XmlReader**的單個參數，其中包含要載入的 XML 文檔。 XML 文件只能包含結構描述或是內嵌於包含資料的 XML 項目的結構描述。 有關將內聯架構編寫為 XML 架構的詳細資訊，請參閱[從 XML 架構 （XSD） 派生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)。  
  
 如果傳遞給**ReadXmlSchema 的**XML 文檔不包含內聯架構資訊，**則 ReadXmlSchema**將從 XML 文檔中的元素推斷架構。 如果**DataSet**已包含架構，則如果新表不存在，則通過添加新表來擴展當前架構。 新的資料行將不會加入現有的資料表。 如果正在添加的列在**DataSet**中已存在，但與 XML 中找到的列的類型不相容，則引發異常。 有關**ReadXmlSchema**如何從 XML 文檔中推斷架構的詳細資訊，請參閱[從 XML 推斷 DataSet 關聯式結構](inferring-dataset-relational-structure-from-xml.md)。  
  
 儘管**ReadXmlSchema**僅載入或推斷**DataSet**的架構，但**DataSet**的**ReadXml**方法載入或推斷架構和 XML 文檔中的資料。 有關詳細資訊，請參閱從[XML 載入資料集](loading-a-dataset-from-xml.md)。  
  
 以下代碼示例演示如何從 XML 文檔或流載入**DataSet**架構。 第一個示例顯示將 XML 架構檔案名傳遞給**ReadXmlSchema**方法。 第二個示例顯示了**System.IO.StreamReader**。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
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
 您還可以指示**DataSet**使用**DataSet**的**InferXmlSchema**方法從 XML 文檔中推斷其架構。 **InferXml 架構**的功能與使用**推斷模式****的 XmlReadMode**的**ReadXml（** 載入資料以及推斷架構）的功能相同，如果正在讀取的文檔不包含內聯架構，則**ReadXmlSchema**的功能相同。 但是 **，InferXmlSchema**提供了一種附加功能，允許您指定在推斷架構時要忽略的特定 XML 命名空間。 **inferXmlSchema**採用兩個必需的參數：XML 文檔的位置，由檔案名、流或**XmlReader**指定;以及要由操作忽略的 XML 命名空間的字串陣列。  
  
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
  
 由於為前面的XML文檔中的元素指定的屬性 **，ReadXmlSchema**方法和具有**InferSchema** Xml 的**ReadXml** **XmlReadMode**方法都將為文檔中的每個元素創建表：**類別**、**類別 ID、****類別名稱**、**描述**、**產品**、產品**ID、****重新排序級別**和**已停產**。 （有關詳細資訊，請參閱從[XML 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)。但是，更合適的結構是只創建 **"類別**和**產品**"表，然後在 **"類別"** 表中創建**類別 ID、****類別名稱**和**說明**列，並在 **"產品**"表中創建 **"產品識別碼"、"****重新排序級別****"和"停產**"列。 為確保推斷的架構忽略 XML 元素中指定的屬性，請使用**InferXmlSchema**方法並指定要忽略**的 Officedata 的**XML 命名空間，如下例所示。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>另請參閱

- [在資料集中使用 XML](using-xml-in-a-dataset.md)
- [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [從 XML 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)
- [從 XML 載入資料集](loading-a-dataset-from-xml.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
