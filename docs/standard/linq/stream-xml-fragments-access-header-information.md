---
title: 如何串流 XML 片段並存取標頭資訊-LINQ to XML
description: 瞭解如何執行和使用自訂座標軸方法，以從 URI 所指定的檔案串流 XML 片段。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: d50c29feb305341155257cd215e0292350689e7b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552212"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-linq-to-xml"></a><span data-ttu-id="0b96b-103">如何串流 XML 片段並存取標頭資訊 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="0b96b-103">How to stream XML fragments with access to header information (LINQ to XML)</span></span>

<span data-ttu-id="0b96b-104">有時候您必須讀取任意大的 XML 檔案並撰寫您的應用程式，讓應用程式的記憶體使用量可以預測。</span><span class="sxs-lookup"><span data-stu-id="0b96b-104">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="0b96b-105">如果您嘗試使用大型 XML 檔案填入 XML 樹狀結構，您的記憶體使用量將與檔案大小成正比，也就是，變成過度。</span><span class="sxs-lookup"><span data-stu-id="0b96b-105">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="0b96b-106">因此，您應該改用資料流技術。</span><span class="sxs-lookup"><span data-stu-id="0b96b-106">Therefore, you should use a streaming technique instead.</span></span>

<span data-ttu-id="0b96b-107">其中一個選項是使用 <xref:System.Xml.XmlReader> 撰寫您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b96b-107">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="0b96b-108">不過，您可能會想要使用 LINQ 來查詢 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="0b96b-108">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="0b96b-109">如果是的話，您可以撰寫自己的自訂座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="0b96b-109">If so, you can write your own custom axis method.</span></span> <span data-ttu-id="0b96b-110">如需詳細資訊，請參閱 [如何撰寫 LINQ to XML 座標軸方法](write-linq-xml-axis-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0b96b-110">For more information, see [How to write a LINQ to XML axis method](write-linq-xml-axis-method.md).</span></span>

<span data-ttu-id="0b96b-111">若要撰寫您自己的座標軸方法，您可以撰寫一個使用的小方法 <xref:System.Xml.XmlReader> 來讀取節點，直到它到達您感興趣的其中一個節點為止。</span><span class="sxs-lookup"><span data-stu-id="0b96b-111">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you're interested.</span></span> <span data-ttu-id="0b96b-112">然後，該方法會呼叫從 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 讀取的 <xref:System.Xml.XmlReader>，並具現化 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="0b96b-112">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="0b96b-113">然後，它會 `yield return` 對列舉自訂座標軸方法的方法產生每個片段。</span><span class="sxs-lookup"><span data-stu-id="0b96b-113">It then yields each fragment through `yield return` to the method that's enumerating your custom axis method.</span></span> <span data-ttu-id="0b96b-114">此時，您就可以在自訂座標軸方法上撰寫 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="0b96b-114">You can then write LINQ queries on your custom axis method.</span></span>

<span data-ttu-id="0b96b-115">在您僅需要處理一次來源文件的情況下，最適合使用資料流技術，而且您可以用文件的順序處理項目。</span><span class="sxs-lookup"><span data-stu-id="0b96b-115">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="0b96b-116">特定的標準查詢運算子 (例如，<xref:System.Linq.Enumerable.OrderBy%2A>) 會反覆查看其來源、收集所有資料、排序這些資料，最後產生順序中的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="0b96b-116">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="0b96b-117">如果您在產生第一個專案前使用具體化其來源的查詢運算子，您將不會保留較小的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="0b96b-117">If you use a query operator that materializes its source before yielding the first item, you won't retain a small memory footprint.</span></span>

## <a name="example-implement-and-use-a-custom-axis-method-that-streams-xml-fragments-from-the-file-specified-by-a-uri"></a><span data-ttu-id="0b96b-118">範例：執行和使用自訂座標軸方法，以從 URI 所指定的檔案串流 XML 片段</span><span class="sxs-lookup"><span data-stu-id="0b96b-118">Example: Implement and use a custom axis method that streams XML fragments from the file specified by a URI</span></span>

