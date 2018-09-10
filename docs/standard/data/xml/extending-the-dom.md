---
title: 擴充 DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 70e13893cf350a193411f1833e2e3b21c9b64182
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269263"
---
# <a name="extending-the-dom"></a><span data-ttu-id="a746b-102">擴充 DOM</span><span class="sxs-lookup"><span data-stu-id="a746b-102">Extending the DOM</span></span>

<span data-ttu-id="a746b-103">Microsoft .NET Framework 含有可提供 XML 文件物件模型 (DOM) 之實作的基底類別組。</span><span class="sxs-lookup"><span data-stu-id="a746b-103">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="a746b-104"><xref:System.Xml.XmlNode> 及其衍生類別會提供方法和屬性，讓您巡覽、查詢和修改 XML 文件的內容和結構。</span><span class="sxs-lookup"><span data-stu-id="a746b-104">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>

<span data-ttu-id="a746b-105">當 XML 內容載入使用 DOM 的記憶體時，建立的節點包含資訊，例如節點名稱、節點型別等等。</span><span class="sxs-lookup"><span data-stu-id="a746b-105">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="a746b-106">有時您可能會需要基底類別所沒有提供的特定節點資訊。</span><span class="sxs-lookup"><span data-stu-id="a746b-106">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="a746b-107">例如，您可能想要查看節點的行號和位置。</span><span class="sxs-lookup"><span data-stu-id="a746b-107">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="a746b-108">在這個案例中，您可以從現有 DOM 類別衍生新類別並且加入其他功能。</span><span class="sxs-lookup"><span data-stu-id="a746b-108">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>

<span data-ttu-id="a746b-109">衍生新類別時有兩個一般方針：</span><span class="sxs-lookup"><span data-stu-id="a746b-109">There are two general guidelines when deriving new classes:</span></span>

- <span data-ttu-id="a746b-110">建議您絕不要從 <xref:System.Xml.XmlNode> 類別中進行衍生。</span><span class="sxs-lookup"><span data-stu-id="a746b-110">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="a746b-111">建議您從感興趣之節點型別的對應類別來衍生類別。</span><span class="sxs-lookup"><span data-stu-id="a746b-111">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="a746b-112">例如，如果您要傳回屬性節點的其他資訊，則可以從 <xref:System.Xml.XmlAttribute> 類別加以衍生。</span><span class="sxs-lookup"><span data-stu-id="a746b-112">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>

- <span data-ttu-id="a746b-113">除了節點建立方法之外，建議在覆寫函式時，您一定要呼叫函式的基底版本，然後加入其他任何的處理。</span><span class="sxs-lookup"><span data-stu-id="a746b-113">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>

## <a name="creating-your-own-node-instances"></a><span data-ttu-id="a746b-114">建立您自己的節點執行個體</span><span class="sxs-lookup"><span data-stu-id="a746b-114">Creating Your Own Node Instances</span></span>

<span data-ttu-id="a746b-115"><xref:System.Xml.XmlDocument> 類別包含節點建立方法。</span><span class="sxs-lookup"><span data-stu-id="a746b-115">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="a746b-116">當 XML 檔載入時，會呼叫這些方法來建立節點。</span><span class="sxs-lookup"><span data-stu-id="a746b-116">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="a746b-117">您可以覆寫這些方法，這樣就會在文件載入時建立您的節點執行個體。</span><span class="sxs-lookup"><span data-stu-id="a746b-117">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="a746b-118">例如，如果擴充了 <xref:System.Xml.XmlElement> 類別，則會繼承 <xref:System.Xml.XmlDocument> 類別，並覆寫 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a746b-118">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>

<span data-ttu-id="a746b-119">下列範例顯示如何覆寫 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法，以傳回 <xref:System.Xml.XmlElement> 類別的實作。</span><span class="sxs-lookup"><span data-stu-id="a746b-119">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>

