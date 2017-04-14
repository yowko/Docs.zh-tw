---
title: "HOW TO：限定 XML 項目和 XML 屬性名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "限定 XML 項目"
  - "限定 XML 名稱"
  - "XML 命名空間, 限定其項目與名稱"
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# HOW TO：限定 XML 項目和 XML 屬性名稱
[程式碼範例](#cpconworkingwithxmlnamespacesanchor1)  
  
 [XmlSerializerNamespaces](frlrfSystemXmlSerializationXmlSerializerNamespacesClassTopic) 類別執行個體所包含的 XML 命名空間，必須符合全球資訊網協會 \(www.w3.org\) 的＜Namespaces in XML＞規格。  
  
 XML 命名空間提供限定 XML 文件中 XML 項目和 XML 屬性名稱的方法。限定名稱 \(Qualified Name\) 是由前置詞和本機名稱所組成，並以半形冒號 \(:\) 隔開。前置詞的作用只是個替代符號 \(Placeholder\)，它會對應到指定命名空間的 URI。通用管理的 URI 命名空間和本機名稱的組合會產生保證是通用唯一的名稱。  
  
 藉由建立 **XmlSerializerNamespaces** 執行個體以及將命名空間配對加入物件中，您可指定 XML 文件使用的前置詞。  
  
### 若要在 XML 文件中建立限定名稱  
  
1.  建立 **XmlSerializerNamespaces** 類別的執行個體。  
  
2.  加入所有前置詞與命名空間配對至 **XmlSerializerNamespaces**。  
  
3.  套用適當的 **System.Xml.Serialization** 屬性至 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) 將要序列化至 XML 文件的每個成員或類別。  
  
     可用的屬性為：[XmlAnyElementAttribute](frlrfSystemXmlSerializationXmlAnyElementAttributeClassTopic)、[XmlArrayAttribute](frlrfSystemXmlSerializationXmlArrayAttributeClassTopic)、[XmlArrayItemAttribute](frlrfSystemXmlSerializationXmlArrayItemAttributeClassTopic)、[XmlAttributeAttribute](frlrfSystemXmlSerializationXmlAttributeAttributeClassTopic)、[XmlElementAttribute](frlrfSystemXmlSerializationXmlElementAttributeClassTopic)、[XmlRootAttribute](frlrfSystemXmlSerializationXmlRootAttributeClassTopic) 與 [XmlTypeAttribute](frlrfSystemXmlSerializationXmlTypeAttributeClassTopic)。  
  
4.  將每個屬性 \(Attribute\) 的 **Namespace** 屬性 \(Property\) 設定為 **XmlSerializerNamespaces** 的其中一個命名空間值。  
  
5.  傳遞 **XmlSerializerNamespaces** 至 **XmlSerializer** 的 **Serialize** 方法。  
  
## 範例  
 下列範例建立 **XmlSerializerNamespaces**，並在物件加入兩個前置詞和命名空間配對。程式碼建立用來系列化 `Books` 類別執行個體的 **XmlSerializer**。程式碼以 **XmlSerializerNamespaces** 呼叫 **Serialize** 方法，讓 XML 能包含有前置詞的命名空間。  
  
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
  
## 請參閱  
 [XML 結構描述定義工具和 XML 序列化](../../../docs/framework/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)   
 [XML 序列化簡介](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [XmlSerializer Class](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [控制 XML 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-xml-serialization.md)   
 [XmlSerializerNamespaces Class](frlrfSystemXmlSerializationXmlSerializerNamespacesClassTopic)   
 [HOW TO：指定 XML 資料流的替代項目名稱](../../../docs/framework/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)   
 [HOW TO：序列化物件](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [HOW TO：還原序列化物件](../../../docs/framework/serialization/how-to-deserialize-an-object.md)