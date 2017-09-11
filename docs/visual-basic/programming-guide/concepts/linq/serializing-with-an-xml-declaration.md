---
title: "序列化使用 XML 宣告 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 50707da956df593f176764bed94adfc6aec3dfa5
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="7dda1-102">使用 XML 宣告 (Visual Basic) 進行序列化</span><span class="sxs-lookup"><span data-stu-id="7dda1-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="7dda1-103">這個主題描述如何控制序列化是否產生 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="7dda1-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="7dda1-104">XML 宣告產生</span><span class="sxs-lookup"><span data-stu-id="7dda1-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="7dda1-105">序列化至<xref:System.IO.File>或<xref:System.IO.TextWriter>使用<xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>方法或<xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>方法會產生 XML 宣告。</xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="7dda1-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName> method generates an XML declaration.</span></span> <span data-ttu-id="7dda1-106">當您序列化<xref:System.Xml.XmlWriter>，寫入器設定 (在指定<xref:System.Xml.XmlWriterSettings>物件) 決定是否產生 XML 宣告。</xref:System.Xml.XmlWriterSettings> </xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="7dda1-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="7dda1-107">如果您要使用 `ToString` 方法序列化為字串，所產生的 XML 將不會包含 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="7dda1-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="7dda1-108">使用 XML 宣告進行序列化</span><span class="sxs-lookup"><span data-stu-id="7dda1-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="7dda1-109">下列範例會建立<xref:System.Xml.Linq.XElement>，將文件儲存至檔案，然後會列印到主控台檔案︰</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="7dda1-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="7dda1-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7dda1-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="7dda1-111">不使用 XML 宣告序列化</span><span class="sxs-lookup"><span data-stu-id="7dda1-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="7dda1-112">下列範例顯示如何將儲存<xref:System.Xml.Linq.XElement>至<xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="7dda1-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="7dda1-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7dda1-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7dda1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dda1-114">See Also</span></span>  
 [<span data-ttu-id="7dda1-115">序列化 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dda1-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
