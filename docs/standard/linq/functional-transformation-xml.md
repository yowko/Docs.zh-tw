---
title: XML LINQ to XML 的功能性轉換
description: 瞭解修改 XML 檔的純功能性轉換方法，以及它與程式化方法有何不同。
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: b23288e013a4104b21523e17e1f266a9f712c451
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552138"
---
# <a name="functional-transformation-of-xml-linq-to-xml"></a><span data-ttu-id="2891e-103">XML (LINQ to XML) 的功能性轉換</span><span class="sxs-lookup"><span data-stu-id="2891e-103">Functional transformation of XML (LINQ to XML)</span></span>

<span data-ttu-id="2891e-104">本文將討論用來修改 XML 檔的純功能性轉換方法，並將它與程式化方法形成對比。</span><span class="sxs-lookup"><span data-stu-id="2891e-104">This article discusses the pure functional transformation approach to modifying XML documents, and contrasts it with a procedural approach.</span></span>

## <a name="modifying-an-xml-document"></a><span data-ttu-id="2891e-105">修改 XML 檔</span><span class="sxs-lookup"><span data-stu-id="2891e-105">Modifying an XML document</span></span>

<span data-ttu-id="2891e-106">XML 程式設計人員其中一個最常見的工做為，將 XML 從一個組織結構轉換為另一個組織結構。</span><span class="sxs-lookup"><span data-stu-id="2891e-106">One of the most common tasks for an XML programmer is transforming XML from one shape to another.</span></span> <span data-ttu-id="2891e-107">XML 文件的組織結構就是文件的結構，其中包括：</span><span class="sxs-lookup"><span data-stu-id="2891e-107">The shape of an XML document is the structure of the document, which includes the following:</span></span>

- <span data-ttu-id="2891e-108">以文件表示的階層。</span><span class="sxs-lookup"><span data-stu-id="2891e-108">The hierarchy expressed by the document.</span></span>
- <span data-ttu-id="2891e-109">項目和屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="2891e-109">The element and attribute names.</span></span>
- <span data-ttu-id="2891e-110">項目和屬性的資料型別。</span><span class="sxs-lookup"><span data-stu-id="2891e-110">The data types of the elements and attributes.</span></span>

<span data-ttu-id="2891e-111">一般而言，將 XML 從一個組織結構轉換為另一個組織結構最有效的方法是，純功能性轉換的方法。</span><span class="sxs-lookup"><span data-stu-id="2891e-111">In general, the most effective approach to transforming XML from one shape to another is that of pure functional transformation.</span></span> <span data-ttu-id="2891e-112">以此種方法，程式設計人員的主要工做為建立適用於整個 XML 文件 (或者一或多個嚴格定義的程式碼) 的轉換。</span><span class="sxs-lookup"><span data-stu-id="2891e-112">In this approach, the primary programmer task is to create a transformation which is applied to the entire XML document (or to one or more strictly defined nodes).</span></span> <span data-ttu-id="2891e-113">在論證上，功能性轉換對程式碼而言是最簡單的 (在程式設計人員熟悉方法之後)，它會產生最容易維護的程式碼，而且通常比替代方法更精簡。</span><span class="sxs-lookup"><span data-stu-id="2891e-113">Functional transformation is arguably the easiest to code (after a programmer is familiar with the approach), yields the most maintainable code, and is often more compact than alternative approaches.</span></span>

### <a name="xml-functional-transformational-technologies"></a><span data-ttu-id="2891e-114">XML 功能轉換技術</span><span class="sxs-lookup"><span data-stu-id="2891e-114">XML functional transformational technologies</span></span>

