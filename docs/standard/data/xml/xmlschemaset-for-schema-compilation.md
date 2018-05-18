---
title: 用於結構描述編譯的 XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91835006925f9768c25ad1a984a3b189e3e4c58c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xmlschemaset-for-schema-compilation"></a>用於結構描述編譯的 XmlSchemaSet
說明 <xref:System.Xml.Schema.XmlSchemaSet>，它是一種可儲存及驗證 XML 結構描述定義語言 (XSD) 結構描述的快取。  
  
## <a name="the-xmlschemaset-class"></a>XmlSchemaSet 類別  
 <xref:System.Xml.Schema.XmlSchemaSet> 是一種可儲存及驗證 XML 結構描述定義語言 (XSD) 結構描述的快取。  
  
 在 <xref:System.Xml?displayProperty=nameWithType> 1.0 版中，已將 XML 結構描述載入 <xref:System.Xml.Schema.XmlSchemaCollection> 類別，做為結構描述程式庫。 在 <xref:System.Xml?displayProperty=nameWithType> 2.0 版中，<xref:System.Xml.XmlValidatingReader> 及 <xref:System.Xml.Schema.XmlSchemaCollection> 類別已過時，並已分別由 <xref:System.Xml.XmlReader.Create%2A> 方法及 <xref:System.Xml.Schema.XmlSchemaSet> 類別取代。  
  
 已經引入 <xref:System.Xml.Schema.XmlSchemaSet> 以修正大量問題，包括標準相容性、效能和過時的 Microsoft XML 資料精簡 (XDR) 結構描述格式。  
  
 下列是 <xref:System.Xml.Schema.XmlSchemaCollection> 類別與 <xref:System.Xml.Schema.XmlSchemaSet> 類別的比較。  
  
|XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|支援 Microsoft XDR 和 W3C XML 結構描述。|只支援 W3C XML 結構描述。|  
|當呼叫 <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> 方法時，會編譯結構描述。|當呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法時，不會編譯結構描述。 這會改進結構描述程式庫建立期間的效能。|  
|每個結構描述都會產生可導致「結構描述島」的個別編譯版本。 因此，所有的 Include 和 Import 都只位於該結構描述範圍內。|編譯的結構描述會產生單一邏輯結構描述 (一「組」結構描述)。 結構描述內已加入至該組的所有匯入結構描述，都會直接加入至它們自身的組。 這表示全部型別都可供所有結構描述使用。|  
|特定目標命名空間在集合中只可以有一個結構描述。|只要不存在型別衝突，就可以為相同的目標命名空間加入多個結構描述。|  
  
## <a name="migrating-to-the-xmlschemaset"></a>移轉至 XmlSchemaSet  
 下列程式碼範例提供從過時的 <xref:System.Xml.Schema.XmlSchemaSet> 類別到新 <xref:System.Xml.Schema.XmlSchemaCollection> 類別的移轉指南。 該程式碼範例會說明兩種類別之間的下列主要差異。  
  
-   不同於 <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> 類別的 <xref:System.Xml.Schema.XmlSchemaCollection> 方法，當呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法時，不會編譯結構描述。 在範例程式碼中，會明確呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法。  
  
