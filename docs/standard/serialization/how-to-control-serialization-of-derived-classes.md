---
title: HOW TO：控制衍生類別的序列化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: caa92596-9e15-4d91-acbe-56911ef47a84
ms.openlocfilehash: 00eb4ba1f5f84c60f1ca51871f604b6ee27798c3
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002836"
---
# <a name="how-to-control-serialization-of-derived-classes"></a><span data-ttu-id="bf0ef-102">HOW TO：控制衍生類別的序列化</span><span class="sxs-lookup"><span data-stu-id="bf0ef-102">How to: Control Serialization of Derived Classes</span></span>
<span data-ttu-id="bf0ef-103">使用 **XmlElementAttribute** 屬性變更 XML 項目的名稱並非自訂物件序列化的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="bf0ef-103">Using the **XmlElementAttribute** attribute to change the name of an XML element is not the only way to customize object serialization.</span></span> <span data-ttu-id="bf0ef-104">您可從現有類別衍生以自訂化 XML 資料流並指示 <xref:System.Xml.Serialization.XmlSerializer> 執行個體如何序列化新類別。</span><span class="sxs-lookup"><span data-stu-id="bf0ef-104">You can also customize the XML stream by deriving from an existing class and instructing the <xref:System.Xml.Serialization.XmlSerializer> instance how to serialize the new class.</span></span>  
  
 <span data-ttu-id="bf0ef-105">例如，指定 `Book` 類別，您可從其中衍生並建立擁有更多屬性的 `ExpandedBook` 類別。</span><span class="sxs-lookup"><span data-stu-id="bf0ef-105">For example, given a `Book` class, you can derive from it and create an `ExpandedBook` class that has a few more properties.</span></span> <span data-ttu-id="bf0ef-106">然而，您必須指示 **XmlSerializer** 在序列化或還原序列化時，接受衍生類型。</span><span class="sxs-lookup"><span data-stu-id="bf0ef-106">However, you must instruct the **XmlSerializer** to accept the derived type when serializing or deserializing.</span></span> <span data-ttu-id="bf0ef-107">做法是建立 <xref:System.Xml.Serialization.XmlElementAttribute> 執行個體並設定其 **Type** 屬性為衍生類別類型。</span><span class="sxs-lookup"><span data-stu-id="bf0ef-107">This can be done by creating a <xref:System.Xml.Serialization.XmlElementAttribute> instance and setting its **Type** property to the derived class type.</span></span> <span data-ttu-id="bf0ef-108">將 **XmlElementAttribute** 新增至 <xref:System.Xml.Serialization.XmlAttributes> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bf0ef-108">Add the **XmlElementAttribute** to a <xref:System.Xml.Serialization.XmlAttributes> instance.</span></span> <span data-ttu-id="bf0ef-109">然後，將 **XmlAttributes** 新增至 <xref:System.Xml.Serialization.XmlAttributeOverrides> 執行個體，並指定要覆寫的類型以及接受衍生類別的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="bf0ef-109">Then add the **XmlAttributes** to a <xref:System.Xml.Serialization.XmlAttributeOverrides> instance, specifying the type being overridden and the name of the member that accepts the derived class.</span></span> <span data-ttu-id="bf0ef-110">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="bf0ef-110">This is shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf0ef-111">範例</span><span class="sxs-lookup"><span data-stu-id="bf0ef-111">Example</span></span>  
  
```vb  
Public Class Orders  
    public Books() As Book  
End Class     
  
Public Class Book  
    public ISBN As String   
End Class  
  
Public Class ExpandedBook  
    Inherits Book  
    public NewEdition As Boolean  
End Class  
  
Public Class Run  
    Shared Sub Main()  
        Dim t As Run = New Run()  
        t.SerializeObject("Book.xml")  
        t.DeserializeObject("Book.xml")  
    End Sub  
  
    Public Sub SerializeObject(filename As String)  
        ' Each overridden field, property, or type requires   
        ' an XmlAttributes instance.   
        Dim attrs As XmlAttributes = New XmlAttributes()  
  
        ' Creates an XmlElementAttribute instance to override the   
        ' field that returns Book objects. The overridden field  
        ' returns Expanded objects instead.  
        Dim attr As XmlElementAttribute = _  
        New XmlElementAttribute()  
        attr.ElementName = "NewBook"  
        attr.Type = GetType(ExpandedBook)  
  
        ' Adds the element to the collection of elements.  
        attrs.XmlElements.Add(attr)  
  
        ' Creates the XmlAttributeOverrides.  
        Dim attrOverrides As XmlAttributeOverrides = _  
        New XmlAttributeOverrides()  
  
        ' Adds the type of the class that contains the overridden   
        ' member, as well as the XmlAttributes instance to override it   
        ' with, to the XmlAttributeOverrides instance.   
        attrOverrides.Add(GetType(Orders), "Books", attrs)  
  
        ' Creates the XmlSerializer using the XmlAttributeOverrides.  
        Dim s As XmlSerializer  = _  
        New XmlSerializer(GetType(Orders), attrOverrides)  
  
        ' Writing the file requires a TextWriter instance.  
        Dim writer As TextWriter = New StreamWriter(filename)  
  
        ' Creates the object to be serialized.  
        Dim myOrders As Orders = New Orders()  
  
        ' Creates an object of the derived type.  
        Dim b As ExpandedBook = New ExpandedBook()  
        b.ISBN= "123456789"  
        b.NewEdition = True  
        myOrders.Books = New ExpandedBook(){b}  
  
        ' Serializes the object.  
        s.Serialize(writer,myOrders)  
        writer.Close()  
    End Sub  
  
    Public Sub DeserializeObject(filename As String)  
        Dim attrOverrides As XmlAttributeOverrides = _  
        New XmlAttributeOverrides()  
        Dim attrs As XmlAttributes = New XmlAttributes()  
  
        ' Creates an XmlElementAttribute to override the   
        ' field that returns Book objects. The overridden field  
        ' returns Expanded objects instead.   
        Dim attr As XmlElementAttribute = _  
        New XmlElementAttribute()  
        attr.ElementName = "NewBook"  
        attr.Type = GetType(ExpandedBook)  
  
        ' Adds the XmlElementAttribute to the collection of objects.  
        attrs.XmlElements.Add(attr)  
  
        attrOverrides.Add(GetType(Orders), "Books", attrs)  
  
        ' Creates the XmlSerializer using the XmlAttributeOverrides.  
        Dim s As XmlSerializer = _  
        New XmlSerializer(GetType(Orders), attrOverrides)  
  
        Dim fs As FileStream = New FileStream(filename, FileMode.Open)  
        Dim myOrders As Orders = CType( s.Deserialize(fs), Orders)  
        Console.WriteLine("ExpandedBook:")  
  
        ' The difference between deserializing the overridden   
        ' XML document and serializing it is this: To read the derived   
        ' object values, you must declare an object of the derived type   
        ' and cast the returned object to it.   
        Dim expanded As ExpandedBook   
        Dim b As Book  
        for each b  in myOrders.Books  
            expanded = CType(b, ExpandedBook)  
            Console.WriteLine(expanded.ISBN)  
            Console.WriteLine(expanded.NewEdition)  
        Next  
    End Sub  
End Class  
```  
  
