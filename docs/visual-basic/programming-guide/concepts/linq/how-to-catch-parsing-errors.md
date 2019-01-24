---
title: HOW TO：攔截剖析錯誤 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: f438a247866fdea8935be2b881a77f97c152b98f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667081"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="23bdc-102">HOW TO：攔截剖析錯誤 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23bdc-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="23bdc-103">這個主題顯示如何偵測格式錯誤或無效的 XML。</span><span class="sxs-lookup"><span data-stu-id="23bdc-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="23bdc-104">是使用 <xref:System.Xml.XmlReader> 實作的。</span><span class="sxs-lookup"><span data-stu-id="23bdc-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="23bdc-105">如果將格式錯誤或無效的 XML 傳遞到 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，基礎 <xref:System.Xml.XmlReader> 類別將會擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="23bdc-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="23bdc-106">剖析 XML 的各種方法 (例如，<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>) 不會攔截例外狀況。然後，您的應用程式就可以攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="23bdc-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="23bdc-107">請注意，如果您使用 XML 常值，就無法取得剖析錯誤。</span><span class="sxs-lookup"><span data-stu-id="23bdc-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="23bdc-108">Visual Basic 編譯器將會攔截格式錯誤或無效 XML 的錯誤。</span><span class="sxs-lookup"><span data-stu-id="23bdc-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23bdc-109">範例</span><span class="sxs-lookup"><span data-stu-id="23bdc-109">Example</span></span>  
 <span data-ttu-id="23bdc-110">下列程式碼嘗試剖析無效的 XML：</span><span class="sxs-lookup"><span data-stu-id="23bdc-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="23bdc-111">執行此程式碼時，它會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="23bdc-111">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="23bdc-112">如需可以預期 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 及 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 方法擲回之例外狀況的詳細資訊，請參閱 <xref:System.Xml.XmlReader> 文件。</span><span class="sxs-lookup"><span data-stu-id="23bdc-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23bdc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23bdc-113">See also</span></span>
- [<span data-ttu-id="23bdc-114">剖析 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23bdc-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
