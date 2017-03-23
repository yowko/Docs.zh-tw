---
title: "如何︰ 使用 XSD (LINQ to XML) 進行驗證 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: a0fe88d4-4e77-49e7-90de-8953feeccc21
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c6df61013b0007e5943060f8926b21d189a01519
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-validate-using-xsd-linq-to-xml-visual-basic"></a>如何︰ 使用 XSD (LINQ to XML) 進行驗證 (Visual Basic)
<xref:System.Xml.Schema>命名空間包含擴充方法，可讓您輕鬆驗證對 XML 結構描述定義語言 (XSD) 檔案的 XML 樹狀結構。</xref:System.Xml.Schema> 如需詳細資訊，請參閱<xref:System.Xml.Schema.Extensions.Validate%2A>方法的文件。</xref:System.Xml.Schema.Extensions.Validate%2A>  
  
## <a name="example"></a>範例  
 下列範例會建立<xref:System.Xml.Schema.XmlSchemaSet>，然後驗證兩個<xref:System.Xml.Linq.XDocument>針對結構描述集合的物件。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Schema.XmlSchemaSet> 其中一個文件有效，另一個無效。  
  
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
  
 這個範例會產生下列輸出：  
  
```  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a>範例  
 下列範例將驗證的 XML 文件從[範例 XML 檔︰ 客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)根據從結構描述有效[範例 XSD 檔︰ 客戶和訂單](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md)。 接著，它會修改 XML 來源文件。 它會變更第一個客戶上的 `CustomerID` 屬性。 變更後，這些訂單將會參考不存在的客戶，因此 XML 文件將不再有效。  
  
 這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)。  
  
 這個範例會使用下列 XSD 結構描述︰[範例 XSD 檔︰ 客戶和訂單](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md)。  
  
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
  
 這個範例會產生下列輸出：  
  
```  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Schema.Extensions.Validate%2A></xref:System.Xml.Schema.Extensions.Validate%2A>   
 [建立 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
