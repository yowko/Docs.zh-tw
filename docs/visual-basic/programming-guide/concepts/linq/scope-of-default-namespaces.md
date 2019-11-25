---
title: 預設命名空間的範圍
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: 8ba4d13b6d40180a88651f0503d1323f2b78f36c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343650"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="b0a5f-102">Scope of Default Namespaces in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0a5f-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="b0a5f-103">在 XML 樹狀結構中表示的預設命名空間不在查詢的範圍內。</span><span class="sxs-lookup"><span data-stu-id="b0a5f-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="b0a5f-104">如果您擁有的 XML 位於預設命名空間中，您仍然必須宣告 <xref:System.Xml.Linq.XNamespace> 變數，然後將它與區域名稱結合，讓限定名稱 (Qualified Name) 得以用於查詢中。</span><span class="sxs-lookup"><span data-stu-id="b0a5f-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="b0a5f-105">查詢 XML 時所遇到的其中一個最常見的問題是，如果 XML 樹狀結構有預設的命名空間，即使 XML 不在命名空間中，開發人員有時候還是會撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="b0a5f-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="b0a5f-106">本主題中的第一組範例會顯示載入預設命名空間中的 XML 但查詢錯誤的常見方式。</span><span class="sxs-lookup"><span data-stu-id="b0a5f-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="b0a5f-107">第二組範例顯示所需的修正，讓您可以在命名空間中查詢 XML。</span><span class="sxs-lookup"><span data-stu-id="b0a5f-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0a5f-108">範例</span><span class="sxs-lookup"><span data-stu-id="b0a5f-108">Example</span></span>  
 <span data-ttu-id="b0a5f-109">此範例顯示在命名空間中建立 XML，以及傳回空結果集的查詢。</span><span class="sxs-lookup"><span data-stu-id="b0a5f-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b0a5f-110">程式碼</span><span class="sxs-lookup"><span data-stu-id="b0a5f-110">Code</span></span>  
  
```vb  
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
  
### <a name="comments"></a><span data-ttu-id="b0a5f-111">註解</span><span class="sxs-lookup"><span data-stu-id="b0a5f-111">Comments</span></span>  
 <span data-ttu-id="b0a5f-112">此範例會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="b0a5f-112">This example produces the following result:</span></span>  
  
```console  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="b0a5f-113">範例</span><span class="sxs-lookup"><span data-stu-id="b0a5f-113">Example</span></span>  
 <span data-ttu-id="b0a5f-114">此範例顯示在命名空間中建立 XML，以及編碼正確的查詢。</span><span class="sxs-lookup"><span data-stu-id="b0a5f-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="b0a5f-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span><span class="sxs-lookup"><span data-stu-id="b0a5f-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="b0a5f-116">這會將所有 XML 屬性放在預設的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="b0a5f-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="b0a5f-117">此範例不需要其他任何修改，就可以讓它正常運作。</span><span class="sxs-lookup"><span data-stu-id="b0a5f-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b0a5f-118">程式碼</span><span class="sxs-lookup"><span data-stu-id="b0a5f-118">Code</span></span>  
  
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
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="b0a5f-119">註解</span><span class="sxs-lookup"><span data-stu-id="b0a5f-119">Comments</span></span>  
 <span data-ttu-id="b0a5f-120">此範例會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="b0a5f-120">This example produces the following result:</span></span>  
  
```console  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0a5f-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="b0a5f-121">See also</span></span>

- [<span data-ttu-id="b0a5f-122">Namespaces Overview (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0a5f-122">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
