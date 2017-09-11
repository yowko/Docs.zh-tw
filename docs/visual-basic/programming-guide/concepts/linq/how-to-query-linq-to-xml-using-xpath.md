---
title: "如何︰ 查詢 LINQ to XML 使用 XPath (Visual Basic) |Microsoft 文件"
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
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 586182367ea26539384ea630dde301fe447915b8
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="f8cf3-102">如何︰ 查詢 LINQ to XML 使用 XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8cf3-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="f8cf3-103">本主題說明可讓您使用 XPath 查詢 XML 樹狀結構的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="f8cf3-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="f8cf3-104">如需使用這些擴充方法的詳細資訊，請參閱<xref:System.Xml.XPath.Extensions?displayProperty=fullName>。</xref:System.Xml.XPath.Extensions?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f8cf3-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="f8cf3-105">除非您已經有非常特定的理由要使用 XPath 查詢 (例如，廣泛使用舊版程式碼)，否則，不建議搭配 LINQ to XML 使用 XPath。</span><span class="sxs-lookup"><span data-stu-id="f8cf3-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="f8cf3-106">將不會執行 XPath 查詢以及[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="f8cf3-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8cf3-107">範例</span><span class="sxs-lookup"><span data-stu-id="f8cf3-107">Example</span></span>  
 <span data-ttu-id="f8cf3-108">下列範例會建立小型 XML 樹狀結構，並使用<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A>來選取一組項目。</xref:System.Xml.XPath.Extensions.XPathSelectElements%2A></span><span class="sxs-lookup"><span data-stu-id="f8cf3-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="f8cf3-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f8cf3-109">This example produces the following output:</span></span>  
  
```  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8cf3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8cf3-110">See Also</span></span>  
 [<span data-ttu-id="f8cf3-111">進階查詢技術 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8cf3-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)

