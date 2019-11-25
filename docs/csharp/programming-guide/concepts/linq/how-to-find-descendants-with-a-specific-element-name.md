---
title: 如何尋找具有特定專案名稱的子系（C#）
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: b3200a2fdf75dbf52079a2b3d27aa1a88d313406
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141087"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="cd0ab-102">如何尋找具有特定專案名稱的子系（C#）</span><span class="sxs-lookup"><span data-stu-id="cd0ab-102">How to find descendants with a specific element name (C#)</span></span>
<span data-ttu-id="cd0ab-103">有時候您會想要尋找具有特定名稱的所有子代。</span><span class="sxs-lookup"><span data-stu-id="cd0ab-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="cd0ab-104">您可以撰寫程式碼來逐一查看所有子代，但是使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸比較容易。</span><span class="sxs-lookup"><span data-stu-id="cd0ab-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd0ab-105">範例</span><span class="sxs-lookup"><span data-stu-id="cd0ab-105">Example</span></span>  
 <span data-ttu-id="cd0ab-106">下列範例顯示如何根據項目名稱尋找子代。</span><span class="sxs-lookup"><span data-stu-id="cd0ab-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="cd0ab-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="cd0ab-107">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="cd0ab-108">範例</span><span class="sxs-lookup"><span data-stu-id="cd0ab-108">Example</span></span>  
 <span data-ttu-id="cd0ab-109">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="cd0ab-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="cd0ab-110">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="cd0ab-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="cd0ab-111">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="cd0ab-111">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd0ab-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd0ab-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
