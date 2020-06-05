---
title: 宣告的 XML 元素和屬性名稱
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 043243eeee7c24d8c63105047fa3e7e0ed58c7b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374664"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="8d36c-102">宣告的 XML 項目和屬性的名稱 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d36c-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="8d36c-103">本主題提供在 XML 常值中命名 XML 元素和屬性的 Visual Basic 指導方針。</span><span class="sxs-lookup"><span data-stu-id="8d36c-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="8d36c-104">在 XML 常值中，您可以指定區功能變數名稱稱或限定名稱。</span><span class="sxs-lookup"><span data-stu-id="8d36c-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="8d36c-105">限定名稱是由 XML 命名空間前置詞、冒號和區功能變數名稱稱所組成。</span><span class="sxs-lookup"><span data-stu-id="8d36c-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="8d36c-106">如需 XML 命名空間前置詞的詳細資訊，請參閱[Xml 元素常](../../../language-reference/xml-literals/xml-element-literal.md)值。</span><span class="sxs-lookup"><span data-stu-id="8d36c-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="8d36c-107">規則</span><span class="sxs-lookup"><span data-stu-id="8d36c-107">Rules</span></span>  
 <span data-ttu-id="8d36c-108">Visual Basic 中元素或屬性的本機名稱必須遵守下列規則。</span><span class="sxs-lookup"><span data-stu-id="8d36c-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
- <span data-ttu-id="8d36c-109">它可以從命名空間開始。</span><span class="sxs-lookup"><span data-stu-id="8d36c-109">It can begin with a namespace.</span></span> <span data-ttu-id="8d36c-110">其開頭必須是字母字元或底線（ `_` ）。</span><span class="sxs-lookup"><span data-stu-id="8d36c-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="8d36c-111">它必須只包含字母字元、十進位數、底線、句點（.）和連字號（-）。</span><span class="sxs-lookup"><span data-stu-id="8d36c-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
- <span data-ttu-id="8d36c-112">長度不得超過1024個字元。</span><span class="sxs-lookup"><span data-stu-id="8d36c-112">It must not be more than 1,024 characters long.</span></span>  
  
- <span data-ttu-id="8d36c-113">出現在 [名稱] 中的冒號表示命名空間分界。</span><span class="sxs-lookup"><span data-stu-id="8d36c-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="8d36c-114">因此，您只能使用冒號來指定特定名稱的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="8d36c-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="8d36c-115">此外，您應該遵守下列指導方針。</span><span class="sxs-lookup"><span data-stu-id="8d36c-115">In addition, you should adhere to the following guideline.</span></span>  
  
- <span data-ttu-id="8d36c-116">XML 1.0 規格會保留以字串 "XML" 開頭的所有名稱，其大小寫不變。</span><span class="sxs-lookup"><span data-stu-id="8d36c-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="8d36c-117">因此，請不要將這些名稱用於您的元素和屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="8d36c-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="8d36c-118">名稱長度指導方針</span><span class="sxs-lookup"><span data-stu-id="8d36c-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="8d36c-119">很重要的是，名稱應該越短越好，同時仍能清楚地識別元素的本質。</span><span class="sxs-lookup"><span data-stu-id="8d36c-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="8d36c-120">這可以改善程式碼的可讀性，並縮短行長度和原始程式檔大小。</span><span class="sxs-lookup"><span data-stu-id="8d36c-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="8d36c-121">不過，您的名稱不應該太短，因為它不會適當地描述元素或程式碼使用它的方式。</span><span class="sxs-lookup"><span data-stu-id="8d36c-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="8d36c-122">這對於您的程式碼可讀性很重要。</span><span class="sxs-lookup"><span data-stu-id="8d36c-122">This is important for the readability of your code.</span></span> <span data-ttu-id="8d36c-123">如果有人嘗試瞭解它，或如果您在撰寫完之後，想要長時間查看它，適當的元素名稱可以節省時間。</span><span class="sxs-lookup"><span data-stu-id="8d36c-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="8d36c-124">名稱區分大小寫</span><span class="sxs-lookup"><span data-stu-id="8d36c-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="8d36c-125">XML 元素名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="8d36c-125">XML element names are case sensitive.</span></span> <span data-ttu-id="8d36c-126">這表示當 Visual Basic 編譯器比較字母大小寫不同的兩個名稱時，它會將它們解讀為不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d36c-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="8d36c-127">例如，它會將 `ABC` 和解讀 `abc` 為參考不同的元素。</span><span class="sxs-lookup"><span data-stu-id="8d36c-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="8d36c-128">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="8d36c-128">XML Namespaces</span></span>  
 <span data-ttu-id="8d36c-129">建立 XML 專案常值時，您可以指定元素名稱的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="8d36c-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="8d36c-130">如需詳細資訊，請參閱[XML 元素常](../../../language-reference/xml-literals/xml-element-literal.md)值。</span><span class="sxs-lookup"><span data-stu-id="8d36c-130">For more information, see [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d36c-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d36c-131">See also</span></span>

- [<span data-ttu-id="8d36c-132">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="8d36c-132">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="8d36c-133">XML 元素常值</span><span class="sxs-lookup"><span data-stu-id="8d36c-133">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
