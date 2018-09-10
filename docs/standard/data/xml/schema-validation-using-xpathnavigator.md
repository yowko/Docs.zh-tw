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
ms.openlocfilehash: d2b04006c46edb29fd4fe05e63224220ed1876af
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085271"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="baaa2-102">使用 XPathNavigator 進行結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="baaa2-102">Schema Validation using XPathNavigator</span></span>
<span data-ttu-id="baaa2-103">您可以使用 <xref:System.Xml.XmlDocument> 類別，透過兩種方式驗證 <xref:System.Xml.XmlDocument> 物件中包含的 XML 內容。</span><span class="sxs-lookup"><span data-stu-id="baaa2-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="baaa2-104">第一種方式是使用驗證 <xref:System.Xml.XmlReader> 物件來驗證 XML 內容，第二種方式是使用 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法。</span><span class="sxs-lookup"><span data-stu-id="baaa2-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="baaa2-105">此外，您也可以使用 <xref:System.Xml.XPath.XPathDocument> 類別，執行 XML 內容的唯讀驗證。</span><span class="sxs-lookup"><span data-stu-id="baaa2-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="baaa2-106">驗證 XML 資料</span><span class="sxs-lookup"><span data-stu-id="baaa2-106">Validating XML Data</span></span>  
 <span data-ttu-id="baaa2-107">依預設，<xref:System.Xml.XmlDocument> 類別不會使用 DTD 或 XML 結構描述定義語言 (XSD) 結構描述驗證，來驗證 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="baaa2-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="baaa2-108">它只會驗證 XML 文件的格式是否正確。</span><span class="sxs-lookup"><span data-stu-id="baaa2-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="baaa2-109">第一種驗證 XML 文件的方式是使用驗證 <xref:System.Xml.XmlDocument> 物件，在將文件載入至 <xref:System.Xml.XmlReader> 物件時進行驗證。</span><span class="sxs-lookup"><span data-stu-id="baaa2-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="baaa2-110">第二種方式是使用 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法，驗證先前不具型別的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="baaa2-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="baaa2-111">在這兩種情況下，都可以使用 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法，重新驗證已驗證 XML 文件的變更。</span><span class="sxs-lookup"><span data-stu-id="baaa2-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="baaa2-112">載入文件時進行驗證</span><span class="sxs-lookup"><span data-stu-id="baaa2-112">Validating a Document as it is Loaded</span></span>  
 <span data-ttu-id="baaa2-113">驗證 <xref:System.Xml.XmlReader> 物件可透過將 <xref:System.Xml.XmlReaderSettings> 物件傳遞至 <xref:System.Xml.XmlReader.Create%2A> 類別的 <xref:System.Xml.XmlReader> 方法 (其將 <xref:System.Xml.XmlReaderSettings> 物件視為參數) 來建立。</span><span class="sxs-lookup"><span data-stu-id="baaa2-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="baaa2-114">做為參數傳遞之 <xref:System.Xml.XmlReaderSettings> 物件具有設為 <xref:System.Xml.XmlReaderSettings.ValidationType%2A>的 `Schema` 屬性，並且 <xref:System.Xml.XmlDocument> 物件中包含之 XML 文件的 XML 結構描述會加入其 <xref:System.Xml.XmlReaderSettings.Schemas%2A> 屬性中。</span><span class="sxs-lookup"><span data-stu-id="baaa2-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="baaa2-115">然後，驗證 <xref:System.Xml.XmlReader> 物件即可用來建立 <xref:System.Xml.XmlDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="baaa2-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="baaa2-116">下列範例透過使用驗證 `contosoBooks.xml` 物件建立 <xref:System.Xml.XmlDocument> 物件，以在將 <xref:System.Xml.XmlDocument> 檔案載入至 <xref:System.Xml.XmlReader> 物件時對其進行驗證。</span><span class="sxs-lookup"><span data-stu-id="baaa2-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="baaa2-117">因為根據該 XML 文件的結構描述的內容，它是有效的，所以不會產生結構描述驗證錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="baaa2-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
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
  
 <span data-ttu-id="baaa2-118">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="baaa2-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="baaa2-119">該範例還採用 `contosoBooks.xsd` 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="baaa2-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="baaa2-120">在上述範例中，如果有任何屬性或項目類型不符合驗證結構描述內指定的對應型別，則在呼叫 <xref:System.Xml.Schema.XmlSchemaValidationException> 時將會擲回 <xref:System.Xml.XmlDocument.Load%2A>。</span><span class="sxs-lookup"><span data-stu-id="baaa2-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="baaa2-121">如果在驗證 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> 上設定了 <xref:System.Xml.XmlReader>，則每當遇到無效的型別時，都將呼叫 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="baaa2-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="baaa2-122">當 <xref:System.Xml.Schema.XmlSchemaException> 存取將 <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> 設定為 `invalid` 的屬性或項目時，將會擲回 <xref:System.Xml.XPath.XPathNavigator>。</span><span class="sxs-lookup"><span data-stu-id="baaa2-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="baaa2-123"><xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> 屬性可用來決定當使用 <xref:System.Xml.XPath.XPathNavigator> 存取屬性或項目時，個別的屬性或項目是否有效。</span><span class="sxs-lookup"><span data-stu-id="baaa2-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="baaa2-124">當 XML 文件載入至具有可定義預設值之關聯結構描述的 <xref:System.Xml.XmlDocument> 物件時，<xref:System.Xml.XmlDocument> 會處理這些預設值，就好像它們是出現在 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="baaa2-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="baaa2-125">這表示針對結構描述中預設的項目，即使在 XML 文件中將其做為空白項目寫入，<xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> 屬性永遠會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="baaa2-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="baaa2-126">使用驗證方法驗證文件</span><span class="sxs-lookup"><span data-stu-id="baaa2-126">Validating a Document using the Validate Method</span></span>  
 <span data-ttu-id="baaa2-127"><xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法會根據 <xref:System.Xml.XmlDocument> 物件之 <xref:System.Xml.XmlDocument> 屬性中指定的結構描述，驗證 <xref:System.Xml.XmlDocument.Schemas%2A> 物件中包含的 XML 文件，並執行資訊集增加。</span><span class="sxs-lookup"><span data-stu-id="baaa2-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="baaa2-128">其結果是以具型別文件取代 <xref:System.Xml.XmlDocument> 物件中先前不具型別的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="baaa2-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="baaa2-129"><xref:System.Xml.XmlDocument> 物件會使用做為參數傳遞至 <xref:System.Xml.Schema.ValidationEventHandler> 方法的 <xref:System.Xml.XmlDocument.Validate%2A> 委派，報告結構描述驗證錯誤及警告。</span><span class="sxs-lookup"><span data-stu-id="baaa2-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="baaa2-130">下列範例根據 `contosoBooks.xml` 物件之 <xref:System.Xml.XmlDocument> 屬性中包含的 `contosoBooks.xsd` 結構描述，驗證 <xref:System.Xml.XmlDocument> 物件中包含的 <xref:System.Xml.XmlDocument.Schemas%2A> 檔案。</span><span class="sxs-lookup"><span data-stu-id="baaa2-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="baaa2-131">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="baaa2-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="baaa2-132">該範例還採用 `contosoBooks.xsd` 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="baaa2-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="baaa2-133">驗證修改</span><span class="sxs-lookup"><span data-stu-id="baaa2-133">Validating Modifications</span></span>  
 <span data-ttu-id="baaa2-134">對 XML 文件進行修改之後，您可以使用 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法，根據 XML 文件的結構描述驗證修改。</span><span class="sxs-lookup"><span data-stu-id="baaa2-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="baaa2-135">下列範例透過使用驗證 `contosoBooks.xml` 物件建立 <xref:System.Xml.XmlDocument> 物件，以在將 <xref:System.Xml.XmlDocument> 檔案載入至 <xref:System.Xml.XmlReader> 物件時對其進行驗證。</span><span class="sxs-lookup"><span data-stu-id="baaa2-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="baaa2-136">XML 文件在載入時順利完成驗證，沒有產生任何結構描述驗證錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="baaa2-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="baaa2-137">然後，根據 `contosoBooks.xsd` 結構描述，本範例對 XML 文件進行兩處無效的修改。</span><span class="sxs-lookup"><span data-stu-id="baaa2-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="baaa2-138">第一處修改是插入導致結構描述驗證錯誤的無效項目子系，而第二處修改則是將具型別節點的值，設為對於節點型別而言無效的值，從而導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="baaa2-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
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
  
 <span data-ttu-id="baaa2-139">範例將 `contosoBooks.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="baaa2-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="baaa2-140">該範例還採用 `contosoBooks.xsd` 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="baaa2-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="baaa2-141">在上述範例中，對 <xref:System.Xml.XmlDocument> 物件中包含的 XML 文件進行兩處修改。</span><span class="sxs-lookup"><span data-stu-id="baaa2-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="baaa2-142">在載入 XML 文件時，所發生的任何結構描述驗證錯誤都會由驗證事件處理常式方法進行處理，並寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="baaa2-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="baaa2-143">在此範例中，載入 XML 文件後發生了驗證錯誤，並且會透過 <xref:System.Xml.XmlDocument.Validate%2A> 類別的 <xref:System.Xml.XmlDocument> 方法來發現錯誤。</span><span class="sxs-lookup"><span data-stu-id="baaa2-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="baaa2-144">使用 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 方法進行的修改導致 <xref:System.InvalidCastException>，因為根據節點的結構描述型別，新值是無效的。</span><span class="sxs-lookup"><span data-stu-id="baaa2-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="baaa2-145">如需使用 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法修改值的詳細資訊，請參閱[使用 XPathNavigator 修改 XML 資料](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)主題。</span><span class="sxs-lookup"><span data-stu-id="baaa2-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="baaa2-146">唯讀驗證</span><span class="sxs-lookup"><span data-stu-id="baaa2-146">Read-Only Validation</span></span>  
 <span data-ttu-id="baaa2-147"><xref:System.Xml.XPath.XPathDocument> 類別是 XML 文件之唯讀的記憶體中表示。</span><span class="sxs-lookup"><span data-stu-id="baaa2-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="baaa2-148"><xref:System.Xml.XPath.XPathDocument> 類別及 <xref:System.Xml.XmlDocument> 類別都可建立 <xref:System.Xml.XPath.XPathNavigator> 物件，以巡覽及編輯 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="baaa2-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="baaa2-149">因為 <xref:System.Xml.XPath.XPathDocument> 類別是唯讀類別，所以從 <xref:System.Xml.XPath.XPathNavigator> 物件傳回的 <xref:System.Xml.XPath.XPathDocument> 物件無法編輯 <xref:System.Xml.XPath.XPathDocument> 物件中包含的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="baaa2-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="baaa2-150">在驗證時，您可以如本主題中先前所述，使用與驗證 <xref:System.Xml.XPath.XPathDocument> 物件建立 <xref:System.Xml.XmlDocument> 物件相同的方式，建立 <xref:System.Xml.XmlReader> 物件。</span><span class="sxs-lookup"><span data-stu-id="baaa2-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="baaa2-151"><xref:System.Xml.XPath.XPathDocument> 物件會在載入 XML 文件時對其進行驗證，但是因為無法編輯 <xref:System.Xml.XPath.XPathDocument> 物件中的 XML 資料，所以您無法重新驗證 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="baaa2-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="baaa2-152">如需有關唯讀與可編輯 <xref:System.Xml.XPath.XPathNavigator> 物件的詳細資訊，請參閱[使用 XPathDocument 和 XmlDocument 讀取 XML 資料](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)主題。</span><span class="sxs-lookup"><span data-stu-id="baaa2-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baaa2-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baaa2-153">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="baaa2-154">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="baaa2-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="baaa2-155">使用 XPathDocument 及 XmlDocument 讀取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="baaa2-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
- [<span data-ttu-id="baaa2-156">使用 XPathNavigator 選取、評估及比對 XML 資料</span><span class="sxs-lookup"><span data-stu-id="baaa2-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="baaa2-157">使用 XPathNavigator 存取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="baaa2-157">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="baaa2-158">使用 XPathNavigator 編輯 XML 資料</span><span class="sxs-lookup"><span data-stu-id="baaa2-158">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
