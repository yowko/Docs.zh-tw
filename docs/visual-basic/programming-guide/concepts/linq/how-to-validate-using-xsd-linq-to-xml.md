---
title: HOW TO：使用 XSD (LINQ to XML) 進行驗證 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a0fe88d4-4e77-49e7-90de-8953feeccc21
ms.openlocfilehash: 9e4250ac1da4b25ce3f1644b38ff0e71693ecc57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691212"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-visual-basic"></a><span data-ttu-id="e3ab3-102">HOW TO：使用 XSD (LINQ to XML) 進行驗證 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3ab3-102">How to: Validate Using XSD (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="e3ab3-103"><xref:System.Xml.Schema> 命名空間包含的擴充方法可針對 XML 結構描述定義語言 (XSD) 檔，簡化 XML 樹狀結構的驗證。</span><span class="sxs-lookup"><span data-stu-id="e3ab3-103">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="e3ab3-104">如需詳細資訊，請參閱 <xref:System.Xml.Schema.Extensions.Validate%2A> 方法的文件。</span><span class="sxs-lookup"><span data-stu-id="e3ab3-104">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3ab3-105">範例</span><span class="sxs-lookup"><span data-stu-id="e3ab3-105">Example</span></span>  
 <span data-ttu-id="e3ab3-106">下列範例會建立 <xref:System.Xml.Schema.XmlSchemaSet>，然後針對結構描述設定驗證兩個 <xref:System.Xml.Linq.XDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="e3ab3-106">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="e3ab3-107">其中一個文件有效，另一個無效。</span><span class="sxs-lookup"><span data-stu-id="e3ab3-107">One of the documents is valid, the other is not.</span></span>  
  
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
  
 <span data-ttu-id="e3ab3-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e3ab3-108">This example produces the following output:</span></span>  
  
```  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="e3ab3-109">範例</span><span class="sxs-lookup"><span data-stu-id="e3ab3-109">Example</span></span>  
 <span data-ttu-id="e3ab3-110">下列範例可讓您驗證的 XML 文件從[範例 XML 檔：客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)根據從結構描述有效[範例 XSD 檔：客戶和訂單](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ab3-110">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) is valid per the schema from [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="e3ab3-111">接著，它會修改 XML 來源文件。</span><span class="sxs-lookup"><span data-stu-id="e3ab3-111">It then modifies the source XML document.</span></span> <span data-ttu-id="e3ab3-112">它會變更第一個客戶上的 `CustomerID` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e3ab3-112">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="e3ab3-113">變更後，這些訂單將會參考不存在的客戶，因此 XML 文件將不再有效。</span><span class="sxs-lookup"><span data-stu-id="e3ab3-113">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="e3ab3-114">此範例使用下列 XML 文件：[範例 XML 檔：客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ab3-114">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="e3ab3-115">此範例使用下列 XSD 結構描述：[範例 XSD 檔：客戶和訂單](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ab3-115">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span>  
  
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
    ' Modify the source document so that it will not validate.  
    custOrdDoc.<Root>.<Orders>.<Order>.<CustomerID>(0).Value = "AAAAA"  
    Console.WriteLine("Attempting to validate after modification")  
    errors = False  
    custOrdDoc.Validate(schemas, AddressOf XSDErrors)  
    Console.WriteLine("custOrdDoc {0}", IIf(errors, "did not validate", "validated"))  
End Sub  
```  
  
 <span data-ttu-id="e3ab3-116">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e3ab3-116">This example produces the following output:</span></span>  
  
```  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3ab3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3ab3-117">See also</span></span>
- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="e3ab3-118">建立 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3ab3-118">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
