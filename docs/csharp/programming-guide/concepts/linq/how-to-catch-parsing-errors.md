---
title: "如何：攔截剖析錯誤 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: ef6f836033a5f46bffc4354c8468c7e8efa82854
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="d45c8-102">如何：攔截剖析錯誤 (C#)</span><span class="sxs-lookup"><span data-stu-id="d45c8-102">How to: Catch Parsing Errors (C#)</span></span>
<span data-ttu-id="d45c8-103">這個主題顯示如何偵測格式錯誤或無效的 XML。</span><span class="sxs-lookup"><span data-stu-id="d45c8-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 <span data-ttu-id="d45c8-104">使用 <xref:System.Xml.XmlReader> 實作 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d45c8-104">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d45c8-105">如果將格式錯誤或無效的 XML 傳遞到 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]，基礎 <xref:System.Xml.XmlReader> 類別會擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d45c8-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="d45c8-106">剖析 XML 的各種方法 (例如 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>) 不會攔截例外狀況。然後，您的應用程式就可以攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d45c8-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d45c8-107">範例</span><span class="sxs-lookup"><span data-stu-id="d45c8-107">Example</span></span>  
 <span data-ttu-id="d45c8-108">下列程式碼嘗試剖析無效的 XML：</span><span class="sxs-lookup"><span data-stu-id="d45c8-108">The following code tries to parse invalid XML:</span></span>  
  
```csharp  
try {  
    XElement contacts = XElement.Parse(  
        @"<Contacts>  
            <Contact>  
                <Name>Jim Wilson</Name>  
            </Contact>  
          </Contcts>");  
  
    Console.WriteLine(contacts);  
}  
catch (System.Xml.XmlException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
 <span data-ttu-id="d45c8-109">執行此程式碼時，它會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="d45c8-109">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="d45c8-110">如需預期 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> 和 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> 方法擲回之例外狀況的資訊，請參閱 <xref:System.Xml.XmlReader> 文件。</span><span class="sxs-lookup"><span data-stu-id="d45c8-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d45c8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d45c8-111">See Also</span></span>  
 [<span data-ttu-id="d45c8-112">剖析 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d45c8-112">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
