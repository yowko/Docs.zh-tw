---
title: "查詢 XDocument 與查詢 XElement (C#)"
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
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fa756d4adb1c361ef52e58bf6bdfd3bc2e31d13a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="39b23-102">查詢 XDocument 與查詢 XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="39b23-102">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="39b23-103">當您透過 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> 載入文件時，您將會注意到您必須撰寫的查詢與透過 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> 載入時撰寫的查詢稍有不同。</span><span class="sxs-lookup"><span data-stu-id="39b23-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="39b23-104">XDocument.Load 和 XElement.Load 之比較</span><span class="sxs-lookup"><span data-stu-id="39b23-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="39b23-105">當您透過 <xref:System.Xml.Linq.XElement>，將 XML 文件載入到 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> 時，XML 樹狀結構根目錄的 <xref:System.Xml.Linq.XElement> 會包含已載入之文件的根項目。</span><span class="sxs-lookup"><span data-stu-id="39b23-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="39b23-106">不過，當您透過 <xref:System.Xml.Linq.XDocument>，將相同的 XML 文件載入到 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> 時，樹狀目錄的根目錄為 <xref:System.Xml.Linq.XDocument> 節點，而已載入之文件的根項目為允許 <xref:System.Xml.Linq.XElement> 之子系 <xref:System.Xml.Linq.XDocument> 節點的項目。</span><span class="sxs-lookup"><span data-stu-id="39b23-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="39b23-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 座標軸會相對於根節點進行運算。</span><span class="sxs-lookup"><span data-stu-id="39b23-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="39b23-108">這個第一個範例會使用 <xref:System.Xml.Linq.XElement.Load%2A> 載入 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="39b23-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="39b23-109">接著，它會針對樹狀結構根目錄的子項目進行查詢。</span><span class="sxs-lookup"><span data-stu-id="39b23-109">It then queries for the child elements of the root of the tree.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="39b23-110">這個範例預期會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="39b23-110">As expected, this example produces the following output:</span></span>  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="39b23-111">下列範例與上述範例幾乎相同，不同處在於會將 XML 樹狀結構載入到 <xref:System.Xml.Linq.XDocument> 而非 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="39b23-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="39b23-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="39b23-112">This example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="39b23-113">請注意，相同的查詢會傳回一個 `Root` 節點，而非三個子節點。</span><span class="sxs-lookup"><span data-stu-id="39b23-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="39b23-114">其中一個處理方法為，在存取座標軸方法之前，先使用 <xref:System.Xml.Linq.XDocument.Root%2A> 屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="39b23-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="39b23-115">這個查詢現在會以查詢樹狀結構根目錄 <xref:System.Xml.Linq.XElement> 的相同方式執行。</span><span class="sxs-lookup"><span data-stu-id="39b23-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="39b23-116">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="39b23-116">The example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39b23-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39b23-117">See Also</span></span>  
 [<span data-ttu-id="39b23-118">基本查詢 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="39b23-118">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)

