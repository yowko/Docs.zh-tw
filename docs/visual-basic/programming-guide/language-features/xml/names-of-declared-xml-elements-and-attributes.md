---
title: 宣告的 XML 項目和屬性的名稱 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07666ead0770c8055a62f75cb481648b0c72ef8b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="fb1b2-102">宣告的 XML 項目和屬性的名稱 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb1b2-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="fb1b2-103">本主題會提供 Visual Basic 指導方針命名 XML 元素和屬性在 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="fb1b2-104">您可以在 XML 常值，指定區域名稱或完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="fb1b2-105">限定的名稱是由 XML 命名空間前置詞、 冒號和本機名稱所組成。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="fb1b2-106">如需有關 XML 命名空間前置詞的詳細資訊，請參閱[XML 元素常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="fb1b2-107">規則</span><span class="sxs-lookup"><span data-stu-id="fb1b2-107">Rules</span></span>  
 <span data-ttu-id="fb1b2-108">項目或屬性在 Visual Basic 中的區域名稱必須遵守下列規則。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="fb1b2-109">它可以開始與命名空間。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-109">It can begin with a namespace.</span></span> <span data-ttu-id="fb1b2-110">它必須以字母字元或底線開頭 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="fb1b2-111">它必須包含只字母字元、 十進位數字、 底線、 句號 （.） 和連字號 （-）。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="fb1b2-112">它不能超過 1024 個字元長。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="fb1b2-113">出現在名稱中的冒號表示命名空間區分。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="fb1b2-114">因此，您可以使用冒號，只是用來指定特定名稱的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="fb1b2-115">此外，您應遵守下列指導方針。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="fb1b2-116">XML 1.0 規格會保留所有名稱開頭為"xml"，任何大小寫變化的字串。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="fb1b2-117">因此，請勿使用這些名稱，您的項目和屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="fb1b2-118">名稱長度指導方針</span><span class="sxs-lookup"><span data-stu-id="fb1b2-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="fb1b2-119">事實上，名稱應該短越好，但仍可清楚識別的項目。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="fb1b2-120">這可改善程式碼的可讀性，並減少線條長度和原始程式檔的大小。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="fb1b2-121">不過，您的名稱不應該短，無法適當地描述項目，或您的程式碼如何使用它。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="fb1b2-122">這是很重要的程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-122">This is important for the readability of your code.</span></span> <span data-ttu-id="fb1b2-123">如果其他人嘗試了解它，或您自己想要在您撰寫之後很長的時間，適當的項目名稱可以節省時間。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="fb1b2-124">在名稱中的區分大小寫</span><span class="sxs-lookup"><span data-stu-id="fb1b2-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="fb1b2-125">XML 項目名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-125">XML element names are case sensitive.</span></span> <span data-ttu-id="fb1b2-126">這表示，當 Visual Basic 編譯器會比較兩個名稱只有字母大小寫不同，它會將它們解譯為不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="fb1b2-127">例如，它可解譯`ABC`和`abc`視為參考到分隔項目。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="fb1b2-128">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="fb1b2-128">XML Namespaces</span></span>  
 <span data-ttu-id="fb1b2-129">在建立 XML 項目常值時，您可以指定的項目名稱的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="fb1b2-130">如需詳細資訊，請參閱[XML 元素常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="fb1b2-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb1b2-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb1b2-131">See Also</span></span>  
 [<span data-ttu-id="fb1b2-132">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="fb1b2-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="fb1b2-133">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="fb1b2-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
