---
title: "如何：尋找子項目的子系 (XPath-LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 873cfe6a725a932ac4616e7ccf0ea11e3f6479f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="d073b-102">如何：尋找子項目的子系 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d073b-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="d073b-103">本主題顯示如何利用特定名稱取得子項目的子代項目。</span><span class="sxs-lookup"><span data-stu-id="d073b-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="d073b-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="d073b-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="d073b-105">範例</span><span class="sxs-lookup"><span data-stu-id="d073b-105">Example</span></span>  
 <span data-ttu-id="d073b-106">此範例模擬從字組處理文件的 XML 表示擷取文字的問題。</span><span class="sxs-lookup"><span data-stu-id="d073b-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="d073b-107">它會先選取所有 `Paragraph` 項目，然後它會選取每個 `Text` 項目的所有 `Paragraph` 子代項目。</span><span class="sxs-lookup"><span data-stu-id="d073b-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="d073b-108">這不會選取 `Text` 項目的子代 `Comment` 項目。</span><span class="sxs-lookup"><span data-stu-id="d073b-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root>  
  <Paragraph>  
    <Text>This is the start of</Text>  
  </Paragraph>  
  <Comment>  
    <Text>This comment is not part of the paragraph text.</Text>  
  </Comment>  
  <Paragraph>  
    <Annotation Emphasis='true'>  
      <Text> a sentence.</Text>  
    </Annotation>  
  </Paragraph>  
  <Paragraph>  
    <Text>  This is a second sentence.</Text>  
  </Paragraph>  
</Root>");  
  
// LINQ to XML query  
string str1 =  
    root  
    .Elements("Paragraph")  
    .Descendants("Text")  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
// XPath expression  
string str2 =  
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))  
    .Cast<XText>()  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
if (str1 == str2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(str2);  
```  
  
 <span data-ttu-id="d073b-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d073b-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a><span data-ttu-id="d073b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d073b-110">See Also</span></span>  
 [<span data-ttu-id="d073b-111">XPath 使用者適用的 LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d073b-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
