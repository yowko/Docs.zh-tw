---
title: 使用 XPathNavigator 進行結構描述驗證
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0199efb172466305af22c4ade7c47115a5cefd8f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939611"
---
# <a name="schema-validation-using-xpathnavigator"></a>使用 XPathNavigator 進行結構描述驗證
您可以使用 <xref:System.Xml.XmlDocument> 類別，透過兩種方式驗證 <xref:System.Xml.XmlDocument> 物件中包含的 XML 內容。 第一種方式是使用驗證 <xref:System.Xml.XmlReader> 物件來驗證 XML 內容，第二種方式是使用 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法。 此外，您也可以使用 <xref:System.Xml.XPath.XPathDocument> 類別，執行 XML 內容的唯讀驗證。  
  
## <a name="validating-xml-data"></a>驗證 XML 資料  
 依預設，<xref:System.Xml.XmlDocument> 類別不會使用 DTD 或 XML 結構描述定義語言 (XSD) 結構描述驗證，來驗證 XML 文件。 它只會驗證 XML 文件的格式是否正確。  
  
 第一種驗證 XML 文件的方式是使用驗證 <xref:System.Xml.XmlDocument> 物件，在將文件載入至 <xref:System.Xml.XmlReader> 物件時進行驗證。 第二種方式是使用 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法，驗證先前不具型別的 XML 文件。 在這兩種情況下，都可以使用 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法，重新驗證已驗證 XML 文件的變更。  
  
### <a name="validating-a-document-as-it-is-loaded"></a>載入文件時進行驗證  
 驗證 <xref:System.Xml.XmlReader> 物件可透過將 <xref:System.Xml.XmlReaderSettings> 物件傳遞至 <xref:System.Xml.XmlReader.Create%2A> 類別的 <xref:System.Xml.XmlReader> 方法 (其將 <xref:System.Xml.XmlReaderSettings> 物件視為參數) 來建立。 做為參數傳遞之 <xref:System.Xml.XmlReaderSettings> 物件具有設為 <xref:System.Xml.XmlReaderSettings.ValidationType%2A>的 `Schema` 屬性，並且 <xref:System.Xml.XmlDocument> 物件中包含之 XML 文件的 XML 結構描述會加入其 <xref:System.Xml.XmlReaderSettings.Schemas%2A> 屬性中。 然後，驗證 <xref:System.Xml.XmlReader> 物件即可用來建立 <xref:System.Xml.XmlDocument> 物件。  
  
 下列範例透過使用驗證 `contosoBooks.xml` 物件建立 <xref:System.Xml.XmlDocument> 物件，以在將 <xref:System.Xml.XmlDocument> 檔案載入至 <xref:System.Xml.XmlReader> 物件時對其進行驗證。 因為根據該 XML 文件的結構描述的內容，它是有效的，所以不會產生結構描述驗證錯誤或警告。  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 範例將 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 該範例還採用 `contosoBooks.xsd` 做為輸入。  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 在上述範例中，如果有任何屬性或項目類型不符合驗證結構描述內指定的對應型別，則在呼叫 <xref:System.Xml.Schema.XmlSchemaValidationException> 時將會擲回 <xref:System.Xml.XmlDocument.Load%2A>。 如果在驗證 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> 上設定了 <xref:System.Xml.XmlReader>，則每當遇到無效的型別時，都將呼叫 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>。  
  
 當 <xref:System.Xml.Schema.XmlSchemaException> 存取將 <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> 設定為 `invalid` 的屬性或項目時，將會擲回 <xref:System.Xml.XPath.XPathNavigator>。  
  
 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> 屬性可用來決定當使用 <xref:System.Xml.XPath.XPathNavigator> 存取屬性或項目時，個別的屬性或項目是否有效。  
  
> [!NOTE]
> 當 XML 文件載入至具有可定義預設值之關聯結構描述的 <xref:System.Xml.XmlDocument> 物件時，<xref:System.Xml.XmlDocument> 會處理這些預設值，就好像它們是出現在 XML 文件中。 這表示針對結構描述中預設的項目，即使在 XML 文件中將其做為空白項目寫入，<xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> 屬性永遠會傳回 `false`。  
  