```vb
Class LineInfoDocument
    Inherits XmlDocument
        Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
        Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
        Return elem
    End Function 'CreateElement
End Class 'LineInfoDocument
```

```csharp
class LineInfoDocument : XmlDocument 
{
    public override XmlElement CreateElement(string prefix, string localname, string nsURI) 
    {
        LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);
        return elem;
    }
}
```

## <a name="extending-a-class"></a><span data-ttu-id="a746b-120">擴充類別</span><span class="sxs-lookup"><span data-stu-id="a746b-120">Extending a Class</span></span>

<span data-ttu-id="a746b-121">若要擴充類別，請從其中一個現有的 DOM 類別衍生您的類別。</span><span class="sxs-lookup"><span data-stu-id="a746b-121">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="a746b-122">接著您可以覆寫基底類別中的虛擬方法或屬性，或加入您自己的方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="a746b-122">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>

<span data-ttu-id="a746b-123">在下列範例中會建立新類別，此新類別會實作 <xref:System.Xml.XmlElement> 類別和 <xref:System.Xml.IXmlLineInfo> 介面。</span><span class="sxs-lookup"><span data-stu-id="a746b-123">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="a746b-124">其他的方法和屬性會定義何者可讓使用者獲得指令行資訊。</span><span class="sxs-lookup"><span data-stu-id="a746b-124">Additional methods and properties are defined which allows users to gather line information.</span></span>

```vb
Class LineInfoElement
   Inherits XmlElement
   Implements IXmlLineInfo
   Private lineNumber As Integer = 0
   Private linePosition As Integer = 0

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub

   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)
      lineNumber = linenum
      linePosition = linepos
   End Sub

   Public ReadOnly Property LineNumber() As Integer
      Get
         Return lineNumber
      End Get
   End Property

   Public ReadOnly Property LinePosition() As Integer
      Get
         Return linePosition
      End Get
   End Property

   Public Function HasLineInfo() As Boolean
      Return True
   End Function
End Class ' End LineInfoElement class.
```

```csharp
class LineInfoElement : XmlElement, IXmlLineInfo {
   int lineNumber = 0;
   int linePosition = 0;
   internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ) : base( prefix, localname, nsURI, doc ) {
       ( (LineInfoDocument)doc ).IncrementElementCount();
  }
  public void SetLineInfo( int linenum, int linepos ) {
      lineNumber = linenum;
      linePosition = linepos;
  }
  public int LineNumber {
     get {
       return lineNumber;
     }
  }
  public int LinePosition {
      get {
        return linePosition;
      }
  }
  public bool HasLineInfo() {
    return true;
  }
} // End LineInfoElement class.
```

### <a name="example"></a><span data-ttu-id="a746b-125">範例</span><span class="sxs-lookup"><span data-stu-id="a746b-125">Example</span></span>

<span data-ttu-id="a746b-126">下列範例計算 XML 文件中項目的數目：</span><span class="sxs-lookup"><span data-stu-id="a746b-126">The following example counts the number of elements in an XML document:</span></span>

```vb
Imports System
Imports System.Xml
Imports System.IO

Class LineInfoDocument
   Inherits XmlDocument

   Private elementCount As Integer

   Friend Sub New()
      elementCount = 0
   End Sub

   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
      Return elem
   End Function

   Public Sub IncrementElementCount()
      elementCount += 1
   End Sub

   Public Function GetCount() As Integer
      Return elementCount
   End Function
End Class 'End LineInfoDocument class.

Class LineInfoElement
   Inherits XmlElement

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub 'New
End Class 'LineInfoElement
 _ 'End LineInfoElement class.

Public Class Test

   Private filename As [String] = "book.xml"

   Public Shared Sub Main()

      Dim doc As New LineInfoDocument()
      doc.Load(filename)
      Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount())
   End Sub
End Class
```

