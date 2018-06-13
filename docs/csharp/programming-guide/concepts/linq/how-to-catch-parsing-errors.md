---
title: 如何：攔截剖析錯誤 (C#)
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 037e490fa7b0600b906ec310201e5d33c2f55baa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333381"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="6f168-102">如何：攔截剖析錯誤 (C#)</span><span class="sxs-lookup"><span data-stu-id="6f168-102">How to: Catch Parsing Errors (C#)</span></span>
<span data-ttu-id="6f168-103">這個主題顯示如何偵測格式錯誤或無效的 XML。</span><span class="sxs-lookup"><span data-stu-id="6f168-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="6f168-104"> 是使用 <xref:System.Xml.XmlReader> 實作的。</span><span class="sxs-lookup"><span data-stu-id="6f168-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="6f168-105">如果將格式錯誤或無效的 XML 傳遞到 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，基礎 <xref:System.Xml.XmlReader> 類別將會擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6f168-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="6f168-106">剖析 XML 的各種方法 (例如，<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>) 不會攔截例外狀況。然後，您的應用程式就可以攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6f168-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f168-107">範例</span><span class="sxs-lookup"><span data-stu-id="6f168-107">Example</span></span>  
 <span data-ttu-id="6f168-108">下列程式碼嘗試剖析無效的 XML：</span><span class="sxs-lookup"><span data-stu-id="6f168-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="6f168-109">執行此程式碼時，它會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="6f168-109">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="6f168-110">如需可以預期 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 及 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 方法擲回之例外狀況的詳細資訊，請參閱 <xref:System.Xml.XmlReader> 文件。</span><span class="sxs-lookup"><span data-stu-id="6f168-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f168-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="6f168-111">See Also</span></span>  
 [<span data-ttu-id="6f168-112">剖析 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6f168-112">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
