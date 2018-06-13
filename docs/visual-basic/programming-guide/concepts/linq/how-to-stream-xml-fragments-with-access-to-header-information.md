---
title: 如何： 串流 XML 片段，以存取標頭資訊 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 60ec63c33d20fa38bed32d9c46c4acfe649ecd15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644468"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a><span data-ttu-id="03999-102">如何： 串流 XML 片段，以存取標頭資訊 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03999-102">How to: Stream XML Fragments with Access to Header Information (Visual Basic)</span></span>
<span data-ttu-id="03999-103">有時候您必須讀取任意大的 XML 檔案並撰寫您的應用程式，讓應用程式的記憶體使用量可以預測。</span><span class="sxs-lookup"><span data-stu-id="03999-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="03999-104">如果您嘗試使用大型 XML 檔案填入 XML 樹狀結構，您的記憶體使用量將與檔案大小成正比，也就是，變成過度。</span><span class="sxs-lookup"><span data-stu-id="03999-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="03999-105">因此，您應該改用資料流技術。</span><span class="sxs-lookup"><span data-stu-id="03999-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="03999-106">其中一個選項是使用 <xref:System.Xml.XmlReader> 撰寫您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="03999-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="03999-107">但是，您可能想要使用 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="03999-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="03999-108">若發生這種情況，您可以撰寫自己的自訂座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="03999-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="03999-109">如需詳細資訊，請參閱[How to： 撰寫 LINQ to XML 軸心方法 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)。</span><span class="sxs-lookup"><span data-stu-id="03999-109">For more information, see [How to: Write a LINQ to XML Axis Method (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="03999-110">若要撰寫您自己的座標軸方法，您可以撰寫使用 <xref:System.Xml.XmlReader> 讀取節點的小方法，直到該方法到達您感興趣的其中一個節點。</span><span class="sxs-lookup"><span data-stu-id="03999-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="03999-111">然後，該方法會呼叫從 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 讀取的 <xref:System.Xml.XmlReader>，並具現化 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="03999-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="03999-112">此時，您就可以在自訂座標軸方法上撰寫 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="03999-112">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="03999-113">在您僅需要處理一次來源文件的情況下，最適合使用資料流技術，而且您可以用文件的順序處理項目。</span><span class="sxs-lookup"><span data-stu-id="03999-113">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="03999-114">特定的標準查詢運算子 (例如，<xref:System.Linq.Enumerable.OrderBy%2A>) 會反覆查看其來源、收集所有資料、排序這些資料，最後產生順序中的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="03999-114">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="03999-115">請注意，如果您在產生第一個項目前使用具體化其來源的查詢運算子，您將不會保留小的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="03999-115">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03999-116">範例</span><span class="sxs-lookup"><span data-stu-id="03999-116">Example</span></span>  
 <span data-ttu-id="03999-117">有時候問題會變得更有趣。</span><span class="sxs-lookup"><span data-stu-id="03999-117">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="03999-118">在下列 XML 文件中，您自訂座標軸方法的消費者也必須知道每個項目所屬客戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="03999-118">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="03999-119">這個範例所採取的方法也是監看這個標頭資訊、儲存標頭資訊，然後建置同時包含您所列舉之標頭資訊與細節的小型 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="03999-119">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="03999-120">這個座標軸方法接著就會產生這個新的小型 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="03999-120">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="03999-121">該查詢將可以存取標頭資訊以及詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="03999-121">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="03999-122">此方法擁有小的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="03999-122">This approach has a small memory footprint.</span></span> <span data-ttu-id="03999-123">產生每個細節 XML 片段時，不會針對上一個片段保留任何參考，而且這個片段適用於記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="03999-123">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="03999-124">請注意，這個技術會在堆積上建立許多短期存在的物件。</span><span class="sxs-lookup"><span data-stu-id="03999-124">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="03999-125">下列範例顯示如何實作與使用從 URI 指定之檔案資料流 XML 片段的自訂座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="03999-125">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="03999-126">這個自訂座標軸是特別撰寫的，讓它預備擁有 `Customer`、`Name` 和 `Item` 項目的文件，並預期這些項目將會與上述 `Source.xml` 文件的排列方式相同。</span><span class="sxs-lookup"><span data-stu-id="03999-126">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="03999-127">這是簡化的實作方法。</span><span class="sxs-lookup"><span data-stu-id="03999-127">It is a simplistic implementation.</span></span> <span data-ttu-id="03999-128">較為複雜的實作方法則用於剖析無效的文件。</span><span class="sxs-lookup"><span data-stu-id="03999-128">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="03999-129">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="03999-129">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03999-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03999-130">See Also</span></span>  
 [<span data-ttu-id="03999-131">進階的 LINQ to XML 程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03999-131">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
