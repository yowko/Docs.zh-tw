---
title: "如何：使用 XPath 查詢 LINQ to XML (C#)"
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
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6d7acf7519e6ab3384f2f34b8435fe96307921f0
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="3a30b-102">如何：使用 XPath 查詢 LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3a30b-102">How to: Query LINQ to XML Using XPath (C#)</span></span>
<span data-ttu-id="3a30b-103">本主題說明可讓您使用 XPath 查詢 XML 樹狀結構的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="3a30b-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="3a30b-104">如需有關使用這些擴充方法的詳細資訊，請參閱 <xref:System.Xml.XPath.Extensions?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="3a30b-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="3a30b-105">除非您已經有非常特定的理由要使用 XPath 查詢 (例如，廣泛使用舊版程式碼)，否則，不建議搭配 LINQ to XML 使用 XPath。</span><span class="sxs-lookup"><span data-stu-id="3a30b-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="3a30b-106">XPath 查詢將不會與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢一起執行。</span><span class="sxs-lookup"><span data-stu-id="3a30b-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a30b-107">範例</span><span class="sxs-lookup"><span data-stu-id="3a30b-107">Example</span></span>  
 <span data-ttu-id="3a30b-108">下列範例會建立小型 XML 樹狀結構，並使用 <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 來選取一組項目。</span><span class="sxs-lookup"><span data-stu-id="3a30b-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="3a30b-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="3a30b-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a30b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a30b-110">See Also</span></span>  
 [<span data-ttu-id="3a30b-111">進階查詢技術 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3a30b-111">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)

