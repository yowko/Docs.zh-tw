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
ms.openlocfilehash: 58f32dcb76246bed1030f3d0a45db2541f381877
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43390724"
---
# <a name="extending-the-dom"></a>擴充 DOM

Microsoft .NET Framework 含有可提供 XML 文件物件模型 (DOM) 之實作的基底類別組。 <xref:System.Xml.XmlNode> 及其衍生類別會提供方法和屬性，讓您巡覽、查詢和修改 XML 文件的內容和結構。

當 XML 內容載入使用 DOM 的記憶體時，建立的節點包含資訊，例如節點名稱、節點型別等等。 有時您可能會需要基底類別所沒有提供的特定節點資訊。 例如，您可能想要查看節點的行號和位置。 在這個案例中，您可以從現有 DOM 類別衍生新類別並且加入其他功能。

衍生新類別時有兩個一般方針：

- 建議您絕不要從 <xref:System.Xml.XmlNode> 類別中進行衍生。 建議您從感興趣之節點型別的對應類別來衍生類別。 例如，如果您要傳回屬性節點的其他資訊，則可以從 <xref:System.Xml.XmlAttribute> 類別加以衍生。

- 除了節點建立方法之外，建議在覆寫函式時，您一定要呼叫函式的基底版本，然後加入其他任何的處理。

## <a name="creating-your-own-node-instances"></a>建立您自己的節點執行個體

<xref:System.Xml.XmlDocument> 類別包含節點建立方法。 當 XML 檔載入時，會呼叫這些方法來建立節點。 您可以覆寫這些方法，這樣就會在文件載入時建立您的節點執行個體。 例如，如果擴充了 <xref:System.Xml.XmlElement> 類別，則會繼承 <xref:System.Xml.XmlDocument> 類別，並覆寫 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法。

下列範例顯示如何覆寫 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法，以傳回 <xref:System.Xml.XmlElement> 類別的實作。

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

## <a name="extending-a-class"></a>擴充類別

若要擴充類別，請從其中一個現有的 DOM 類別衍生您的類別。 接著您可以覆寫基底類別中的虛擬方法或屬性，或加入您自己的方法或屬性。

在下列範例中會建立新類別，此新類別會實作 <xref:System.Xml.XmlElement> 類別和 <xref:System.Xml.IXmlLineInfo> 介面。 其他的方法和屬性會定義何者可讓使用者獲得指令行資訊。

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

### <a name="example"></a>範例

下列範例計算 XML 文件中項目的數目：

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

#### <a name="input"></a>輸入

book.xml

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a>輸出

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a>節點事件處理常式

DOM 的 .NET Framework 實作也包含一個事件系統，當 XML 文件中的節點變更時，可以讓您接收和處理事件。 使用 <xref:System.Xml.XmlNodeChangedEventHandler> 和 <xref:System.Xml.XmlNodeChangedEventArgs> 類別，您可以擷取 `NodeChanged`、`NodeChanging`、`NodeInserted`、`NodeInserting`、`NodeRemoved` 和 `NodeRemoving` 事件。

事件處理程序在衍生類別中的執行方式，與在原始 DOM 類別中的執行方式相同。

如需有關節點事件處理的詳細資訊，請參閱[事件](../../../../docs/standard/events/index.md)和 <xref:System.Xml.XmlNodeChangedEventHandler>。

## <a name="default-attributes-and-the-createelement-method"></a>預設屬性和 CreateElement 方法

如果要在衍生類別中覆寫 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法，則編輯文件而建立新項目時，將不會加入預設屬性。 這只是在編輯時才會發生的問題。 因為 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法負責將預設屬性加入 <xref:System.Xml.XmlDocument>，所以您必須將此功能以程式碼編寫在 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法中。 如果載入含有預設屬性的 <xref:System.Xml.XmlDocument>，則會正確處理它們。 如需有關預設屬性的詳細資訊，請參閱[為 DOM 中的項目建立新屬性](creating-new-attributes-for-elements-in-the-dom.md)。

## <a name="see-also"></a>請參閱

[XML 文件物件模型 (DOM)](xml-document-object-model-dom.md)  