-   若要重複處理 <xref:System.Xml.Schema.XmlSchemaSet>，則必須使用 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 屬性。  
  
 下列是過時的 <xref:System.Xml.Schema.XmlSchemaCollection> 程式碼範例。  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 下列是對等的 <xref:System.Xml.Schema.XmlSchemaSet> 程式碼範例。  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a>加入及擷取結構描述  
 使用 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法，可將結構描述加入至 <xref:System.Xml.Schema.XmlSchemaSet>。 將結構描述加入至 <xref:System.Xml.Schema.XmlSchemaSet> 後，便會與目標命名空間 URI 關聯。 目標命名空間 URI 可指定為 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法的參數，或如果未指定任何目標命名空間，則 <xref:System.Xml.Schema.XmlSchemaSet> 會使用結構描述中定義的目標命名空間。  
  
 使用 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 屬性，可從 <xref:System.Xml.Schema.XmlSchemaSet> 擷取結構描述。 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 屬性可讓您重複處理 <xref:System.Xml.Schema.XmlSchema> 中包含的 <xref:System.Xml.Schema.XmlSchemaSet> 物件。 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 屬性會傳回 <xref:System.Xml.Schema.XmlSchema> 中包含的所有 <xref:System.Xml.Schema.XmlSchemaSet> 物件，或如果給定目標命名空間參數，則會傳回屬於目標命名空間的所有 <xref:System.Xml.Schema.XmlSchema> 物件。 如果將 `null` 指定為目標命名空間參數，則 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 屬性會傳回所有結構描述但無命名空間。  
  
 下列範例會將 `books.xsd` 命名空間中的 `http://www.contoso.com/books` 結構描述加入至 <xref:System.Xml.Schema.XmlSchemaSet>，從 `http://www.contoso.com/books` 擷取所有屬於 <xref:System.Xml.Schema.XmlSchemaSet> 命名空間的結構描述，然後將那些結構描述寫入 <xref:System.Console>。  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 如需在 <xref:System.Xml.Schema.XmlSchemaSet> 物件中加入及擷取結構描述的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法及 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 屬性參考文件。  
  
## <a name="compiling-schemas"></a>編譯結構描述  
 透過 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法，可將 <xref:System.Xml.Schema.XmlSchemaSet> 中的結構描述編譯成一個邏輯結構描述。  
  
> [!NOTE]
>  不同於過時的 <xref:System.Xml.Schema.XmlSchemaCollection> 類別，當呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法時，不會編譯結構描述。  
  
 如果 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法執行成功，則 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 屬性會設為 `true`。  
  
> [!NOTE]
>  如果結構描述是在 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 時編輯的，則 <xref:System.Xml.Schema.XmlSchemaSet> 屬性不受影響。 也不會追蹤 <xref:System.Xml.Schema.XmlSchemaSet> 中個別結構描述的更新。 因此，即使 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 中的其中一個結構描述已變更，只要未在 `true` 中加入或移除結構描述，<xref:System.Xml.Schema.XmlSchemaSet> 屬性就可為 <xref:System.Xml.Schema.XmlSchemaSet>。  
  
 下列範例會將 `books.xsd` 檔案加入至 <xref:System.Xml.Schema.XmlSchemaSet>，然後呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法。  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 如需編譯 <xref:System.Xml.Schema.XmlSchemaSet> 中結構描述的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法參考文件。  
  
## <a name="reprocessing-schemas"></a>重新處理結構描述  
 當呼叫 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法時，重新處理 <xref:System.Xml.Schema.XmlSchemaSet> 中的結構描述會執行對結構描述執行的所有前置處理步驟。 如果 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 方法呼叫成功，則 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 屬性會設為 `false`。  
  
 在 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 執行編譯之後，如果已修改 <xref:System.Xml.Schema.XmlSchemaSet> 中的結構描述，則應使用 <xref:System.Xml.Schema.XmlSchemaSet> 方法。  
  
 下列範例說明如何使用 <xref:System.Xml.Schema.XmlSchemaSet> 方法重新處理加入至 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 的結構描述。 在使用 <xref:System.Xml.Schema.XmlSchemaSet> 方法編譯 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>，並已修改加入至 <xref:System.Xml.Schema.XmlSchemaSet> 的結構描述之後，<xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 屬性會設為 `true` (即使已修改 <xref:System.Xml.Schema.XmlSchemaSet> 中的結構描述)。 呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 方法會執行 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法所執行的所有前置處理，並將 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 屬性設為 `false`。  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 如需重新處理 <xref:System.Xml.Schema.XmlSchemaSet> 中結構描述的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 方法參考文件。  
  