```csharp
using System;
using System.Xml;
using System.IO;

class LineInfoDocument : XmlDocument {

  int elementCount;
  internal LineInfoDocument():base() {
    elementCount = 0;
  }

  public override XmlElement CreateElement( string prefix, string localname, string nsURI) {
    LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this );
    return elem;
  }

  public void IncrementElementCount() {
     elementCount++;
  }

  public int GetCount() {
     return elementCount;
  }
} // End LineInfoDocument class.

class LineInfoElement:XmlElement {

    internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ):base( prefix,localname,nsURI, doc ){
      ((LineInfoDocument)doc).IncrementElementCount();
    }
} // End LineInfoElement class.

public class Test {

  const String filename = "book.xml";
  public static void Main() {

     LineInfoDocument doc =new LineInfoDocument();
     doc.Load(filename);
     Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount());

  }
}
```

#### <a name="input"></a><span data-ttu-id="a746b-127">輸入</span><span class="sxs-lookup"><span data-stu-id="a746b-127">Input</span></span>

<span data-ttu-id="a746b-128">book.xml</span><span class="sxs-lookup"><span data-stu-id="a746b-128">book.xml</span></span>

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a><span data-ttu-id="a746b-129">輸出</span><span class="sxs-lookup"><span data-stu-id="a746b-129">Output</span></span>

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a><span data-ttu-id="a746b-130">節點事件處理常式</span><span class="sxs-lookup"><span data-stu-id="a746b-130">Node Event Handler</span></span>

<span data-ttu-id="a746b-131">DOM 的 .NET Framework 實作也包含一個事件系統，當 XML 文件中的節點變更時，可以讓您接收和處理事件。</span><span class="sxs-lookup"><span data-stu-id="a746b-131">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="a746b-132">使用 <xref:System.Xml.XmlNodeChangedEventHandler> 和 <xref:System.Xml.XmlNodeChangedEventArgs> 類別，您可以擷取 `NodeChanged`、`NodeChanging`、`NodeInserted`、`NodeInserting`、`NodeRemoved` 和 `NodeRemoving` 事件。</span><span class="sxs-lookup"><span data-stu-id="a746b-132">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>

<span data-ttu-id="a746b-133">事件處理程序在衍生類別中的執行方式，與在原始 DOM 類別中的執行方式相同。</span><span class="sxs-lookup"><span data-stu-id="a746b-133">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>

<span data-ttu-id="a746b-134">如需有關節點事件處理的詳細資訊，請參閱[事件](../../../../docs/standard/events/index.md)和 <xref:System.Xml.XmlNodeChangedEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="a746b-134">For more information regarding node event handling, see [Events](../../../../docs/standard/events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>

## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="a746b-135">預設屬性和 CreateElement 方法</span><span class="sxs-lookup"><span data-stu-id="a746b-135">Default Attributes and the CreateElement Method</span></span>

<span data-ttu-id="a746b-136">如果要在衍生類別中覆寫 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法，則編輯文件而建立新項目時，將不會加入預設屬性。</span><span class="sxs-lookup"><span data-stu-id="a746b-136">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="a746b-137">這只是在編輯時才會發生的問題。</span><span class="sxs-lookup"><span data-stu-id="a746b-137">This is only an issue while editing.</span></span> <span data-ttu-id="a746b-138">因為 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法負責將預設屬性加入 <xref:System.Xml.XmlDocument>，所以您必須將此功能以程式碼編寫在 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法中。</span><span class="sxs-lookup"><span data-stu-id="a746b-138">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="a746b-139">如果載入含有預設屬性的 <xref:System.Xml.XmlDocument>，則會正確處理它們。</span><span class="sxs-lookup"><span data-stu-id="a746b-139">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="a746b-140">如需有關預設屬性的詳細資訊，請參閱[為 DOM 中的項目建立新屬性](creating-new-attributes-for-elements-in-the-dom.md)。</span><span class="sxs-lookup"><span data-stu-id="a746b-140">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a746b-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a746b-141">See also</span></span>

- [<span data-ttu-id="a746b-142">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="a746b-142">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)  
