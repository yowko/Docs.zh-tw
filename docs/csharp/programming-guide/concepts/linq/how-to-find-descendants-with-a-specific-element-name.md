---
title: HOW TO：尋找具有特定項目名稱的子系 (C#)
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 11f13dfc61e837a923cb9709301d89ff6d2149dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530385"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="27a0e-102">HOW TO：尋找具有特定項目名稱的子系 (C#)</span><span class="sxs-lookup"><span data-stu-id="27a0e-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="27a0e-103">有時候您會想要尋找具有特定名稱的所有子代。</span><span class="sxs-lookup"><span data-stu-id="27a0e-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="27a0e-104">您可以撰寫程式碼來逐一查看所有子代，但是使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸比較容易。</span><span class="sxs-lookup"><span data-stu-id="27a0e-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27a0e-105">範例</span><span class="sxs-lookup"><span data-stu-id="27a0e-105">Example</span></span>  
 <span data-ttu-id="27a0e-106">下列範例顯示如何根據項目名稱尋找子代。</span><span class="sxs-lookup"><span data-stu-id="27a0e-106">The following example shows how to find descendants based on the element name.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
IEnumerable<string> textSegs =  
    from seg in root.Descendants("t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="27a0e-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="27a0e-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="27a0e-108">範例</span><span class="sxs-lookup"><span data-stu-id="27a0e-108">Example</span></span>  
 <span data-ttu-id="27a0e-109">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="27a0e-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="27a0e-110">如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="27a0e-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root xmlns='http://www.adatum.com'>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<string> textSegs =  
    from seg in root.Descendants(ad + "t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="27a0e-111">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="27a0e-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="27a0e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27a0e-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- [<span data-ttu-id="27a0e-113">基本查詢 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="27a0e-113">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
