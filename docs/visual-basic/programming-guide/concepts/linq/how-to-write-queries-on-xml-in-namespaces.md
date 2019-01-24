---
title: HOW TO：命名空間 (Visual Basic) 中的 XML 撰寫查詢
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 00dfc4e14c38357deb3efc4a32fd00a97f6010b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609924"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a><span data-ttu-id="ab994-102">HOW TO：命名空間 (Visual Basic) 中的 XML 撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="ab994-102">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>
<span data-ttu-id="ab994-103">若要撰寫命名空間 (Namespace) 中的 XML 查詢，您必須使用具有正確命名空間的 <xref:System.Xml.Linq.XName> 物件。</span><span class="sxs-lookup"><span data-stu-id="ab994-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="ab994-104">在 Visual Basic 中，最常見的方法是定義全域命名空間，然後使用利用全域命名空間的 XML 常值和 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="ab994-104">In Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="ab994-105">您可以定義預設的全域命名空間，在此情況下，XML 常值中的項目預設會在命名空間中。</span><span class="sxs-lookup"><span data-stu-id="ab994-105">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="ab994-106">或者，您可以利用前置詞定義全域命名空間，然後在 XML 常值和 XML 屬性中使用前置詞 (如有需要)。</span><span class="sxs-lookup"><span data-stu-id="ab994-106">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals, and in XML properties.</span></span> <span data-ttu-id="ab994-107">如同 XML 的其他格式，這些屬性預設永遠在沒有命名空間中。</span><span class="sxs-lookup"><span data-stu-id="ab994-107">As with other forms of XML, attributes are always in no namespace by default.</span></span>  
  
 <span data-ttu-id="ab994-108">本主題中的第一組範例會示範如何在預設命名空間中建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="ab994-108">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="ab994-109">第二組範例則示範如何在具有前置詞的命名空間中建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="ab994-109">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab994-110">範例</span><span class="sxs-lookup"><span data-stu-id="ab994-110">Example</span></span>  
 <span data-ttu-id="ab994-111">下列範例會建立位於預設命名空間中的 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="ab994-111">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="ab994-112">接著，它會擷取項目的集合。</span><span class="sxs-lookup"><span data-stu-id="ab994-112">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
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
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="ab994-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="ab994-113">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="ab994-114">範例</span><span class="sxs-lookup"><span data-stu-id="ab994-114">Example</span></span>  
 <span data-ttu-id="ab994-115">不過，在 Visual Basic 中，針對使用具有前置詞之命名空間的 XML 樹狀撰寫查詢與查詢預設命名空間中的 XML 樹狀相當不同。</span><span class="sxs-lookup"><span data-stu-id="ab994-115">In Visual Basic, however, writing queries on an XML tree that uses a namespace with a prefix is quite different from querying an XML tree in a default namespace.</span></span> <span data-ttu-id="ab994-116">一般而言，您會使用 `Imports` 陳述式來匯入具有前置詞的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ab994-116">Typically you use the `Imports` statement to import the namespace with a prefix.</span></span> <span data-ttu-id="ab994-117">然後，當您建構 XML 樹狀結構時，就會將此前置詞用於項目和屬性名稱中。</span><span class="sxs-lookup"><span data-stu-id="ab994-117">You then use the prefix in the element and attribute names when you construct the XML tree.</span></span> <span data-ttu-id="ab994-118">此外，在使用 XML 屬性來查詢 XML 樹狀結構時，您也會使用此前置詞。</span><span class="sxs-lookup"><span data-stu-id="ab994-118">You also use the prefix when querying an XML tree using XML properties.</span></span>  
  
 <span data-ttu-id="ab994-119">下列範例會建立位於命名空間中，具有前置詞的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="ab994-119">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="ab994-120">接著，它會擷取項目的集合。</span><span class="sxs-lookup"><span data-stu-id="ab994-120">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="ab994-121">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="ab994-121">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab994-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab994-122">See also</span></span>
- [<span data-ttu-id="ab994-123">處理 XML 命名空間 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab994-123">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
