---
title: "命名空間概觀 (LINQ to XML) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 73eb9d0808666238e55abdf53888ec0f9b501fe2
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="namespaces-overview-linq-to-xml"></a><span data-ttu-id="6b3dd-102">命名空間概觀 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6b3dd-102">Namespaces Overview (LINQ to XML)</span></span>
<span data-ttu-id="6b3dd-103">本主題介紹 <xref:System.Xml.Linq.XName> 類別和 <xref:System.Xml.Linq.XNamespace> 類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-103">This topic introduces namespaces, the <xref:System.Xml.Linq.XName> class, and the <xref:System.Xml.Linq.XNamespace> class.</span></span>  
  
## <a name="xml-names"></a><span data-ttu-id="6b3dd-104">XML 名稱</span><span class="sxs-lookup"><span data-stu-id="6b3dd-104">XML Names</span></span>  
 <span data-ttu-id="6b3dd-105">XML 名稱通常是 XML 程式設計中的複雜性來源。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-105">XML names are often a source of complexity in XML programming.</span></span> <span data-ttu-id="6b3dd-106">XML 名稱包含 XML 命名空間 (也稱為 XML 命名空間 URI) 和區域名稱。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-106">An XML name consists of an XML namespace (also called an XML namespace URI) and a local name.</span></span> <span data-ttu-id="6b3dd-107">XML 命名空間與以 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 為基礎之程式中的命名空間很相似。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-107">An XML namespace is similar to a namespace in a [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]-based program.</span></span> <span data-ttu-id="6b3dd-108">它可讓您唯一限定項目和屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-108">It enables you to uniquely qualify the names of elements and attributes.</span></span> <span data-ttu-id="6b3dd-109">這有助於防止 XML 文件各個部分間的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-109">This helps avoid name conflicts between various parts of an XML document.</span></span> <span data-ttu-id="6b3dd-110">當您宣告 XML 命名空間時，您可以選擇僅在該命名空間中為唯一的區域名稱。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-110">When you have declared an XML namespace, you can select a local name that only has to be unique within that namespace.</span></span>  
  
 <span data-ttu-id="6b3dd-111">XML 名稱的另一個層面為 XML「命名空間前置詞」**。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-111">Another aspect of XML names is XML *namespace prefixes*.</span></span> <span data-ttu-id="6b3dd-112">XML 前置詞會造成 XML 名稱大部分的複雜度。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-112">XML prefixes cause most of the complexity of XML names.</span></span> <span data-ttu-id="6b3dd-113">這些前置詞可讓您建立 XML 命名空間的捷徑，讓 XML 文件更精簡而且更容易了解。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-113">These prefixes enable you to create a shortcut for an XML namespace, which makes the XML document more concise and understandable.</span></span> <span data-ttu-id="6b3dd-114">不過，XML 前置詞的內容與其意義相依，這會增加複雜度。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-114">However, XML prefixes depend on their context to have meaning, which adds complexity.</span></span> <span data-ttu-id="6b3dd-115">例如，XML 前置詞 `aw` 可以與 XML 樹狀結構一部分的其中一個 XML 命名空間產生關聯，並與 XML 樹狀結構不同部分的不同 XML 命名空間產生關聯。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-115">For example, the XML prefix `aw` could be associated with one XML namespace in one part of an XML tree, and with a different XML namespace in a different part of the XML tree.</span></span>  
  
 <span data-ttu-id="6b3dd-116">使用 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 搭配 C# 的其中一項優點是，您不必使用 XML 前置詞。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-116">One of the advantages of using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] with C# is that you do not have to use XML prefixes.</span></span> <span data-ttu-id="6b3dd-117">當 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 載入或剖析 XML 文件時，每個 XML 前置詞都會解析為其對應的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-117">When [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] loads or parses an XML document, each XML prefix is resolved to its corresponding XML namespace.</span></span> <span data-ttu-id="6b3dd-118">之後，當您處理使用命名空間的文件時，您幾乎永遠都要透過命名空間 URI (而非透過命名空間前置詞) 存取命名空間。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-118">After that, when you work with a document that uses namespaces, you almost always access the namespaces through the namespace URI, and not through the namespace prefix.</span></span> <span data-ttu-id="6b3dd-119">當開發人員在 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中使用 XML 名稱時，他們一律要使用完整的 XML 名稱 (也就是，XML 命名空間加上區域名稱)。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-119">When developers work with XML names in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] they always work with a fully-qualified XML name (that is, an XML namespace and a local name).</span></span> <span data-ttu-id="6b3dd-120">不過，必要時，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 可讓您使用並控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-120">However, when necessary, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] allows you to work with and control namespace prefixes.</span></span>  
  
 <span data-ttu-id="6b3dd-121">在 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中，代表 XML 名稱的類別是 <xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-121">In [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], the class that represents XML names is <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="6b3dd-122">XML 名稱經常出現在整個 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API 中，而且無論哪裡需要 XML 名稱，您都會找到 <xref:System.Xml.Linq.XName> 參數。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-122">XML names appear frequently throughout the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API, and wherever an XML name is required, you will find an <xref:System.Xml.Linq.XName> parameter.</span></span> <span data-ttu-id="6b3dd-123">但很少會直接使用 <xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-123">However, you rarely work directly with an <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="6b3dd-124"><xref:System.Xml.Linq.XName> 包含字串的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-124"><xref:System.Xml.Linq.XName> contains an implicit conversion from string.</span></span>  
  
 <span data-ttu-id="6b3dd-125">如需詳細資訊，請參閱 <xref:System.Xml.Linq.XNamespace> 和 <xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="6b3dd-125">For more information, see <xref:System.Xml.Linq.XNamespace> and <xref:System.Xml.Linq.XName>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b3dd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b3dd-126">See Also</span></span>  
 [<span data-ttu-id="6b3dd-127">處理 XML 命名空間 (C#)</span><span class="sxs-lookup"><span data-stu-id="6b3dd-127">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
