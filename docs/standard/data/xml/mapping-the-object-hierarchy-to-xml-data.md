---
title: "將物件階層架構對應至 XML 資料 | Microsoft Docs"
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
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# 將物件階層架構對應至 XML 資料
當 XML 文件在記憶體時，概念式的表示就是樹狀結構。  對於程式設計，您有物件階層架構來存取樹狀結構的節點。  下列範例顯示 XML 內容如何成為節點。  
  
 當 XML 讀入 XML 文件物件模型 \(DOM\) 時，片段會轉譯成節點，而這些節點會保留本身其他相關的中繼資料，例如其節點型別與值。  節點型別是指其物件，以及決定可執行哪些動作與可設定或擷取哪些屬性的項目。  
  
 如果您有下列的簡單 XML：  
  
 **輸入**  
  
```  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 輸入表示在記憶體中，顯示成下列具指派節點型別屬性的節點樹狀結構：  
  
 ![範例節點樹狀結構](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple\_XML")  
Book 和 title 節點的樹狀結構表示  
  
 `book` 項目會成為 **XmlElement** 物件，下一個項目 \(`title`\) 也會成為 **XmlElement**，而項目內容會成為 **XmlText** 物件。  查看 **XmlElement** 方法和屬性時，方法和屬性與 **XmlText** 物件中可以使用的方法和屬性不同。  因此了解 XML 標記會變成何種節點型別變得很重要，因為它的節點型別會決定可以執行的動作。  
  
 下列範例讀入 XML 資料，並且根據節點型別寫出不同的文字。  使用下列 XML 資料檔 **items.xml** 來做為輸入：  
  
 **輸入**  
  
```  
<?xml version="1.0"?>  
<!-- This is a sample XML document -->  
<!DOCTYPE Items [<!ENTITY number "123">]>  
<Items>  
  <Item>Test with an entity: &number;</Item>  
  <Item>test with a child element <more/> stuff</Item>  
  <Item>test with a CDATA section <![CDATA[<456>]]> def</Item>  
  <Item>Test with a char entity: A</Item>  
  <!-- Fourteen chars in this element.-->  
  <Item>1234567890ABCD</Item>  
</Items>  
```  
  
 下列程式碼範例讀取 **items.xml** 檔並且顯示每個節點型別的資訊。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
    Private Const filename As String = "items.xml"  
  
    Public Shared Sub Main()  
  
        Dim reader As XmlTextReader = Nothing  
  
        Try  
            ' Load the reader with the data file and   
            'ignore all white space nodes.   
            reader = New XmlTextReader(filename)  
            reader.WhitespaceHandling = WhitespaceHandling.None  
  
            ' Parse the file and display each of the nodes.  
            While reader.Read()  
                Select Case reader.NodeType  
                    Case XmlNodeType.Element  
                        Console.Write("<{0}>", reader.Name)  
                    Case XmlNodeType.Text  
                        Console.Write(reader.Value)  
                    Case XmlNodeType.CDATA  
                        Console.Write("<![CDATA[{0}]]>", reader.Value)  
                    Case XmlNodeType.ProcessingInstruction  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value)  
                    Case XmlNodeType.Comment  
                        Console.Write("<!--{0}-->", reader.Value)  
                    Case XmlNodeType.XmlDeclaration  
                        Console.Write("<?xml version='1.0'?>")  
                    Case XmlNodeType.Document  
                    Case XmlNodeType.DocumentType  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value)  
                    Case XmlNodeType.EntityReference  
                        Console.Write(reader.Name)  
                    Case XmlNodeType.EndElement  
                        Console.Write("</{0}>", reader.Name)  
                End Select  
            End While  
  
        Finally  
            If Not (reader Is Nothing) Then  
                reader.Close()  
            End If  
        End Try  
    End Sub 'Main ' End class  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    private const String filename = "items.xml";  
  
    public static void Main()  
    {  
        XmlTextReader reader = null;  
  
        try  
        {  
            // Load the reader with the data file and ignore   
            // all white space nodes.  
            reader = new XmlTextReader(filename);  
            reader.WhitespaceHandling = WhitespaceHandling.None;  
  
            // Parse the file and display each of the nodes.  
            while (reader.Read())  
            {  
                switch (reader.NodeType)  
                {  
                    case XmlNodeType.Element:  
                        Console.Write("<{0}>", reader.Name);  
                        break;  
                    case XmlNodeType.Text:  
                        Console.Write(reader.Value);  
                        break;  
                    case XmlNodeType.CDATA:  
                        Console.Write("<![CDATA[{0}]]>", reader.Value);  
                        break;  
                    case XmlNodeType.ProcessingInstruction:  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.Comment:  
                        Console.Write("<!--{0}-->", reader.Value);  
                        break;  
                    case XmlNodeType.XmlDeclaration:  
                        Console.Write("<?xml version='1.0'?>");  
                        break;  
                    case XmlNodeType.Document:  
                        break;  
                    case XmlNodeType.DocumentType:  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.EntityReference:  
                        Console.Write(reader.Name);  
                        break;  
                    case XmlNodeType.EndElement:  
                        Console.Write("</{0}>", reader.Name);  
                        break;  
                }  
            }  
        }  
  
        finally  
        {  
            if (reader != null)  
                reader.Close();  
        }  
    }  
} // End class  
```  
  
 範例的輸出透露資料至節點型別的對應。  
  
 **輸出**  
  
