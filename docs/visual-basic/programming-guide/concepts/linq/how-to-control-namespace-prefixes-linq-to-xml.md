---
title: "如何︰ 控制命名空間前置詞 (Visual Basic) (LINQ to XML) |Microsoft 文件"
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
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 87db9e5384bee835ca4fde141765eabf9a7cfedb
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="c0909-102">如何：控制命名空間前置字元 (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c0909-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="c0909-103">這個主題描述如何控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="c0909-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0909-104">範例</span><span class="sxs-lookup"><span data-stu-id="c0909-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c0909-105">描述</span><span class="sxs-lookup"><span data-stu-id="c0909-105">Description</span></span>  
 <span data-ttu-id="c0909-106">這個範例會宣告兩個命名空間。</span><span class="sxs-lookup"><span data-stu-id="c0909-106">This example declares two namespaces.</span></span> <span data-ttu-id="c0909-107">它會指定`http://www.adventure-works.com`命名空間的前置詞`aw`，而且`www.fourthcoffee.com`命名空間的前置詞的`fc`。</span><span class="sxs-lookup"><span data-stu-id="c0909-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c0909-108">程式碼</span><span class="sxs-lookup"><span data-stu-id="c0909-108">Code</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="c0909-109">註解</span><span class="sxs-lookup"><span data-stu-id="c0909-109">Comments</span></span>  
 <span data-ttu-id="c0909-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="c0909-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0909-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0909-111">See Also</span></span>  
 [<span data-ttu-id="c0909-112">處理 XML 命名空間 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0909-112">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
