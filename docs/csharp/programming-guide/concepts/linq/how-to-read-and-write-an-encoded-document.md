---
title: "如何：讀取和寫入編碼的文件 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a08fa9404c92bd64b07059df2f419bff5f80da3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a><span data-ttu-id="83102-102">如何：讀取和寫入編碼的文件 (C#)</span><span class="sxs-lookup"><span data-stu-id="83102-102">How to: Read and Write an Encoded Document (C#)</span></span>
<span data-ttu-id="83102-103">若要建立編碼的 XML 文件，您可以將編碼設定為所需的字碼頁名稱，以便將 <xref:System.Xml.Linq.XDeclaration> 加入到 XML 樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="83102-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>  
  
 <span data-ttu-id="83102-104">由 <xref:System.Text.Encoding.WebName%2A> 傳回的任何值都是有效的值。</span><span class="sxs-lookup"><span data-stu-id="83102-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>  
  
 <span data-ttu-id="83102-105">如果您要讀取加密的文件，<xref:System.Xml.Linq.XDeclaration.Encoding%2A> 屬性將會設定為字碼頁名稱。</span><span class="sxs-lookup"><span data-stu-id="83102-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>  
  
 <span data-ttu-id="83102-106">如果您將 <xref:System.Xml.Linq.XDeclaration.Encoding%2A> 設定為有效的字碼頁名稱，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會使用指定的編碼序列化。</span><span class="sxs-lookup"><span data-stu-id="83102-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83102-107">範例</span><span class="sxs-lookup"><span data-stu-id="83102-107">Example</span></span>  
 <span data-ttu-id="83102-108">下列範例會建立兩個文件，其中一個編碼為 utf-8，而另一個編碼為 utf-16。</span><span class="sxs-lookup"><span data-stu-id="83102-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="83102-109">然後，會載入文件並將編碼方式列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="83102-109">It then loads the documents and prints the encoding to the console.</span></span>  
  
```csharp  
Console.WriteLine("Creating a document with utf-8 encoding");  
XDocument encodedDoc8 = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc8.Save("EncodedUtf8.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
Console.WriteLine("Creating a document with utf-16 encoding");  
XDocument encodedDoc16 = new XDocument(  
    new XDeclaration("1.0", "utf-16", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc16.Save("EncodedUtf16.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc8 = XDocument.Load("EncodedUtf8.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc16 = XDocument.Load("EncodedUtf16.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding);  
```  
  
 <span data-ttu-id="83102-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="83102-110">This example produces the following output:</span></span>  
  
```  
Creating a document with utf-8 encoding  
Encoding is:utf-8  
  
Creating a document with utf-16 encoding  
Encoding is:utf-16  
  
Encoded document:  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-8  
  
Encoded document:  
<?xml version="1.0" encoding="utf-16" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-16  
```  
  
## <a name="see-also"></a><span data-ttu-id="83102-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83102-111">See Also</span></span>  
 <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="83102-112">進階 LINQ to XML 程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="83102-112">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
