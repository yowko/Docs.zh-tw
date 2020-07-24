---
title: '如何控制命名空間前置詞（c #）（LINQ to XML）'
description: '瞭解如何在 c # 中以 LINQ to XML 序列化 XML 樹狀結構時，控制命名空間前置詞。 有些情況需要控制命名空間前置詞。'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: b0c5cbfa7488f3a7105595830ef6765e6bfb1f12
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105312"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="ee2b9-104">如何控制命名空間前置詞（c #）（LINQ to XML）</span><span class="sxs-lookup"><span data-stu-id="ee2b9-104">How to control namespace prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="ee2b9-105">這個主題描述如何在序列化 XML 樹狀時控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-105">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="ee2b9-106">在許多情況下，不需要控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-106">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="ee2b9-107">不過，某些 XML 程式設計工具需要命名空間前置詞的特定控制權。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-107">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="ee2b9-108">例如，您所操作的 XSLT 樣式表或 XAML 文件可能包含參考特定命名空間前置詞的內嵌 XPath 運算式。在此情況下，請務必使用這些特定前置詞來序列化文件。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-108">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="ee2b9-109">這就是控制命名空間前置詞的最常見原因。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-109">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="ee2b9-110">控制命名空間前置詞的另一個常見原因是，您要讓使用者手動編輯 XML 文件，而且您要建立使用者便於輸入的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-110">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="ee2b9-111">例如，您可能要產生 XSD 文件。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-111">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="ee2b9-112">若要轉換結構描述，建議您使用 `xs` 或 `xsd` 做為結構描述命名空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-112">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="ee2b9-113">若要控制命名空間前置詞，您可插入宣告命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-113">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="ee2b9-114">如果您宣告具有特定前置詞的命名空間，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 將會在序列化時，嘗試允許命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-114">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="ee2b9-115">若要建立宣告具有特定前置詞之命名空間的屬性，您可以建立屬性，其中之屬性名稱的命名空間為 <xref:System.Xml.Linq.XNamespace.Xmlns%2A>，而屬性的名稱為命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-115">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="ee2b9-116">屬性的值為命名空間的 URI。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-116">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee2b9-117">範例</span><span class="sxs-lookup"><span data-stu-id="ee2b9-117">Example</span></span>  
 <span data-ttu-id="ee2b9-118">這個範例會宣告兩個命名空間。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-118">This example declares two namespaces.</span></span> <span data-ttu-id="ee2b9-119">它會指定 `http://www.adventure-works.com` 命名空間的前置詞為 `aw`，而 `www.fourthcoffee.com` 命名空間的前置詞為 `fc`。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-119">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="ee2b9-120">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="ee2b9-120">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee2b9-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="ee2b9-121">See also</span></span>

- [<span data-ttu-id="ee2b9-122">命名空間概觀 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ee2b9-122">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