<span data-ttu-id="0b96b-119">有時候問題會變得更有趣。</span><span class="sxs-lookup"><span data-stu-id="0b96b-119">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="0b96b-120">在下列 XML 文件中，您自訂座標軸方法的消費者也必須知道每個項目所屬客戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="0b96b-120">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root>
  <Customer>
    <Name>A. Datum Corporation</Name>
    <Item>
      <Key>0001</Key>
    </Item>
    <Item>
      <Key>0002</Key>
    </Item>
    <Item>
      <Key>0003</Key>
    </Item>
    <Item>
      <Key>0004</Key>
    </Item>
  </Customer>
  <Customer>
    <Name>Fabrikam, Inc.</Name>
    <Item>
      <Key>0005</Key>
    </Item>
    <Item>
      <Key>0006</Key>
    </Item>
    <Item>
      <Key>0007</Key>
    </Item>
    <Item>
      <Key>0008</Key>
    </Item>
  </Customer>
  <Customer>
    <Name>Southridge Video</Name>
    <Item>
      <Key>0009</Key>
    </Item>
    <Item>
      <Key>0010</Key>
    </Item>
  </Customer>
</Root>
```

<span data-ttu-id="0b96b-121">此範例所採用的方法也會監看此標頭資訊、儲存標頭資訊，然後建立包含標頭資訊和您要列舉之詳細資料的小型 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="0b96b-121">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you're enumerating.</span></span> <span data-ttu-id="0b96b-122">這個座標軸方法接著就會產生這個新的小型 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="0b96b-122">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="0b96b-123">該查詢將可以存取標頭資訊以及詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0b96b-123">The query then has access to the header information as well as the detail information.</span></span>

<span data-ttu-id="0b96b-124">此方法擁有小的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="0b96b-124">This approach has a small memory footprint.</span></span> <span data-ttu-id="0b96b-125">當產生每個詳細的 XML 片段時，不會保留前一個片段的參考，而且可供垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="0b96b-125">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it's available for garbage collection.</span></span> <span data-ttu-id="0b96b-126">這項技術會在堆積上建立許多短期存留的物件。</span><span class="sxs-lookup"><span data-stu-id="0b96b-126">This technique creates many short lived objects on the heap.</span></span>

<span data-ttu-id="0b96b-127">下列範例顯示如何實作與使用從 URI 指定之檔案資料流 XML 片段的自訂座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="0b96b-127">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="0b96b-128">撰寫這個自訂座標軸的方式，就是它需要具有、和專案的檔， `Customer` `Name` `Item` 而且這些專案會依照上述檔的方式排列 `Source.xml` 。</span><span class="sxs-lookup"><span data-stu-id="0b96b-128">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="0b96b-129">它是一種簡單的執行方式。</span><span class="sxs-lookup"><span data-stu-id="0b96b-129">It's a simplistic implementation.</span></span> <span data-ttu-id="0b96b-130">較為複雜的實作方法則用於剖析無效的文件。</span><span class="sxs-lookup"><span data-stu-id="0b96b-130">A more robust implementation would be prepared to parse an invalid document.</span></span>

```csharp
static IEnumerable<XElement> StreamCustomerItem(string uri)
{
    using (XmlReader reader = XmlReader.Create(uri))
    {
        XElement name = null;
        XElement item = null;

        reader.MoveToContent();

        // Parse the file, save header information when encountered, and yield the
        // Item XElement objects as they're created.

        // loop through Customer elements
        while (reader.Read())
        {
            if (reader.NodeType == XmlNodeType.Element
                && reader.Name == "Customer")
            {
                // move to Name element
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.Element &&
                        reader.Name == "Name")
                    {
                        name = XElement.ReadFrom(reader) as XElement;
                        break;
                    }
                }

                // Loop through Item elements
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.EndElement)
                        break;
                    if (reader.NodeType == XmlNodeType.Element
                        && reader.Name == "Item")
                    {
                        item = XElement.ReadFrom(reader) as XElement;
                        if (item != null) {
                            XElement tempRoot = new XElement("Root",
                                new XElement(name)
                            );
                            tempRoot.Add(item);
                            yield return item;
                        }
                    }
                }
            }
        }
    }
}

