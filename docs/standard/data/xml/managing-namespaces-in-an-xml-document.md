---
title: 管理 XML 文件中的命名空間
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83ea398f18ab02840ea811c74a6053dba11a3baa
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490883"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="ce530-102">管理 XML 文件中的命名空間</span><span class="sxs-lookup"><span data-stu-id="ce530-102">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="ce530-103">XML 命名空間會將 XML 文件中的項目與屬性名稱連結到自訂和預定的 URI。</span><span class="sxs-lookup"><span data-stu-id="ce530-103">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="ce530-104">若要建立這些關聯，請為命名空間 URI 定義前置詞，並使用這些前置詞來限定 XML 資料中的元素與屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ce530-104">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="ce530-105">命名空間可用來避免元素和屬性名稱發生衝突，並讓相同名稱的元素和屬性以不同方式處理和驗證。</span><span class="sxs-lookup"><span data-stu-id="ce530-105">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a><span data-ttu-id="ce530-106">宣告命名空間</span><span class="sxs-lookup"><span data-stu-id="ce530-106">Declaring namespaces</span></span>  
 <span data-ttu-id="ce530-107">若要在元素上宣告命名空間，請使用 `xmlns:` 屬性：</span><span class="sxs-lookup"><span data-stu-id="ce530-107">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="ce530-108">其中 `<name>` 是命名空間前置詞，而 `<"uri">` 則是識別命名空間的 URI。</span><span class="sxs-lookup"><span data-stu-id="ce530-108">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="ce530-109">在宣告前置詞之後，您可以用它來限定 XML 文件中的元素和屬性，並將其與命名空間 URI 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="ce530-109">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="ce530-110">因為命名空間前置詞會用於整份文件，所以其長度應該短一點。</span><span class="sxs-lookup"><span data-stu-id="ce530-110">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="ce530-111">這個範例會定義兩個 `BOOK` 元素。</span><span class="sxs-lookup"><span data-stu-id="ce530-111">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="ce530-112">第一個元素由前置詞 `mybook` 所限定，而第二個元素則由前置詞 `bb` 所限定。</span><span class="sxs-lookup"><span data-stu-id="ce530-112">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="ce530-113">每個前置詞都與不同的命名空間 URI 相關：</span><span class="sxs-lookup"><span data-stu-id="ce530-113">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 <span data-ttu-id="ce530-114">若要表示某元素是特定命名空間的一部分，請將命名空間前置詞加到其中。</span><span class="sxs-lookup"><span data-stu-id="ce530-114">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="ce530-115">例如，如果 `Author` 元素屬於 `mybook` 命名空間，便會將它宣告為 `<mybook:Author>`。</span><span class="sxs-lookup"><span data-stu-id="ce530-115">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a><span data-ttu-id="ce530-116">宣告範圍</span><span class="sxs-lookup"><span data-stu-id="ce530-116">Declaration scope</span></span>  
 <span data-ttu-id="ce530-117">命名空間的有效範圍，是從宣告點至宣告該命名空間之元素的結尾。</span><span class="sxs-lookup"><span data-stu-id="ce530-117">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="ce530-118">在此範例中，於 `BOOK` 元素中定義的命名空間並不適用於 `BOOK` 元素以外的元素，如 `Publisher` 元素：</span><span class="sxs-lookup"><span data-stu-id="ce530-118">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 <span data-ttu-id="ce530-119">雖然命名空間必須先行宣告才能使用，但它不必出現在 XML 文件的最前面。</span><span class="sxs-lookup"><span data-stu-id="ce530-119">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="ce530-120">當您在 XML 文件中使用多個命名空間時，您可以定義一個命名空間當做預設命名空間，以便建立更易讀取的文件。</span><span class="sxs-lookup"><span data-stu-id="ce530-120">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="ce530-121">預設命名空間會在根元素中宣告，並且套用到文件中所有非限定的元素。</span><span class="sxs-lookup"><span data-stu-id="ce530-121">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="ce530-122">預設命名空間僅適用於元素，不適用於屬性。</span><span class="sxs-lookup"><span data-stu-id="ce530-122">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="ce530-123">若要使用預設命名空間，請在元素的宣告中省略前置詞和冒號：</span><span class="sxs-lookup"><span data-stu-id="ce530-123">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="ce530-124">管理命名空間</span><span class="sxs-lookup"><span data-stu-id="ce530-124">Managing namespaces</span></span>  
 <span data-ttu-id="ce530-125"><xref:System.Xml.XmlNamespaceManager> 類別會保存命名空間 URI 和其前置詞的集合，並讓您從這個集合查詢、加入及移除命名空間。</span><span class="sxs-lookup"><span data-stu-id="ce530-125">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="ce530-126">某些內容中需要使用這個類別，才能改善 XML 處理效能。</span><span class="sxs-lookup"><span data-stu-id="ce530-126">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="ce530-127">例如，<xref:System.Xml.Xsl.XsltContext> 類別會使用 <xref:System.Xml.XmlNamespaceManager>，以提供 XPath 支援。</span><span class="sxs-lookup"><span data-stu-id="ce530-127">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="ce530-128">命名空間管理員不會在命名空間上執行任何驗證，而是會假設前置詞和命名空間已經過驗證並且符合 [W3C 命名空間](https://www.w3.org/TR/REC-xml-names/)規格。</span><span class="sxs-lookup"><span data-stu-id="ce530-128">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce530-129">[C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) 和 [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) 中的 LINQ TO XML 不會使用 <xref:System.Xml.XmlNamespaceManager> 管理命名空間。</span><span class="sxs-lookup"><span data-stu-id="ce530-129">LINQ TO XML in [C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="ce530-130">如需在使用 LINQ to XML 時管理命名空間的資訊，請參閱 LINQ 文件中的[處理 XML 命名空間 (C#)](../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md) 和[處理 XML 命名空間 (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="ce530-130">See [Working with XML Namespaces (C#)](../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md) and [Working with XML Namespaces (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="ce530-131">以下是您可以使用 <xref:System.Xml.XmlNamespaceManager> 類別執行的一些管理和查詢工作。</span><span class="sxs-lookup"><span data-stu-id="ce530-131">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="ce530-132">如需詳細資訊和範例，請追蹤每個方法或屬性的參考頁面連結。</span><span class="sxs-lookup"><span data-stu-id="ce530-132">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="ce530-133">以</span><span class="sxs-lookup"><span data-stu-id="ce530-133">To</span></span>|<span data-ttu-id="ce530-134">使用</span><span class="sxs-lookup"><span data-stu-id="ce530-134">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="ce530-135">加入命名空間</span><span class="sxs-lookup"><span data-stu-id="ce530-135">Add a namespace</span></span>|<span data-ttu-id="ce530-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="ce530-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="ce530-137">移除命名空間</span><span class="sxs-lookup"><span data-stu-id="ce530-137">Remove a namespace</span></span>|<span data-ttu-id="ce530-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="ce530-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="ce530-139">尋找預設命名空間的 URI</span><span class="sxs-lookup"><span data-stu-id="ce530-139">Find the URI for the default namespace</span></span>|<span data-ttu-id="ce530-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="ce530-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="ce530-141">尋找命名空間前置詞的 URI</span><span class="sxs-lookup"><span data-stu-id="ce530-141">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="ce530-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="ce530-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="ce530-143">尋找命名空間 URI 的前置詞</span><span class="sxs-lookup"><span data-stu-id="ce530-143">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="ce530-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="ce530-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="ce530-145">取得目前節點中的命名空間清單</span><span class="sxs-lookup"><span data-stu-id="ce530-145">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="ce530-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="ce530-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="ce530-147">設定命名空間的範圍</span><span class="sxs-lookup"><span data-stu-id="ce530-147">Scope a namespace</span></span>|<span data-ttu-id="ce530-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> 和 <xref:System.Xml.XmlNamespaceManager.PopScope%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="ce530-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="ce530-149">檢查前置詞是否定義於目前範圍中</span><span class="sxs-lookup"><span data-stu-id="ce530-149">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="ce530-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="ce530-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="ce530-151">取得用來查詢前置詞與 URI 的名稱資料表</span><span class="sxs-lookup"><span data-stu-id="ce530-151">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="ce530-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="ce530-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce530-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce530-153">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="ce530-154">XML 文件和資料</span><span class="sxs-lookup"><span data-stu-id="ce530-154">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