## <a name="checking-for-a-schema"></a>檢查結構描述  
 您可以使用 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法，檢查結構描述是否包含在 <xref:System.Xml.Schema.XmlSchemaSet> 中。 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> 方法允許檢查目標命名空間或 <xref:System.Xml.Schema.XmlSchema> 物件。 如果結構描述包含在 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> 中，則在這兩種情況下，`true` 方法都會傳回 <xref:System.Xml.Schema.XmlSchemaSet>；否則，傳回 `false`。  
  
 如需檢查結構描述的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> 方法參考文件。  
  
## <a name="removing-schemas"></a>移除結構描述  
 使用 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> 及 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> 方法，可將結構描述從 <xref:System.Xml.Schema.XmlSchemaSet> 中移除。 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> 方法會從 <xref:System.Xml.Schema.XmlSchemaSet> 移除指定的結構描述，而 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> 方法會移除指定的結構描述及其從 <xref:System.Xml.Schema.XmlSchemaSet> 匯入的所有結構描述。  
  
 下列範例說明如何將多個結構描述加入至 <xref:System.Xml.Schema.XmlSchemaSet>，然後使用 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> 方法移除其中一個結構描述及其匯入的所有結構描述。  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 如需從 <xref:System.Xml.Schema.XmlSchemaSet> 移除結構描述的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> 及 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> 方法參考文件。  
  
## <a name="schema-resolution-and-xsimport"></a>結構描述解析及 xs:import  
 下列範例說明當 <xref:System.Xml.Schema.XmlSchemaSet> 中存在某個指定命名空間的多個結構描述時，匯入結構描述的 <xref:System.Xml.Schema.XmlSchemaSet> 行為。  
  
 例如，設想一個 <xref:System.Xml.Schema.XmlSchemaSet>，假設其中有 `http://www.contoso.com` 命名空間的多個結構描述。 具有下列 `xs:import` 指示詞的結構描述會加入至 <xref:System.Xml.Schema.XmlSchemaSet>。  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet> 會嘗試匯入 `http://www.contoso.com` 命名空間的結構描述，方法是從 `http://www.contoso.com/schema.xsd` URL 將其載入。 即使在 `http://www.contoso.com` 中存在 <xref:System.Xml.Schema.XmlSchemaSet> 命名空間的其他結構描述文件，也只有在結構描述文件中宣告的結構描述宣告及型別才可在匯入結構描述中使用。 如果在 `schema.xsd` URL 處找不到 `http://www.contoso.com/schema.xsd` 檔案，則不會將 `http://www.contoso.com` 命名空間的任何結構描述匯入到匯入結構描述中。  
  
## <a name="validating-xml-documents"></a>驗證 XML 文件  
 您可根據 <xref:System.Xml.Schema.XmlSchemaSet> 中的結構描述來驗證 XML 文件。 驗證 XML 文件的方法是將結構描述加入至 <xref:System.Xml.XmlReaderSettings> 物件的 <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> 屬性，或將 <xref:System.Xml.Schema.XmlSchemaSet> 加入至 <xref:System.Xml.XmlReaderSettings> 物件的 <xref:System.Xml.XmlReaderSettings.Schemas%2A> 屬性。 然後，<xref:System.Xml.XmlReaderSettings> 類別的 <xref:System.Xml.XmlReader.Create%2A> 方法會使用 <xref:System.Xml.XmlReader> 物件來建立 <xref:System.Xml.XmlReader> 物件並驗證 XML 文件。  
  
 如需有關使用 <xref:System.Xml.Schema.XmlSchemaSet> 驗證 XML 文件的詳細資訊，請參閱 [使用 XmlSchemaSet 驗證 XML 結構描述 (XSD)](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>  
 [XmlSchemaSet 作為結構描述快取](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [使用 XmlSchemaSet 驗證 XML 結構描述 (XSD)](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
