---
title: "如何︰ 攔截剖析錯誤 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
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
ms.openlocfilehash: 6065bb7656151392e4a5b7ad1078706284ba5616
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="db804-102">如何︰ 攔截剖析錯誤 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db804-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="db804-103">這個主題顯示如何偵測格式錯誤或無效的 XML。</span><span class="sxs-lookup"><span data-stu-id="db804-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="db804-104">使用<xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader>實作</span><span class="sxs-lookup"><span data-stu-id="db804-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="db804-105">如果將格式錯誤或無效的 XML 傳遞到[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]，基礎<xref:System.Xml.XmlReader>類別將會擲回例外狀況。</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="db804-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="db804-106">這類剖析 XML 的各種方法<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>，不會攔截例外狀況，然後根據您的應用程式攔截例外狀況。</xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="db804-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="db804-107">請注意，如果您使用 XML 常值，就無法取得剖析錯誤。</span><span class="sxs-lookup"><span data-stu-id="db804-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="db804-108">Visual Basic 編譯器將會攔截格式錯誤或無效 XML 的錯誤。</span><span class="sxs-lookup"><span data-stu-id="db804-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db804-109">範例</span><span class="sxs-lookup"><span data-stu-id="db804-109">Example</span></span>  
 <span data-ttu-id="db804-110">下列程式碼嘗試剖析無效的 XML：</span><span class="sxs-lookup"><span data-stu-id="db804-110">The following code tries to parse invalid XML:</span></span>  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 <span data-ttu-id="db804-111">執行此程式碼時，它會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="db804-111">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="db804-112">如需有關您可以預期的例外狀況資訊<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>， <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>， <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>，和<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>方法擲回，請參閱<xref:System.Xml.XmlReader>文件。</xref:System.Xml.XmlReader> </xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="db804-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db804-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db804-113">See Also</span></span>  
 [<span data-ttu-id="db804-114">剖析 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db804-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
