---
title: '如何尋找具有特定專案名稱的子系（c #）'
description: 瞭解如何使用下階軸來尋找具有特定名稱的所有子系。 請參閱程式碼範例和其他資源。
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 96ebf2d10a9ed5e07aab2870142f9869903ad442
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303240"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="bd0fd-104">如何尋找具有特定專案名稱的子系（c #）</span><span class="sxs-lookup"><span data-stu-id="bd0fd-104">How to find descendants with a specific element name (C#)</span></span>
<span data-ttu-id="bd0fd-105">有時候您會想要尋找具有特定名稱的所有子代。</span><span class="sxs-lookup"><span data-stu-id="bd0fd-105">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="bd0fd-106">您可以撰寫程式碼來逐一查看所有子代，但是使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸比較容易。</span><span class="sxs-lookup"><span data-stu-id="bd0fd-106">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd0fd-107">範例</span><span class="sxs-lookup"><span data-stu-id="bd0fd-107">Example</span></span>  
 <span data-ttu-id="bd0fd-108">下列範例顯示如何根據項目名稱尋找子代。</span><span class="sxs-lookup"><span data-stu-id="bd0fd-108">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="bd0fd-109">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bd0fd-109">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="bd0fd-110">範例</span><span class="sxs-lookup"><span data-stu-id="bd0fd-110">Example</span></span>  
 <span data-ttu-id="bd0fd-111">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="bd0fd-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="bd0fd-112">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="bd0fd-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="bd0fd-113">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bd0fd-113">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd0fd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd0fd-114">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
