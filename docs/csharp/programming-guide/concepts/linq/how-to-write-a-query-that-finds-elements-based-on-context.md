---
title: 如何：撰寫可根據內容尋找項目的查詢 (C#)
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: c1c43bc47df1612be26c78351a9d30272a020160
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45987951"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="81230-102">如何：撰寫可根據內容尋找項目的查詢 (C#)</span><span class="sxs-lookup"><span data-stu-id="81230-102">How to: Write a Query that Finds Elements Based on Context (C#)</span></span>
<span data-ttu-id="81230-103">有時候您可能必須撰寫會依其內容選取項目的查詢。</span><span class="sxs-lookup"><span data-stu-id="81230-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="81230-104">您可能想要依據前面或後面的同層級項目進行篩選。</span><span class="sxs-lookup"><span data-stu-id="81230-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="81230-105">您可能想要依據子系或祖系項目進行篩選。</span><span class="sxs-lookup"><span data-stu-id="81230-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="81230-106">您僅能撰寫查詢並使用 `where` 子句中的查詢結果來達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="81230-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="81230-107">如果您必須先依據 Null 進行測試，然後再測試值，在 `let` 子句中進行查詢，然後使用 `where` 子句中的結果會比較方便。</span><span class="sxs-lookup"><span data-stu-id="81230-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81230-108">範例</span><span class="sxs-lookup"><span data-stu-id="81230-108">Example</span></span>  
 <span data-ttu-id="81230-109">下列範例會選取緊跟著 `p` 項目後面的所有 `ul` 項目。</span><span class="sxs-lookup"><span data-stu-id="81230-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="81230-110">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="81230-110">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="81230-111">範例</span><span class="sxs-lookup"><span data-stu-id="81230-111">Example</span></span>  
 <span data-ttu-id="81230-112">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="81230-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="81230-113">如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="81230-113">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="81230-114">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="81230-114">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="81230-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="81230-115">See Also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>  
- [<span data-ttu-id="81230-116">基本查詢 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="81230-116">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
