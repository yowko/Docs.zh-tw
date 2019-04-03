---
title: HOW TO：控制命名空間前置詞 (Visual Basic) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 7e5a05d2fa93e61338f450d0a4d890fa94c04fd2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839008"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="fea21-102">HOW TO：控制命名空間前置詞 (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="fea21-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="fea21-103">這個主題描述如何控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="fea21-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fea21-104">範例</span><span class="sxs-lookup"><span data-stu-id="fea21-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="fea21-105">描述</span><span class="sxs-lookup"><span data-stu-id="fea21-105">Description</span></span>  
 <span data-ttu-id="fea21-106">這個範例會宣告兩個命名空間。</span><span class="sxs-lookup"><span data-stu-id="fea21-106">This example declares two namespaces.</span></span> <span data-ttu-id="fea21-107">它會指定`http://www.adventure-works.com`命名空間具有前置詞`aw`，且`www.fourthcoffee.com`命名空間具有的前置詞`fc`。</span><span class="sxs-lookup"><span data-stu-id="fea21-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fea21-108">程式碼</span><span class="sxs-lookup"><span data-stu-id="fea21-108">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="fea21-109">註解</span><span class="sxs-lookup"><span data-stu-id="fea21-109">Comments</span></span>  
 <span data-ttu-id="fea21-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fea21-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fea21-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fea21-111">See also</span></span>

- [<span data-ttu-id="fea21-112">處理 XML 命名空間 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fea21-112">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
