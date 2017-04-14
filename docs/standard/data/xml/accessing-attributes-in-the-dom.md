---
title: "存取 DOM 中的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# 存取 DOM 中的屬性
屬性 \(Attribute\) 是項目的屬性 \(Property\)，而不是項目的子系。  這個差別是很重要的，因為這關係到用來巡覽 XML 文件物件模型 \(DOM\) 的同層級節點、父節點和子節點的方法。  例如，**PreviousSibling** 和 **NextSibling** 方法無法用來從項目巡覽到屬性，或在屬性之間巡覽。  屬性 \(Attribute\) 反而是項目的屬性並且由項目所擁有，它有 **OwnerElement** 屬性而沒有 **parentNode** 屬性 \(Property\)，並且有不同的巡覽方法。  
  
 當目前的節點是項目時，使用 **HasAttribute** 方法來查看是否有與項目相關的屬性。  一旦知道項目有屬性 \(Attribute\)，就有多種存取屬性 \(Attribute\) 的方法。  若要從項目中擷取單一屬性，您可以使用 **XmlElement** 的 **GetAttribute** 與 **GetAttributeNode** 方法，也可以取得所有的屬性並將其置於集合中。  如果您需要重複集合，那麼取得集合很有用。  如果想要有項目的所有屬性 \(Attribute\)，請使用項目的 **Attributes** 屬性 \(Property\) 來擷取所有的屬性 \(Attribute\) 置於集合中。  
  
## 擷取所有的屬性 \(Attribute\) 置於集合中  
 如果想要將項目節點的所有屬性 \(Attribute\) 都置於集合之中，請呼叫 \(Call\) **XmlElement.Attributes** 屬性 \(Property\)。  這會取得包含項目之所有屬性的 **XmlAttributeCollection**。  **XmlAttributeCollection** 類別會從 **XmlNamedNode** 對應繼承。  所以，集合可以使用的方法和屬性除了 **XmlAttributeCollection** 類別特定的方法和屬性 \(如 **ItemOf** 屬性和 **Append** 方法\) 之外，還包括具名節點對應可使用的方法和屬性。  屬性集合中的每個項目都代表一個 **XmlAttribute** 節點。  若要找出項目上的屬性數目，請取得 **XmlAttributeCollection**，並且使用 **Count** 屬性來查看集合中有多少 **XmlAttribute** 節點。  
  
 下列程式碼範例將說明如何擷取屬性集合，同時使用 **Count** 方法來計算迴圈索引並加以重複。  程式碼顯示如何從集合中擷取單一的屬性 \(Attribute\) 並顯示其值。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.   
        Dim myElement As XmlElement = doc.DocumentElement  
  
        ' Create an attribute collection from the element.  
        Dim attrColl As XmlAttributeCollection = myElement.Attributes  
  
        ' Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...")  
        Dim i As Integer  
        For i = 0 To attrColl.Count - 1  
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)  
            Console.Write("{0}", attrColl.ItemOf(i).Value)  
            Console.WriteLine()  
        Next  
  
        ' Retrieve a single attribute from the collection; specifically, the  
        ' attribute with the name "misc".  
        Dim attr As XmlAttribute = attrColl("misc")  
  
        ' Retrieve the value from that attribute.  
        Dim miscValue As String = attr.InnerXml  
  
        Console.WriteLine("Display the attribute information.")  
        Console.WriteLine(miscValue)  
  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  
    public static void Main()  
    {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +  
                      "<title>The Handmaid's Tale</title>" +  
                      "<price>14.95</price>" +  
                      "</book>");  
  
        // Move to an element.  
        XmlElement myElement = doc.DocumentElement;  
  
        // Create an attribute collection from the element.  
        XmlAttributeCollection attrColl = myElement.Attributes;  
  
        // Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...");  
        for (int i = 0; i < attrColl.Count; i++)  
        {  
            Console.Write("{0} = ", attrColl[i].Name);  
            Console.Write("{0}", attrColl[i].Value);  
            Console.WriteLine();  
        }  
  
        // Retrieve a single attribute from the collection; specifically, the  
        // attribute with the name "misc".  
        XmlAttribute attr = attrColl["misc"];  
  
        // Retrieve the value from that attribute.  
        String miscValue = attr.InnerXml;  
  
        Console.WriteLine("Display the attribute information.");  
        Console.WriteLine(miscValue);  
  
    }  
}  
```  
  
 這個範例顯示下列輸出：  
  
 **輸出**  
  
 顯示集合中的所有屬性 \(Attribute\)。  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 屬性集合中的資訊可以由名稱或索引編號擷取。  上述範例顯示如何依名稱擷取資料。  下一個範例則顯示如何依索引編號擷取資料。  
  
 因為 **XmlAttributeCollection** 是集合並且可以依名稱或索引重複執行，此範例將說明如何使用以零起始的索引，並將下列檔案 **baseuri.xml** 作為輸入，來選取集合中的第一個屬性。  
  
### 輸入  
  
```  
<!-- XML fragment -->  
<book genre="novel">  
  <title>Pride And Prejudice</title>  
</book>  
```  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.Load("http://localhost/baseuri.xml")  
  
        ' Display information on the attribute node. The value  
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.  
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)  
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)  
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)  
        Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText)  
    End Sub 'Main   
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    // Create the XmlDocument.  
    XmlDocument doc = new XmlDocument();  
  
    doc.Load("http://localhost/baseuri.xml");  
  
    // Display information on the attribute node. The value  
    // returned for BaseURI is 'http://localhost/baseuri.xml'.  
    XmlAttribute attr = doc.DocumentElement.Attributes[0];  
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);  
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);  
    Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText);  
  }  
}  
```  
  
## 擷取個別屬性 \(Attribute\) 節點  
 若要從項目中擷取單一屬性節點，便會使用 <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=fullName> 方法。  它會傳回型別 **XmlAttribute** 的物件。  一旦有了 **XmlAttribute**，在 [XmlAttribute Members](frlrfsystemxmlxmlattributeclasstopic) 類別中可以使用的所有方法和屬性 \(Property\)，這個物件也都可以使用，例如尋找 **OwnerElement**。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.  
        Dim root As XmlElement  
        root = doc.DocumentElement  
  
        ' Get an attribute.  
        Dim attr As XmlAttribute  
        attr = root.GetAttributeNode("ISBN")  
  
        ' Display the value of the attribute.  
        Dim attrValue As String  
        attrValue = attr.InnerXml  
        Console.WriteLine(attrValue)  
  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
 public class Sample  
 {  
      public static void Main()  
      {  
    XmlDocument doc = new XmlDocument();  
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +  
                   "<title>The Handmaid's Tale</title>" +  
                   "<price>14.95</price>" +  
                   "</book>");   
  
    // Move to an element.  
     XmlElement root = doc.DocumentElement;  
  
    // Get an attribute.  
     XmlAttribute attr = root.GetAttributeNode("ISBN");  
  
    // Display the value of the attribute.  
     String attrValue = attr.InnerXml;  
     Console.WriteLine(attrValue);  
  
    }  
}  
```  
  
 如前一個範例所示，您也可以從屬性集合中擷取單一屬性節點。  下列程式碼範例顯示如何撰寫一行程式碼，從 XML 文件樹狀結構的根目錄，依索引編號擷取單一屬性 \(Attribute\)，它也稱為 **DocumentElement** 屬性 \(Property\)。  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## 請參閱  
 [XML 文件物件模型 \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)