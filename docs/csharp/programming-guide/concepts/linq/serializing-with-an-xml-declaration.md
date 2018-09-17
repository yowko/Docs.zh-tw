---
title: 使用 XML 宣告序列化 (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 613280efc8c734c53c4af9252b4b83e2dd942f36
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45597291"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="88e3b-102">使用 XML 宣告序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="88e3b-102">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="88e3b-103">這個主題描述如何控制序列化是否產生 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="88e3b-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="88e3b-104">XML 宣告產生</span><span class="sxs-lookup"><span data-stu-id="88e3b-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="88e3b-105">使用 <xref:System.IO.File> 方法或 <xref:System.IO.TextWriter> 方法序列化為 <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> 或 <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> 會產生 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="88e3b-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="88e3b-106">當您序列化為 <xref:System.Xml.XmlWriter> 時，寫入器設定 (在 <xref:System.Xml.XmlWriterSettings> 物件中指定) 會決定是否產生 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="88e3b-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="88e3b-107">如果您要使用 `ToString` 方法序列化為字串，所產生的 XML 將不會包含 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="88e3b-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="88e3b-108">使用 XML 宣告進行序列化</span><span class="sxs-lookup"><span data-stu-id="88e3b-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="88e3b-109">下列範例會建立 <xref:System.Xml.Linq.XElement>、將文件儲存為檔案，然後將檔案列印到主控台：</span><span class="sxs-lookup"><span data-stu-id="88e3b-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="88e3b-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="88e3b-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="88e3b-111">不使用 XML 宣告序列化</span><span class="sxs-lookup"><span data-stu-id="88e3b-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="88e3b-112">下列範例顯示如何將 <xref:System.Xml.Linq.XElement> 儲存為 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="88e3b-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="88e3b-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="88e3b-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="88e3b-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="88e3b-114">See Also</span></span>

- [<span data-ttu-id="88e3b-115">序列化 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="88e3b-115">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
