---
title: '如何篩選選擇性元素（c #）'
description: 瞭解如何篩選選擇性元素，即使您不確定它是否存在於 XML 檔中。
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: a1cd93b70ea2c077437b58bd341f51f15f014871
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302863"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="06aae-103">如何篩選選擇性元素（c #）</span><span class="sxs-lookup"><span data-stu-id="06aae-103">How to filter on an optional element (C#)</span></span>
<span data-ttu-id="06aae-104">有時候即使您不確定項目是否存在於 XML 文件中，您都會想要針對該項目進行篩選。</span><span class="sxs-lookup"><span data-stu-id="06aae-104">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="06aae-105">搜尋應該會執行，因此，如果特定的項目沒有子項目，您就不會篩選該項目來觸發 Null 參考例外狀況。</span><span class="sxs-lookup"><span data-stu-id="06aae-105">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="06aae-106">在下列範例中，`Child5` 項目沒有 `Type` 子項目，但查詢仍會正確執行。</span><span class="sxs-lookup"><span data-stu-id="06aae-106">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06aae-107">範例</span><span class="sxs-lookup"><span data-stu-id="06aae-107">Example</span></span>  
 <span data-ttu-id="06aae-108">此範例使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="06aae-108">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
var cList =  
    from typeElement in root.Elements().Elements("Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element("Text");  
foreach(string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="06aae-109">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="06aae-109">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="06aae-110">範例</span><span class="sxs-lookup"><span data-stu-id="06aae-110">Example</span></span>  
 <span data-ttu-id="06aae-111">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="06aae-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="06aae-112">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="06aae-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
XNamespace ad = "http://www.adatum.com";  
var cList =  
    from typeElement in root.Elements().Elements(ad + "Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element(ad + "Text");  
foreach (string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="06aae-113">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="06aae-113">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="06aae-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06aae-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="06aae-115">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="06aae-115">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="06aae-116">投射作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="06aae-116">Projection Operations (C#)</span></span>](./projection-operations.md)
