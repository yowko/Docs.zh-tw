---
title: 從 XML 載入資料集結構描述資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: b895ad59ed0ab2542ecdfb04b6db559e12edc55c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928385"
---
# <a name="loading-dataset-schema-information-from-xml"></a>從 XML 載入資料集結構描述資訊
的架構<xref:System.Data.DataSet> (其資料表、資料行、關聯和條件約束) 可以透過程式設計方式定義、由的**Fill**或**FillSchema**方法<xref:System.Data.Common.DataAdapter>建立, 或是從 XML 檔載入。 若要從 XML 檔載入**資料集**架構資訊, 您可以使用**資料集**的**ReadXmlSchema**或**InferXmlSchema**方法。 **ReadXmlSchema**可讓您從包含 xml 架構定義語言 (XSD) 架構的檔, 或具有內嵌 xml 架構的 xml 檔, 載入或推斷**資料集**架構資訊。 **InferXmlSchema**可讓您從 XML 檔推斷架構, 同時忽略您指定的特定 XML 命名空間。  
  
> [!NOTE]
> 當您使用 Web 服務或 XML 序列化來傳送使用 XSD 結構 (例如, 嵌套關聯) 在記憶體中建立的**資料集**時, 可能不會保留**資料集**內的資料表順序。 因此, 在此情況下,**資料集**的收件者不應該相依于資料表排序。 不過, 如果要傳送之**資料集**的架構是從 XSD 檔案讀取, 而不是在記憶體中建立, 則一律會保留資料表順序。  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 若要從 XML 檔載入**資料集**的架構, 而不載入任何資料, 您可以使用**DataSet**的**ReadXmlSchema**方法。 **ReadXmlSchema**會使用 XML 架構定義語言 (XSD) 架構來建立定義的**資料集**架構。  
  
 **ReadXmlSchema**方法會接受檔案名、資料流程或包含要載入之 XML 檔的**XmlReader**的單一引數。 XML 文件只能包含結構描述或是內嵌於包含資料的 XML 項目的結構描述。 如需將內嵌架構撰寫為 XML 架構的詳細資訊, 請參閱[從 XML 架構 (XSD) 衍生資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)。  
  
 如果傳遞至**ReadXmlSchema**的 XML 檔不包含內嵌架構資訊, 則**READXMLSCHEMA**會從 XML 檔中的元素推斷架構。 如果**資料集**已經包含架構, 則會藉由加入新的資料表 (如果尚未存在) 來擴充目前的架構。 新的資料行將不會加入現有的資料表。 如果加入的資料行已經存在於 DataSet 中, 但其類型與在 XML 中找到的**資料**行不相容, 則會擲回例外狀況。 如需**ReadXmlSchema**如何從 xml 檔推斷架構的詳細資訊, 請參閱[從 Xml 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。  
  
 雖然**ReadXmlSchema**只會載入或推斷**資料集**的架構, 但**資料集**的**ReadXml**方法會載入或推斷 XML 檔中所包含的架構和資料。 如需詳細資訊, 請參閱[從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)。  
  
 下列程式碼範例示範如何從 XML 檔或資料流程載入**DataSet**架構。 第一個範例顯示將 XML 架構檔案名傳遞至**ReadXmlSchema**方法。 第二個範例會顯示**StreamReader**。  
  
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
 您也可以使用**資料集**的**InferXmlSchema**方法, 指示**資料集**從 XML 檔推斷其架構。 **InferXmlSchema**的運作方式與使用**XmlReadMode** **InferSchema** (載入資料和推斷架構) 的**ReadXml**相同, 如果所讀取的檔未包含任何內嵌架構, 則**ReadXmlSchema** 。 不過, **InferXmlSchema**提供了額外的功能, 可讓您指定在推斷架構時要忽略的特定 XML 命名空間。 **InferXmlSchema**會採用兩個必要的引數: XML 檔的位置 (由檔案名、資料流程或**XmlReader**指定)。以及要由作業忽略之 XML 命名空間的字串陣列。  
  
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
  
 因為先前 XML 檔中的專案指定了屬性, 所以**ReadXmlSchema**方法和**ReadXml**方法 ( **XmlReadMode**為**InferSchema** ) 會針對中的每個元素建立資料表記錄**分類**、類別目錄、類別**名稱**、**描述**、**產品**、 **ProductID**、 **ReorderLevel**和已**停止**。 (如需詳細資訊, 請參閱[從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md))。不過, 更適當的結構是只建立 category 和**Products**資料表, 然後在 category 資料表中建立 [類別目錄]、[**類別名稱**] 和 [**描述**] 資料行, 以及 **Products**資料表中的 ProductID、 **ReorderLevel**和已**停止**資料行。 為確保推斷的架構忽略 XML 元素中指定的屬性, 請使用**InferXmlSchema**方法, 並指定要忽略之**officedata**的 XML 命名空間, 如下列範例所示。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>另請參閱

- [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
