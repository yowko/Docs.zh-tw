---
title: HOW TO：限定 XML 元素和 XML 屬性名稱
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 95b99bb093282352b6f8e2b9f04cba773e64259d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a>HOW TO：限定 XML 元素和 XML 屬性名稱
[程式碼範例](#cpconworkingwithxmlnamespacesanchor1)  
  
 <xref:System.Xml.Serialization.XmlSerializerNamespaces> 類別執行個體所包含的 XML 命名空間，必須符合全球資訊網協會 (www.w3.org) 的＜Namespaces in XML＞規格。  
  
 XML 命名空間提供限定 XML 文件中 XML 項目和 XML 屬性名稱的方法。 限定名稱 (Qualified Name) 是由前置詞和本機名稱所組成，並以半形冒號 (:) 隔開。 前置詞的作用只是個替代符號 (Placeholder)，它會對應到指定命名空間的 URI。 通用管理的 URI 命名空間和本機名稱的組合會產生保證是通用唯一的名稱。  
  
 藉由建立 `XmlSerializerNamespaces` 執行個體以及將命名空間配對加入物件中，您可指定 XML 文件使用的前置詞。  
  
### <a name="to-create-qualified-names-in-an-xml-document"></a>若要在 XML 文件中建立限定名稱  
  
1.  建立 `XmlSerializerNamespaces` 類別的執行個體。  
  
2.  加入所有前置詞與命名空間配對至 `XmlSerializerNamespaces`。  
  
3.  套用適當的 `System.Xml.Serialization` 屬性至 <xref:System.Xml.Serialization.XmlSerializer> 將要序列化至 XML 文件的每個成員或類別。  
  
     可用的屬性為：<xref:System.Xml.Serialization.XmlAnyElementAttribute>、<xref:System.Xml.Serialization.XmlArrayAttribute>、<xref:System.Xml.Serialization.XmlArrayItemAttribute>、<xref:System.Xml.Serialization.XmlAttributeAttribute>、<xref:System.Xml.Serialization.XmlElementAttribute>、<xref:System.Xml.Serialization.XmlRootAttribute> 與 <xref:System.Xml.Serialization.XmlTypeAttribute>。  
  
4.  將每個屬性 (Attribute) 的 `Namespace` 屬性 (Property) 設定為 `XmlSerializerNamespaces` 的其中一個命名空間值。  
  
5.  傳遞 `XmlSerializerNamespaces` 至 `Serialize` 的 `XmlSerializer` 方法。  
  
## <a name="example"></a>範例  
 下列範例建立 `XmlSerializerNamespaces`，並在物件加入兩個前置詞和命名空間配對。 程式碼建立用來系列化 `XmlSerializer` 類別執行個體的 `Books`。 程式碼以 `Serialize``XmlSerializerNamespaces`呼叫  方法，讓 XML 能包含有前置詞的命名空間。  
  
```vb  
Option Explicit   
public class Price  
{  
    [XmlAttribute(Namespace = "http://www.cpandl.com")]  
    public string currency;  
    [XmlElement(Namespace = "http://www.cohowinery.com")]  
    public decimal price;  
}  
  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Serialization  
  
Public Class Run  
  
    Public Shared Sub Main()  
        Dim test As New Run()  
        test.SerializeObject("XmlNamespaces.xml")  
    End Sub 'Main  
  
    Public Sub SerializeObject(filename As String)  
        Dim mySerializer As New XmlSerializer(GetType(Books))  
        ' Writing a file requires a TextWriter.  
        Dim myWriter As New StreamWriter(filename)  
  
        ' Creates an XmlSerializerNamespaces and adds two  
        ' prefix-namespace pairs.   
        Dim myNamespaces As New XmlSerializerNamespaces()  
        myNamespaces.Add("books", "http://www.cpandl.com")  
        myNamespaces.Add("money", "http://www.cohowinery.com")  
  
        ' Creates a Book.  
        Dim myBook As New Book()  
        myBook.TITLE = "A Book Title"  
        Dim myPrice As New Price()  
        myPrice.price = CDec(9.95)  
        myPrice.currency = "US Dollar"  
        myBook.PRICE = myPrice  
        Dim myBooks As New Books()  
        myBooks.Book = myBook  
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)  
        myWriter.Close()  
    End Sub  
End Class  
  
Public Class Books  
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _  
    Public Book As Book  
End Class 'Books  
  
<XmlType([Namespace] := "http://www.cpandl.com")> _  
Public Class Book  
  
    <XmlElement([Namespace] := "http://www.cpandl.com")> _  
    Public TITLE As String  
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _  
    Public PRICE As Price  
End Class  
  
Public Class Price  
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _  
    Public currency As String  
    Public <XmlElement([Namespace] := "http://www.cohowinery.com")> _  
        price As Decimal  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Serialization;  
  
public class Run  
{  
    public static void Main()  
    {  
        Run test = new Run();  
        test.SerializeObject("XmlNamespaces.xml");  
    }  
    public void SerializeObject(string filename)  
    {  
        XmlSerializer mySerializer = new XmlSerializer(typeof(Books));  
        // Writing a file requires a TextWriter.  
        TextWriter myWriter = new StreamWriter(filename);  
  
        // Creates an XmlSerializerNamespaces and adds two  
        // prefix-namespace pairs.  
        XmlSerializerNamespaces myNamespaces =   
        new XmlSerializerNamespaces();  
        myNamespaces.Add("books", "http://www.cpandl.com");  
        myNamespaces.Add("money", "http://www.cohowinery.com");  
  
        // Creates a Book.  
        Book myBook = new Book();  
        myBook.TITLE = "A Book Title";  
        Price myPrice = new Price();  
        myPrice.price = (decimal) 9.95;  
        myPrice.currency = "US Dollar";  
        myBook.PRICE = myPrice;  
        Books myBooks = new Books();  
        myBooks.Book = myBook;  
        mySerializer.Serialize(myWriter,myBooks,myNamespaces);  
        myWriter.Close();  
    }  
}  
  
public class Books  
{  
    [XmlElement(Namespace = "http://www.cohowinery.com")]  
    public Book Book;  
}  
  
[XmlType(Namespace ="http://www.cpandl.com")]  
public class Book  
{  
    [XmlElement(Namespace = "http://www.cpandl.com")]  
    public string TITLE;  
    [XmlElement(Namespace ="http://www.cohowinery.com")]  
    public Price PRICE;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [XML 結構描述定義工具和 XML 序列化](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 [XML 序列化簡介](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [XmlSerializer 類別](xref:System.Xml.Serialization.XmlSerializer)  
 [可控制 XML 序列化的屬性](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 [如何：指定 XML 資料流的替代元素名稱](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 [如何：序列化物件](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [如何：還原序列化物件](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
