---
title: 如何：控制命名空間前置字元 (C#) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: dd2a91fde868425cadbc395d6db0f913e2be600f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44182133"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="7e4ab-102">如何：控制命名空間前置字元 (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7e4ab-102">How to: Control Namespace Prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="7e4ab-103">這個主題描述如何在序列化 XML 樹狀時控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-103">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="7e4ab-104">在許多情況下，不需要控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-104">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="7e4ab-105">不過，某些 XML 程式設計工具需要命名空間前置詞的特定控制權。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-105">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="7e4ab-106">例如，您所操作的 XSLT 樣式表或 XAML 文件可能包含參考特定命名空間前置詞的內嵌 XPath 運算式。在此情況下，請務必使用這些特定前置詞來序列化文件。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-106">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="7e4ab-107">這就是控制命名空間前置詞的最常見原因。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-107">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="7e4ab-108">控制命名空間前置詞的另一個常見原因是，您要讓使用者手動編輯 XML 文件，而且您要建立使用者便於輸入的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-108">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="7e4ab-109">例如，您可能要產生 XSD 文件。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-109">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="7e4ab-110">若要轉換結構描述，建議您使用 `xs` 或 `xsd` 做為結構描述命名空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-110">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="7e4ab-111">若要控制命名空間前置詞，您可插入宣告命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-111">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="7e4ab-112">如果您宣告具有特定前置詞的命名空間，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 將會在序列化時，嘗試允許命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-112">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="7e4ab-113">若要建立宣告具有特定前置詞之命名空間的屬性，您可以建立屬性，其中之屬性名稱的命名空間為 <xref:System.Xml.Linq.XNamespace.Xmlns%2A>，而屬性的名稱為命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="7e4ab-114">屬性的值為命名空間的 URI。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-114">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e4ab-115">範例</span><span class="sxs-lookup"><span data-stu-id="7e4ab-115">Example</span></span>  
 <span data-ttu-id="7e4ab-116">這個範例會宣告兩個命名空間。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-116">This example declares two namespaces.</span></span> <span data-ttu-id="7e4ab-117">它會指定 `http://www.adventure-works.com` 命名空間的前置詞為 `aw`，而 `www.fourthcoffee.com` 命名空間的前置詞為 `fc`。</span><span class="sxs-lookup"><span data-stu-id="7e4ab-117">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
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
  
 <span data-ttu-id="7e4ab-118">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7e4ab-118">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e4ab-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="7e4ab-119">See Also</span></span>

- [<span data-ttu-id="7e4ab-120">處理 XML 命名空間 (C#)</span><span class="sxs-lookup"><span data-stu-id="7e4ab-120">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