### <a name="validating-a-document-using-the-validate-method"></a>使用驗證方法驗證文件  
 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法會根據 <xref:System.Xml.XmlDocument> 物件之 <xref:System.Xml.XmlDocument> 屬性中指定的結構描述，驗證 <xref:System.Xml.XmlDocument.Schemas%2A> 物件中包含的 XML 文件，並執行資訊集增加。 其結果是以具型別文件取代 <xref:System.Xml.XmlDocument> 物件中先前不具型別的 XML 文件。  
  
 <xref:System.Xml.XmlDocument> 物件會使用做為參數傳遞至 <xref:System.Xml.Schema.ValidationEventHandler> 方法的 <xref:System.Xml.XmlDocument.Validate%2A> 委派，報告結構描述驗證錯誤及警告。  
  
 下列範例根據 `contosoBooks.xml` 物件之 <xref:System.Xml.XmlDocument> 屬性中包含的 `contosoBooks.xsd` 結構描述，驗證 <xref:System.Xml.XmlDocument> 物件中包含的 <xref:System.Xml.XmlDocument.Schemas%2A> 檔案。  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidateExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Dim document As XmlDocument = New XmlDocument()  
        document.Load("contosoBooks.xml")  
        Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
        Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
        document.Validate(validation)  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidateExample  
{  
    static void Main(string[] args)  
    {  
        XmlDocument document = new XmlDocument();  
        document.Load("contosoBooks.xml");  
        XPathNavigator navigator = document.CreateNavigator();  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
        ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
        document.Validate(validation);  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 範例將 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 該範例還採用 `contosoBooks.xsd` 做為輸入。  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>驗證修改  
 對 XML 文件進行修改之後，您可以使用 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法，根據 XML 文件的結構描述驗證修改。  
  
 下列範例透過使用驗證 `contosoBooks.xml` 物件建立 <xref:System.Xml.XmlDocument> 物件，以在將 <xref:System.Xml.XmlDocument> 檔案載入至 <xref:System.Xml.XmlReader> 物件時對其進行驗證。 XML 文件在載入時順利完成驗證，沒有產生任何結構描述驗證錯誤或警告。 然後，根據 `contosoBooks.xsd` 結構描述，本範例對 XML 文件進行兩處無效的修改。 第一處修改是插入導致結構描述驗證錯誤的無效項目子系，而第二處修改則是將具型別節點的值，設為對於節點型別而言無效的值，從而導致例外狀況。  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
            Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
            navigator.MoveToChild("book", "http://www.contoso.com/books")  
            navigator.MoveToChild("author", "http://www.contoso.com/books")  
  
            navigator.AppendChild("<title>Book Title</title>")  
  
            document.Validate(validation)  
  
            navigator.MoveToParent()  
            navigator.MoveToChild("price", "http://www.contoso.com/books")  
            navigator.SetTypedValue(DateTime.Now)  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
  
            ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
            navigator.MoveToChild("book", "http://www.contoso.com/books");  
            navigator.MoveToChild("author", "http://www.contoso.com/books");  
  
            navigator.AppendChild("<title>Book Title</title>");  
  
            document.Validate(validation);  
  
            navigator.MoveToParent();  
            navigator.MoveToChild("price", "http://www.contoso.com/books");  
            navigator.SetTypedValue(DateTime.Now);  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 範例將 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 該範例還採用 `contosoBooks.xsd` 做為輸入。  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 在上述範例中，對 <xref:System.Xml.XmlDocument> 物件中包含的 XML 文件進行兩處修改。 在載入 XML 文件時，所發生的任何結構描述驗證錯誤都會由驗證事件處理常式方法進行處理，並寫入主控台。  
  
 在此範例中，載入 XML 文件後發生了驗證錯誤，並且會透過 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法來發現錯誤。  
  
 使用 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 方法進行的修改導致 <xref:System.InvalidCastException>，因為根據節點的結構描述型別，新值是無效的。  
  
 如需使用 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法修改值的詳細資訊，請參閱[使用 XPathNavigator 修改 XML 資料](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)主題。  
  
### <a name="read-only-validation"></a>唯讀驗證  
 <xref:System.Xml.XPath.XPathDocument> 類別是 XML 文件之唯讀的記憶體中表示。 <xref:System.Xml.XPath.XPathDocument> 類別及 <xref:System.Xml.XmlDocument> 類別都可建立 <xref:System.Xml.XPath.XPathNavigator> 物件，以巡覽及編輯 XML 文件。 因為 <xref:System.Xml.XPath.XPathDocument> 類別是唯讀類別，所以從 <xref:System.Xml.XPath.XPathNavigator> 物件傳回的 <xref:System.Xml.XPath.XPathDocument> 物件無法編輯 <xref:System.Xml.XPath.XPathDocument> 物件中包含的 XML 文件。  
  
 在驗證時，您可以如本主題中先前所述，使用與驗證 <xref:System.Xml.XPath.XPathDocument> 物件建立 <xref:System.Xml.XmlDocument> 物件相同的方式，建立 <xref:System.Xml.XmlReader> 物件。 <xref:System.Xml.XPath.XPathDocument> 物件會在載入 XML 文件時對其進行驗證，但是因為無法編輯 <xref:System.Xml.XPath.XPathDocument> 物件中的 XML 資料，所以您無法重新驗證 XML 文件。  
  
 如需有關唯讀與可編輯 <xref:System.Xml.XPath.XPathNavigator> 物件的詳細資訊，請參閱[使用 XPathDocument 和 XmlDocument 讀取 XML 資料](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)主題。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [使用 XPathDocument 及 XmlDocument 讀取 XML 資料](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [使用 XPathNavigator 選取、評估及比對 XML 資料](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [使用 XPathNavigator 存取 XML 資料](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [使用 XPathNavigator 編輯 XML 資料](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