<span data-ttu-id="2891e-115">Microsoft 提供兩個可用於 XML 文件的功能性轉換技術：XSLT 和 LINQ to XML。</span><span class="sxs-lookup"><span data-stu-id="2891e-115">Microsoft offers two functional transformation technologies for use on XML documents: XSLT and LINQ to XML.</span></span> <span data-ttu-id="2891e-116">在 <xref:System.Xml.Xsl> Managed 命名空間與 MSXML 的原始 COM 實作中支援 XSLT。</span><span class="sxs-lookup"><span data-stu-id="2891e-116">XSLT is supported in the <xref:System.Xml.Xsl> managed namespace and in the native COM implementation of MSXML.</span></span> <span data-ttu-id="2891e-117">雖然 XSLT 是強大的管理 XML 文件技術，但是它需要特殊領域的專業知識，也就是 XSLT 語言及其支援的 API。</span><span class="sxs-lookup"><span data-stu-id="2891e-117">Although XSLT is a robust technology for manipulating XML documents, it requires expertise in a specialized domain, namely the XSLT language and its supporting APIs.</span></span>

<span data-ttu-id="2891e-118">LINQ to XML 在 C# 或 Visual Basic 程式碼中，提供以明確而且強大的方式撰寫純功能性轉換之程式碼所需的工具。</span><span class="sxs-lookup"><span data-stu-id="2891e-118">LINQ to XML provides the tools necessary to code pure functional transformations in an expressive and powerful way, within C# or Visual Basic code.</span></span> <span data-ttu-id="2891e-119">例如，LINQ to XML 文件中的許多範例都使用純功能性方法。</span><span class="sxs-lookup"><span data-stu-id="2891e-119">For example, many of the examples in the LINQ to XML documentation use a pure functional approach.</span></span> <span data-ttu-id="2891e-120">此外，在 [教學課程：操作 WordprocessingML 檔中的內容](xml-shape-wordprocessingml-documents.md) 教學課程中，我們使用 LINQ to XML 以功能性方法操作 Microsoft Word 檔中的資訊。</span><span class="sxs-lookup"><span data-stu-id="2891e-120">Also, in the [Tutorial: Manipulating Content in a WordprocessingML Document](xml-shape-wordprocessingml-documents.md) tutorial, we use LINQ to XML in a functional approach to manipulate information in a Microsoft Word document.</span></span>

<span data-ttu-id="2891e-121">如需更完整的 LINQ to XML 與其他 Microsoft XML 技術的比較，請參閱 [LINQ to XML 與其他 xml 技術](linq-xml-vs-xml-technologies.md)的比較。</span><span class="sxs-lookup"><span data-stu-id="2891e-121">For a more complete comparison of LINQ to XML with other Microsoft XML technologies, see [LINQ to XML vs. other XML technologies](linq-xml-vs-xml-technologies.md).</span></span>

<span data-ttu-id="2891e-122">當來源文件具有不規則的結構時，XSLT 是文件中心轉換的建議工具。</span><span class="sxs-lookup"><span data-stu-id="2891e-122">XSLT is the recommended tool for  document-centric transformations when the source document has an irregular structure.</span></span> <span data-ttu-id="2891e-123">不過，LINQ to XML 也可以執行文件中心的轉換。</span><span class="sxs-lookup"><span data-stu-id="2891e-123">However, LINQ to XML can also perform document-centric transforms.</span></span> <span data-ttu-id="2891e-124">如需詳細資訊，請參閱 [如何使用批註來轉換 XSLT 樣式的 LINQ to XML 樹狀](use-annotations-transform-linq-xml-trees-xslt-style.md)結構。</span><span class="sxs-lookup"><span data-stu-id="2891e-124">For more information, see [How to use annotations to transform LINQ to XML trees in an XSLT style](use-annotations-transform-linq-xml-trees-xslt-style.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2891e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2891e-125">See also</span></span>

- [<span data-ttu-id="2891e-126">純功能性轉換簡介</span><span class="sxs-lookup"><span data-stu-id="2891e-126">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)
- [<span data-ttu-id="2891e-127">教學課程：操作 WordprocessingML 檔中的內容</span><span class="sxs-lookup"><span data-stu-id="2891e-127">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
- [<span data-ttu-id="2891e-128">LINQ to XML 與其他 XML 技術的比較</span><span class="sxs-lookup"><span data-stu-id="2891e-128">LINQ to XML vs. other XML technologies</span></span>](linq-xml-vs-xml-technologies.md)
