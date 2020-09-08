---
title: 使用 XML 宣告進行序列化-LINQ to XML
description: '您可以控制當您在 c # 或 Visual Basic 中序列化 XML 時，是否產生 XML 宣告。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 8d25d199b149ac6aeb2aa37dc248523e79847220
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552118"
---
# <a name="serialize-with-an-xml-declaration-linq-to-xml"></a><span data-ttu-id="ddb5d-103">使用 XML 宣告進行序列化 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="ddb5d-103">Serialize with an XML declaration (LINQ to XML)</span></span>

<span data-ttu-id="ddb5d-104">本文描述如何在您使用 c # 或 Visual Basic 序列化 XML 時，控制是否產生 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="ddb5d-104">This article describes how to control whether an XML declaration is generated when you serialize XML in C# or Visual Basic.</span></span>

<span data-ttu-id="ddb5d-105">使用 <xref:System.IO.File> 方法或 <xref:System.IO.TextWriter> 方法序列化為 <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> 或 <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> 會產生 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="ddb5d-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="ddb5d-106">當您序列化為時 <xref:System.Xml.XmlWriter> ，會在物件中指定 (寫入器設定， <xref:System.Xml.XmlWriterSettings>) 判斷是否產生 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="ddb5d-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated.</span></span>

<span data-ttu-id="ddb5d-107">如果您要使用方法序列化至字串 `ToString` ，產生的 xml 將不會包含 xml 宣告。</span><span class="sxs-lookup"><span data-stu-id="ddb5d-107">If you're serializing to a string using the `ToString` method, the resulting XML won't include an XML declaration.</span></span>

## <a name="example-serialize-with-an-xml-declaration"></a><span data-ttu-id="ddb5d-108">範例：使用 XML 宣告進行序列化</span><span class="sxs-lookup"><span data-stu-id="ddb5d-108">Example: Serialize with an XML declaration</span></span>

<span data-ttu-id="ddb5d-109">下列範例會建立 <xref:System.Xml.Linq.XElement>、將文件儲存為檔案，然後將檔案列印到主控台：</span><span class="sxs-lookup"><span data-stu-id="ddb5d-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Child", "child content")
);
root.Save("Root.xml");
string str = File.ReadAllText("Root.xml");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root>
                           <Child>child content</Child>
                       </Root>
root.Save("Root.xml")
Dim str As String = File.ReadAllText("Root.xml")
Console.WriteLine(str)
```

<span data-ttu-id="ddb5d-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="ddb5d-110">This example produces the following output:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Root>
  <Child>child content</Child>
</Root>
```

## <a name="example-serialize-without-an-xml-declaration"></a><span data-ttu-id="ddb5d-111">範例：不使用 XML 宣告進行序列化</span><span class="sxs-lookup"><span data-stu-id="ddb5d-111">Example: Serialize without an XML declaration</span></span>

<span data-ttu-id="ddb5d-112">下列範例顯示如何將 <xref:System.Xml.Linq.XElement> 儲存為 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="ddb5d-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>

```csharp
StringBuilder sb = new StringBuilder();
XmlWriterSettings xws = new XmlWriterSettings();
xws.OmitXmlDeclaration = true;

using (XmlWriter xw = XmlWriter.Create(sb, xws)) {
    XElement root = new XElement("Root",
        new XElement("Child", "child content")
    );
    root.Save(xw);
}
Console.WriteLine(sb.ToString());
```

```vb
Dim sb As StringBuilder = New StringBuilder()
Dim xws As XmlWriterSettings = New XmlWriterSettings()
xws.OmitXmlDeclaration = True

Using xw As XmlWriter = XmlWriter.Create(sb, xws)
    Dim root = <Root>
                   <Child>child content</Child>
               </Root>
    root.Save(xw)
End Using
Console.WriteLine(sb.ToString())
```

<span data-ttu-id="ddb5d-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="ddb5d-113">This example produces the following output:</span></span>

```xml
<Root><Child>child content</Child></Root>
```