```  
  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 逐行使用輸入，並利用程式碼所產生的輸出，即可使用下列表格來分析哪個節點的測試會產生哪些輸出行，藉此瞭解何種 XML 資料會成為何種節點型別。  
  
|輸入|輸出|節點型別測試|  
|--------|--------|------------|  
|\<?xml version\="1.0"?\>|\<?xml version\='1.0'?\>|XmlNodeType.XmlDeclaration|  
|\<\!\-\- This is a sample XML document \-\-\>|\<\!\-\- This is a sample XML document \-\-\>|XmlNodeType.Comment|  
|\<\!DOCTYPE Items \[\<\!ENTITY number "123"\>\]\>|\<\!DOCTYPE Items \[\<\!ENTITY number "123"\>\]|XmlNodeType.DocumentType|  
|\<Items\>|\<Items\>|XmlNodeType.Element|  
|\<Item\>|\<Item\>|XmlNodeType.Element|  
|Test with an entity: &number;|Test with an entity: 123|XmlNodeType.Text|  
|\<\/Item\>|\<\/Item\>|XmlNodeType.EndElement|  
|\<Item\>|\<Item\>|XmNodeType.Element|  
|test with a child element|test with a child element|XmlNodeType.Text|  
|\<more\>|\<more\>|XmlNodeType.Element|  
|stuff|stuff|XmlNodeType.Text|  
|\<\/Item\>|\<\/Item\>|XmlNodeType.EndElement|  
|\<Item\>|\<Item\>|XmlNodeType.Element|  
|test with a CDATA section|test with a CDATA section|XmlTest.Text|  
|\<\!\[CDATA\[\<456\>\]\]\>|\<\!\[CDATA\[\<456\>\]\]\>|XmlTest.CDATA|  
|def|def|XmlNodeType.Text|  
|\<\/Item\>|\<\/Item\>|XmlNodeType.EndElement|  
|\<Item\>|\<Item\>|XmlNodeType.Element|  
|Test with a char entity: &\#65;|Test with a char entity: A|XmlNodeType.Text|  
|\<\/Item\>|\<\/Item\>|XmlNodeType.EndElement|  
|\<\!\-\- Fourteen chars in this element.\-\-\>|\<\-\-Fourteen chars in this element.\-\-\>|XmlNodeType.Comment|  
|\<Item\>|\<Item\>|XmlNodeType.Element|  
|1234567890ABCD|1234567890ABCD|XmlNodeType.Text|  
|\<\/Item\>|\<\/Item\>|XmlNodeType.EndElement|  
|\<\/Items\>|\<\/Items\>|XmlNodeType.EndElement|  
  
 您必須知道指派的是何種節點型別，因為節點型別可控制何種動作是有效的，以及何種屬性是您可以設定和擷取的。  
  
 若資料是由 **PreserveWhitespace** 旗標載入 DOM，泛空白字元節點的建立就會受到控制。  如需詳細資訊，請參閱[載入 DOM 時處理泛空白字元和顯著泛空白字元](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md)。  
  
 若要將新節點加入至 DOM，請參閱[將節點插入 XML 文件](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)。  若要從 DOM 移除節點，請參閱[從 XML 文件移除節點、內容和值](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)。  若要修改 DOM 中節點的內容，請參閱[修改 XML 文件中的節點、內容和值](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)。  
  
## 請參閱  
 [XML 文件物件模型 \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)