---
title: 如何使用 XSD 進行驗證-LINQ to XML
description: 您可以使用 System.Xml 中的擴充方法。針對 XML 架構定義語言驗證 XML 樹狀結構的架構命名空間 (XSD) 檔。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 275a49658ddf2524530949929a7a5f04515a8493
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552776"
---
# <a name="how-to-validate-using-xsd-linq-to-xml"></a><span data-ttu-id="f35cf-103">如何使用 XSD 驗證 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f35cf-103">How to validate using XSD (LINQ to XML)</span></span>

<span data-ttu-id="f35cf-104"><xref:System.Xml.Schema> 命名空間包含的擴充方法可針對 XML 結構描述定義語言 (XSD) 檔，簡化 XML 樹狀結構的驗證。</span><span class="sxs-lookup"><span data-stu-id="f35cf-104">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="f35cf-105">如需詳細資訊，請參閱 <xref:System.Xml.Schema.Extensions.Validate%2A> 方法的文件。</span><span class="sxs-lookup"><span data-stu-id="f35cf-105">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>

## <a name="example-validate-xdocument-objects-against-an-xmlschemaset"></a><span data-ttu-id="f35cf-106">範例：針對 XmlSchemaSet 驗證 XDocument 物件</span><span class="sxs-lookup"><span data-stu-id="f35cf-106">Example: Validate XDocument objects against an XmlSchemaSet</span></span>

<span data-ttu-id="f35cf-107">下列範例會建立 <xref:System.Xml.Schema.XmlSchemaSet>，然後針對結構描述設定驗證兩個 <xref:System.Xml.Linq.XDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="f35cf-107">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="f35cf-108">其中一個檔是有效的，另一個則不是。</span><span class="sxs-lookup"><span data-stu-id="f35cf-108">One of the documents is valid, the other isn't.</span></span>

```csharp
string xsdMarkup =
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>
       <xsd:element name='Root'>
        <xsd:complexType>
         <xsd:sequence>
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>
         </xsd:sequence>
        </xsd:complexType>
       </xsd:element>
      </xsd:schema>";
XmlSchemaSet schemas = new XmlSchemaSet();
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));

XDocument doc1 = new XDocument(
    new XElement("Root",
        new XElement("Child1", "content1"),
        new XElement("Child2", "content1")
    )
);

XDocument doc2 = new XDocument(
    new XElement("Root",
        new XElement("Child1", "content1"),
        new XElement("Child3", "content1")
    )
);

Console.WriteLine("Validating doc1");
bool errors = false;
doc1.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");

Console.WriteLine();
Console.WriteLine("Validating doc2");
errors = false;
doc2.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");
```

```vb
Dim errors As Boolean = False

Private Sub XSDErrors(ByVal o As Object, ByVal e As ValidationEventArgs)
    Console.WriteLine("{0}", e.Message)
    errors = True
End Sub

Sub Main()
    Dim xsdMarkup As XElement = _
        <xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>
            <xsd:element name='Root'>
                <xsd:complexType>
                    <xsd:sequence>
                        <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>
                        <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>
                    </xsd:sequence>
                </xsd:complexType>
            </xsd:element>
        </xsd:schema>
    Dim schemas As XmlSchemaSet = New XmlSchemaSet()
    schemas.Add("", xsdMarkup.CreateReader)

    Dim doc1 As XDocument = _
        <?xml version='1.0'?>
        <Root>
            <Child1>content1</Child1>
            <Child2>content1</Child2>
        </Root>

    Dim doc2 As XDocument = _
        <?xml version='1.0'?>
        <Root>
            <Child1>content1</Child1>
            <Child3>content1</Child3>
        </Root>

    Console.WriteLine("Validating doc1")
    errors = False
    doc1.Validate(schemas, AddressOf XSDErrors)
    Console.WriteLine("doc1 {0}", IIf(errors = True, "did not validate", "validated"))

    Console.WriteLine()
    Console.WriteLine("Validating doc2")
    errors = False
    doc2.Validate(schemas, AddressOf XSDErrors)
    Console.WriteLine("doc2 {0}", IIf(errors = True, "did not validate", "validated"))
End Sub
```

<span data-ttu-id="f35cf-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f35cf-109">This example produces the following output:</span></span>

```output
Validating doc1
doc1 validated

Validating doc2
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.
doc2 did not validate
```

## <a name="example-validate-an-xml-document-from-a-file-against-a-schema-from-a-file"></a><span data-ttu-id="f35cf-110">範例：根據檔案中的架構驗證 XML 檔</span><span class="sxs-lookup"><span data-stu-id="f35cf-110">Example: Validate an XML document from a file against a schema from a file</span></span>

<span data-ttu-id="f35cf-111">下列範例會根據範例 XSD 檔案中的架構，驗證 XML [檔：](sample-xml-file-customers-orders.md) 客戶和訂單是否有效 [：客戶和訂單](sample-xsd-file-customers-orders.md)。</span><span class="sxs-lookup"><span data-stu-id="f35cf-111">The following example validates that the XML document from [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md) is valid per the schema from [Sample XSD file: Customers and orders](sample-xsd-file-customers-orders.md).</span></span> <span data-ttu-id="f35cf-112">接著，它會修改 XML 來源文件。</span><span class="sxs-lookup"><span data-stu-id="f35cf-112">It then modifies the source XML document.</span></span> <span data-ttu-id="f35cf-113">它會變更第一個客戶上的 `CustomerID` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f35cf-113">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="f35cf-114">變更之後，訂單會參考不存在的客戶，因此 XML 檔將不會再進行驗證。</span><span class="sxs-lookup"><span data-stu-id="f35cf-114">After the change, orders will then refer to a customer that doesn't exist, so the XML document will no longer validate.</span></span>

```csharp
XmlSchemaSet schemas = new XmlSchemaSet();
schemas.Add("", "CustomersOrders.xsd");

Console.WriteLine("Attempting to validate");
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");
bool errors = false;
custOrdDoc.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");

Console.WriteLine();
// Modify the source document so that it won't validate.
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";
Console.WriteLine("Attempting to validate after modification");
errors = false;
custOrdDoc.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");
```

```vb
Dim errors As Boolean = False

Private Sub XSDErrors(ByVal o As Object, ByVal e As ValidationEventArgs)
    Console.WriteLine("{0}", e.Message)
    errors = True
End Sub

Sub Main()
    Dim schemas As XmlSchemaSet = New XmlSchemaSet()
    schemas.Add("", "CustomersOrders.xsd")

    Console.WriteLine("Attempting to validate")
    Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")
    errors = False
    custOrdDoc.Validate(schemas, AddressOf XSDErrors)
    Console.WriteLine("custOrdDoc {0}", IIf(errors, "did not validate", "validated"))

    Console.WriteLine()
    ' Modify the source document so that it won't validate.
    custOrdDoc.<Root>.<Orders>.<Order>.<CustomerID>(0).Value = "AAAAA"
    Console.WriteLine("Attempting to validate after modification")
    errors = False
    custOrdDoc.Validate(schemas, AddressOf XSDErrors)
    Console.WriteLine("custOrdDoc {0}", IIf(errors, "did not validate", "validated"))
End Sub
```

<span data-ttu-id="f35cf-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f35cf-115">This example produces the following output:</span></span>

```output
Attempting to validate
custOrdDoc validated

Attempting to validate after modification
The key sequence 'AAAAA' in Keyref fails to refer to some key.
custOrdDoc did not validate
```

## <a name="see-also"></a><span data-ttu-id="f35cf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f35cf-116">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f35cf-117">XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="f35cf-117">XML trees</span></span>](functional-construction.md)
