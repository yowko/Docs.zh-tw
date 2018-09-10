---
title: 使用 XmlNodeChangedEventArgs 之 XML 文件中的事件處理
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 0fe844e3-5b6f-4fe7-ad15-22459501738b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c382b22825512000a906af8a865b6b7c5f4c73c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44204886"
---
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a><span data-ttu-id="5f736-102">使用 XmlNodeChangedEventArgs 之 XML 文件中的事件處理</span><span class="sxs-lookup"><span data-stu-id="5f736-102">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>
<span data-ttu-id="5f736-103">**XmlNodeChangedEventArgs** 會封裝傳入註冊在處理事件之 **XmlDocument** 物件上的事件處理常式之引數。</span><span class="sxs-lookup"><span data-stu-id="5f736-103">The **XmlNodeChangedEventArgs** encapsulates the arguments passed to the event handlers registered on the **XmlDocument** object for handling events.</span></span> <span data-ttu-id="5f736-104">下列表格說明事件和引發事件的時機。</span><span class="sxs-lookup"><span data-stu-id="5f736-104">The events and a description of when they are fired is given in the following table.</span></span>  
  
|<span data-ttu-id="5f736-105">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="5f736-105">Event</span></span>|<span data-ttu-id="5f736-106">引發</span><span class="sxs-lookup"><span data-stu-id="5f736-106">Fired</span></span>|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|<span data-ttu-id="5f736-107">當屬於目前文件的節點要插入另一個節點。</span><span class="sxs-lookup"><span data-stu-id="5f736-107">When a node belonging to the current document is about to be inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeInserted>|<span data-ttu-id="5f736-108">當屬於目前文件的節點已經插入另一個節點。</span><span class="sxs-lookup"><span data-stu-id="5f736-108">When a node belonging to the current document has been inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|<span data-ttu-id="5f736-109">當屬於這個文件的節點要從文件中移除。</span><span class="sxs-lookup"><span data-stu-id="5f736-109">When a node belonging to this document is about to be removed from the document.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|<span data-ttu-id="5f736-110">當屬於這個文件的節點已經從其父代中移除。</span><span class="sxs-lookup"><span data-stu-id="5f736-110">When a node belonging to this document has been removed from its parent.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanging>|<span data-ttu-id="5f736-111">當節點的值即將要變更。</span><span class="sxs-lookup"><span data-stu-id="5f736-111">When the value of a node is about to be changed.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanged>|<span data-ttu-id="5f736-112">當節點的值已經變更。</span><span class="sxs-lookup"><span data-stu-id="5f736-112">When the value of a node has been changed.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="5f736-113">若 **XmlDataDocument** 記憶體使用已完全最佳化為使用 **DataSet** 存放區，則在變更基礎 **DataSet** 時，**XmlDataDocument** 可能不會引發上列的任何事件。</span><span class="sxs-lookup"><span data-stu-id="5f736-113">If the **XmlDataDocument** memory usage is fully optimized to use **DataSet** storage, the **XmlDataDocument** might not raise any of the events listed above when changes are made to the underlying **DataSet**.</span></span> <span data-ttu-id="5f736-114">如果您需要這些事件，則必須周遊整個 **XmlDocument** 一次，讓記憶體使用成為非完全最佳化。</span><span class="sxs-lookup"><span data-stu-id="5f736-114">If you need these events, you must traverse the whole **XmlDocument** once to make the memory usage non-fully optimized.</span></span>  
  
 <span data-ttu-id="5f736-115">下列程式碼範例將說明如何定義事件處理常式，以及如何將事件處理常式加入事件中。</span><span class="sxs-lookup"><span data-stu-id="5f736-115">The following code example shows how to define an event handler and how to add the event handler to an event.</span></span>  
  
```vb  
' Attach the event handler, NodeInsertedHandler, to the NodeInserted  
' event.  
Dim doc as XmlDocument = new XmlDocument()  
Dim XmlNodeChgEHdlr as XmlNodeChangedEventHandler = new XmlNodeChangedEventHandler(addressof MyNodeChangedEvent)   
AddHandler doc.NodeInserted, XmlNodeChgEHdlr   
  
Dim n as XmlNode = doc.CreateElement( "element" )  
Console.WriteLine( "Before Event Inserting" )   
  
' This is the point where the new node is being inserted in the tree,  
' and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n )  
Console.WriteLine( "After Event Inserting" )   
  
' Define the event handler that handles the NodeInserted event.  
sub NodeInsertedHandler(src as Object, args as XmlNodeChangedEventArgs)  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!")  
end sub  
```  
  
