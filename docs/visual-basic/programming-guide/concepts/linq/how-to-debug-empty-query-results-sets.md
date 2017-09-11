---
title: "如何︰ 偵錯空白查詢結果集 (Visual Basic) |Microsoft 文件"
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
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 85a0d070c415924ef116367b0202c01bef6d8ace
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="ffbae-102">如何︰ 偵錯空白查詢結果集 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffbae-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>
<span data-ttu-id="ffbae-103">查詢 XML 時所遇到的其中一個最常見的問題是，如果 XML 樹狀結構有預設的命名空間，即使 XML 不在命名空間中，開發人員有時候還是會撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="ffbae-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="ffbae-104">本主題中的第一組範例會顯示將 XML 載入預設命名空間而且查詢錯誤的常見方式。</span><span class="sxs-lookup"><span data-stu-id="ffbae-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="ffbae-105">第二組範例顯示所需的修正，讓您可以在命名空間中查詢 XML。</span><span class="sxs-lookup"><span data-stu-id="ffbae-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="ffbae-106">如需詳細資訊，請參閱[處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="ffbae-106">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffbae-107">範例</span><span class="sxs-lookup"><span data-stu-id="ffbae-107">Example</span></span>  
 <span data-ttu-id="ffbae-108">此範例顯示 XML 在命名空間中的建立，以及傳回空結果集的查詢。</span><span class="sxs-lookup"><span data-stu-id="ffbae-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns='http://www.adventure-works.com'>  
        <Child>1</Child>  
        <Child>2</Child>  
        <Child>3</Child>  
        <AnotherChild>4</AnotherChild>  
        <AnotherChild>5</AnotherChild>  
        <AnotherChild>6</AnotherChild>  
    </Root>  
Dim c1 As IEnumerable(Of XElement) = _  
        From el In root.<Child> _  
        Select el  
Console.WriteLine("Result set follows:")  
For Each el As XElement In c1  
    Console.WriteLine(el.Value)  
Next  
Console.WriteLine("End of result set")  
```  
  
 <span data-ttu-id="ffbae-109">此範例會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="ffbae-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="ffbae-110">範例</span><span class="sxs-lookup"><span data-stu-id="ffbae-110">Example</span></span>  
 <span data-ttu-id="ffbae-111">此範例顯示 XML 在命名空間中的建立，以及編碼正確的查詢。</span><span class="sxs-lookup"><span data-stu-id="ffbae-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="ffbae-112">解決方案是宣告並初始化全域預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="ffbae-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="ffbae-113">這會將所有 XML 屬性放在預設的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="ffbae-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="ffbae-114">此範例不需要其他任何修改，就可以讓它正常運作。</span><span class="sxs-lookup"><span data-stu-id="ffbae-114">No other modifications are required to the example to make it work properly.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="ffbae-115">此範例會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="ffbae-115">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffbae-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffbae-116">See Also</span></span>  
 [<span data-ttu-id="ffbae-117">基本查詢 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffbae-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