```csharp  
public class Orders  
{  
    public Book[] Books;  
}      
  
public class Book  
{  
    public string ISBN;  
}  
  
public class ExpandedBook:Book  
{  
    public bool NewEdition;  
}  
  
public class Run  
{  
    public void SerializeObject(string filename)  
    {  
        // Each overridden field, property, or type requires   
        // an XmlAttributes instance.  
        XmlAttributes attrs = new XmlAttributes();  
  
        // Creates an XmlElementAttribute instance to override the   
        // field that returns Book objects. The overridden field  
        // returns Expanded objects instead.  
        XmlElementAttribute attr = new XmlElementAttribute();  
        attr.ElementName = "NewBook";  
        attr.Type = typeof(ExpandedBook);  
  
        // Adds the element to the collection of elements.  
        attrs.XmlElements.Add(attr);  
  
        // Creates the XmlAttributeOverrides instance.  
        XmlAttributeOverrides attrOverrides = new XmlAttributeOverrides();  
  
        // Adds the type of the class that contains the overridden   
        // member, as well as the XmlAttributes instance to override it   
        // with, to the XmlAttributeOverrides.  
        attrOverrides.Add(typeof(Orders), "Books", attrs);  
  
        // Creates the XmlSerializer using the XmlAttributeOverrides.  
        XmlSerializer s =   
        new XmlSerializer(typeof(Orders), attrOverrides);  
  
        // Writing the file requires a TextWriter instance.  
        TextWriter writer = new StreamWriter(filename);  
  
        // Creates the object to be serialized.  
        Orders myOrders = new Orders();  
  
        // Creates an object of the derived type.  
        ExpandedBook b = new ExpandedBook();  
        b.ISBN= "123456789";  
        b.NewEdition = true;  
        myOrders.Books = new ExpandedBook[]{b};  
  
        // Serializes the object.  
        s.Serialize(writer,myOrders);  
        writer.Close();  
    }  
  
    public void DeserializeObject(string filename)  
    {  
        XmlAttributeOverrides attrOverrides =   
            new XmlAttributeOverrides();  
        XmlAttributes attrs = new XmlAttributes();  
  
        // Creates an XmlElementAttribute to override the   
        // field that returns Book objects. The overridden field  
        // returns Expanded objects instead.  
        XmlElementAttribute attr = new XmlElementAttribute();  
        attr.ElementName = "NewBook";  
        attr.Type = typeof(ExpandedBook);  
  
        // Adds the XmlElementAttribute to the collection of objects.  
        attrs.XmlElements.Add(attr);  
  
        attrOverrides.Add(typeof(Orders), "Books", attrs);  
  
        // Creates the XmlSerializer using the XmlAttributeOverrides.  
        XmlSerializer s =   
        new XmlSerializer(typeof(Orders), attrOverrides);  
  
        FileStream fs = new FileStream(filename, FileMode.Open);  
        Orders myOrders = (Orders) s.Deserialize(fs);  
        Console.WriteLine("ExpandedBook:");  
  
        // The difference between deserializing the overridden   
        // XML document and serializing it is this: To read the derived   
        // object values, you must declare an object of the derived type   
        // and cast the returned object to it.  
        ExpandedBook expanded;  
        foreach(Book b in myOrders.Books)   
        {  
            expanded = (ExpandedBook)b;  
            Console.WriteLine(  
            expanded.ISBN + "\n" +   
            expanded.NewEdition);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf0ef-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf0ef-112">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>  
- <xref:System.Xml.Serialization.XmlElementAttribute>  
- <xref:System.Xml.Serialization.XmlAttributes>  
- <xref:System.Xml.Serialization.XmlAttributeOverrides>  
- [<span data-ttu-id="bf0ef-113">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="bf0ef-113">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
- [<span data-ttu-id="bf0ef-114">如何：序列化物件</span><span class="sxs-lookup"><span data-stu-id="bf0ef-114">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [<span data-ttu-id="bf0ef-115">如何：指定 XML 資料流的替代元素名稱</span><span class="sxs-lookup"><span data-stu-id="bf0ef-115">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