static void Main(string[] args)
{
    XElement xmlTree = new XElement("Root",
        from el in StreamCustomerItem("Source.xml")
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7
        select new XElement("Item",
            new XElement("Customer", (string)el.Parent.Element("Name")),
            new XElement(el.Element("Key"))
        )
    );
    Console.WriteLine(xmlTree);
}
```

```vb
Module Module1

    Sub Main()
        Dim xmlTree = <Root>
                          <%=
                              From el In New StreamCustomerItem("Source.xml")
                              Let itemKey = CInt(el.<Key>.Value)
                              Where itemKey >= 3 AndAlso itemKey <= 7
                              Select <Item>
                                         <Customer><%= el.Parent.<Name>.Value %></Customer>
                                         <%= el.<Key> %>
                                     </Item>
                          %>
                      </Root>

        Console.WriteLine(xmlTree)
    End Sub

End Module

Public Class StreamCustomerItem
    Implements IEnumerable(Of XElement)

    Private _uri As String

    Public Sub New(ByVal uri As String)
        _uri = uri
    End Sub

    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator
        Return New StreamCustomerItemEnumerator(_uri)
    End Function

    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator
        Return Me.GetEnumerator()
    End Function
End Class

Public Class StreamCustomerItemEnumerator
    Implements IEnumerator(Of XElement)

    Private _current As XElement
    Private _customerName As String
    Private _reader As Xml.XmlReader
    Private _uri As String

    Public Sub New(ByVal uri As String)
        _uri = uri
        _reader = Xml.XmlReader.Create(_uri)
        _reader.MoveToContent()
    End Sub

    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current
        Get
            Return _current
        End Get
    End Property

    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current
        Get
            Return Me.Current
        End Get
    End Property

    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext
        Dim item As XElement
        Dim name As XElement

        ' Parse the file, save header information when encountered, and return the
        ' current Item XElement.

        ' loop through Customer elements
        While _reader.Read()
            If _reader.NodeType = Xml.XmlNodeType.Element Then
                Select Case _reader.Name
                    Case "Customer"
                        ' move to Name element
                        While _reader.Read()

                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso
                                _reader.Name = "Name" Then

                                name = TryCast(XElement.ReadFrom(_reader), XElement)
                                _customerName = If(name IsNot Nothing, name.Value, "")
                                Exit While
                            End If

                        End While
                    Case "Item"
                        item = TryCast(XElement.ReadFrom(_reader), XElement)
                        Dim tempRoot = <Root>
                                           <Name><%= _customerName %></Name>
                                           <%= item %>
                                       </Root>
                        _current = item
                        Return True
                End Select
            End If
        End While

        Return False
    End Function

    Public Sub Reset() Implements IEnumerator.Reset
        _reader = Xml.XmlReader.Create(_uri)
        _reader.MoveToContent()
    End Sub

#Region "IDisposable Support"
    Private disposedValue As Boolean ' To detect redundant calls

    ' IDisposable
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)
        If Not Me.disposedValue Then
            If disposing Then
                _reader.Close()
            End If
        End If
        Me.disposedValue = True
    End Sub

    Public Sub Dispose() Implements IDisposable.Dispose
        Dispose(True)
        GC.SuppressFinalize(Me)
    End Sub
#End Region

End Class
```

 <span data-ttu-id="0b96b-131">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0b96b-131">This code produces the following output:</span></span>

```xml
<Root>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0003</Key>
  </Item>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0004</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0005</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0006</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0007</Key>
  </Item>
</Root>
```