```csharp  
// Attach the event handler, NodeInsertedHandler, to the NodeInserted  
// event.  
XmlDocument doc = new XmlDocument();  
doc.NodeInserted += new XmlNodeChangedEventHandler(NodeInsertedHandler);  
XmlNode n = doc.CreateElement( "element" );  
Console.WriteLine( "Before Event Inserting" );  
  
// This is the point where the new node is being inserted in the tree,  
// and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n );  
Console.WriteLine( "After Event Inserting" );   
  
// Define the event handler that handles the NodeInserted event.  
void NodeInsertedHandler(Object src, XmlNodeChangedEventArgs args)  
{  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!");  
}  
```  
  
 <span data-ttu-id="5f736-116">有些 XML 文件物件模型 (DOM) 作業是可以引發多個事件的複合作業。</span><span class="sxs-lookup"><span data-stu-id="5f736-116">Some XML Document Object Model (DOM) operations are compound operations that can result in multiple events being fired.</span></span> <span data-ttu-id="5f736-117">例如，**AppendChild** 也必須移除先前父代所附加的節點。</span><span class="sxs-lookup"><span data-stu-id="5f736-117">For example, **AppendChild** may also have to remove the node being appended from its previous parent.</span></span> <span data-ttu-id="5f736-118">在這個案例中，您會看到先引發 **NodeRemoved** 事件，接著引發 **NodeInserted** 事件。</span><span class="sxs-lookup"><span data-stu-id="5f736-118">In this case, you see a **NodeRemoved** event fired first, followed by a **NodeInserted** event.</span></span> <span data-ttu-id="5f736-119">設定 **InnerXml** 這類的作業可以在多個事件中產生。</span><span class="sxs-lookup"><span data-stu-id="5f736-119">Operations like setting **InnerXml** could result in multiple events.</span></span>  
  
 <span data-ttu-id="5f736-120">下列程式碼範例將說明事件處理常式的建立以及 **NodeInserted** 事件的處理。</span><span class="sxs-lookup"><span data-stu-id="5f736-120">The following code example shows the creation of the event handler and the handling of the **NodeInserted** event.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports Microsoft.VisualBasic  
  
Public Class Sample  
  
    Private Const filename As String = "books.xml"  
  
    Shared Sub Main()  
        Dim mySample As Sample = New Sample()  
        mySample.Run(filename)  
    End Sub  
  
    Public Sub Run(ByVal args As String)  
        ' Create and load the XML document.  
        Console.WriteLine("Loading file 0 ...", args)  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.Load(args)  
  
        ' Create the event handlers.  
        Dim XmlNodeChgEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeChangedEvent)  
        Dim XmlNodeInsrtEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeInsertedEvent)  
        AddHandler doc.NodeChanged, XmlNodeChgEHdlr  
        AddHandler doc.NodeInserted, XmlNodeInsrtEHdlr  
  
        ' Change the book price.  
        doc.DocumentElement.LastChild.InnerText = "5.95"  
  
        ' Add a new element.  
        Dim newElem As XmlElement = doc.CreateElement("style")  
        newElem.InnerText = "hardcover"  
        doc.DocumentElement.AppendChild(newElem)  
  
        Console.WriteLine(Chr(13) + Chr(10) + "Display the modified XML...")  
        Console.WriteLine(doc.OuterXml)  
    End Sub  
  
    ' Handle the NodeChanged event.  
    Public Sub MyNodeChangedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Changed Event: <0> changed", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value  0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
    ' Handle the NodeInserted event.  
    Public Sub MyNodeInsertedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Inserted Event: <0> inserted", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value 0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
End Class        ' End class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  private const String filename = "books.xml";  
  
  public static void Main()  
  {  
     Sample mySample = new Sample();  
     mySample.Run(filename);  
  }  
  
  public void Run(String args)  
  {  
  
     // Create and load the XML document.  
     Console.WriteLine ("Loading file {0} ...", args);  
     XmlDocument doc = new XmlDocument();  
     doc.Load (args);  
  
     // Create the event handlers.  
     doc.NodeChanged += new XmlNodeChangedEventHandler(this.MyNodeChangedEvent);  
     doc.NodeInserted += new XmlNodeChangedEventHandler(this.MyNodeInsertedEvent);  
  
     // Change the book price.  
     doc.DocumentElement.LastChild.InnerText = "5.95";  
  
     // Add a new element.  
     XmlElement newElem = doc.CreateElement("style");  
     newElem.InnerText = "hardcover";  
     doc.DocumentElement.AppendChild(newElem);  
  
     Console.WriteLine("\r\nDisplay the modified XML...");  
     Console.WriteLine(doc.OuterXml);             
  
  }  
  
  // Handle the NodeChanged event.  
  public void MyNodeChangedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Changed Event: <{0}> changed", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value  {0}", args.Node.Value);  
     }  
     else  
       Console.WriteLine("");  
  }  
  
  // Handle the NodeInserted event.  
  public void MyNodeInsertedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Inserted Event: <{0}> inserted", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value {0}", args.Node.Value);  
     }  
     else  
        Console.WriteLine("");  
  }  
  
} // End class   
```  
  
 <span data-ttu-id="5f736-121">如需詳細資訊，請參閱 <xref:System.Xml.XmlNodeChangedEventArgs> 與 <xref:System.Xml.XmlNodeChangedEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="5f736-121">For more information, see <xref:System.Xml.XmlNodeChangedEventArgs> and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f736-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f736-122">See also</span></span>

- [<span data-ttu-id="5f736-123">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="5f736-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
