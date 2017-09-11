---
title: "宣告的 XML 項目和屬性 (Visual Basic) 的名稱 |Microsoft 文件"
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
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2c0bb2350f50138d00e202e2e887a2202d21942f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="7b24d-102">宣告的 XML 項目和屬性的名稱 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b24d-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="7b24d-103">本主題提供[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML 項目和 XML 常值中的屬性命名指導方針。</span><span class="sxs-lookup"><span data-stu-id="7b24d-103">This topic provides [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="7b24d-104">您可以在 XML 常值，指定區域名稱或完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="7b24d-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="7b24d-105">限定的名稱是由 XML 命名空間前置詞、 冒號與本機名稱所組成。</span><span class="sxs-lookup"><span data-stu-id="7b24d-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="7b24d-106">如需 XML 命名空間前置詞的詳細資訊，請參閱[XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="7b24d-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="7b24d-107">規則</span><span class="sxs-lookup"><span data-stu-id="7b24d-107">Rules</span></span>  
 <span data-ttu-id="7b24d-108">項目或屬性中的本機名稱[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]必須遵守下列規則。</span><span class="sxs-lookup"><span data-stu-id="7b24d-108">A local name of an element or attribute in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="7b24d-109">它可以開始使用命名空間。</span><span class="sxs-lookup"><span data-stu-id="7b24d-109">It can begin with a namespace.</span></span> <span data-ttu-id="7b24d-110">它必須以字母字元或底線 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="7b24d-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="7b24d-111">它必須包含僅字母字元、 十進位數字、 底線、 句號 （.） 和連字號 （-）。</span><span class="sxs-lookup"><span data-stu-id="7b24d-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="7b24d-112">它不能超過 1024 個字元長。</span><span class="sxs-lookup"><span data-stu-id="7b24d-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="7b24d-113">出現在名稱中的冒號表示命名空間的分界。</span><span class="sxs-lookup"><span data-stu-id="7b24d-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="7b24d-114">因此，您可以使用冒號，只是用來指定特定名稱的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="7b24d-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="7b24d-115">此外，您應該遵守下列指導方針。</span><span class="sxs-lookup"><span data-stu-id="7b24d-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="7b24d-116">XML 1.0 規格會保留所有名稱開頭為"xml"，任何大小寫變化的字串。</span><span class="sxs-lookup"><span data-stu-id="7b24d-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="7b24d-117">因此，請勿使用這些元素的名稱和屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="7b24d-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="7b24d-118">名稱長度方針</span><span class="sxs-lookup"><span data-stu-id="7b24d-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="7b24d-119">事實上，名稱應該盡量縮短但仍可清楚識別的項目。</span><span class="sxs-lookup"><span data-stu-id="7b24d-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="7b24d-120">這可改善程式碼的可讀性，並減少線條長度和原始程式檔的大小。</span><span class="sxs-lookup"><span data-stu-id="7b24d-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="7b24d-121">不過，您的名稱不應該過短，無法正確地描述項目或程式碼使用它。</span><span class="sxs-lookup"><span data-stu-id="7b24d-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="7b24d-122">這是很重要的程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="7b24d-122">This is important for the readability of your code.</span></span> <span data-ttu-id="7b24d-123">如果有人試圖了解它，或您自己想要在您撰寫之後很長的時間，適當的項目名稱可以節省時間。</span><span class="sxs-lookup"><span data-stu-id="7b24d-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="7b24d-124">在 名稱區分大小寫</span><span class="sxs-lookup"><span data-stu-id="7b24d-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="7b24d-125">XML 項目名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="7b24d-125">XML element names are case sensitive.</span></span> <span data-ttu-id="7b24d-126">這表示當[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器比較兩個不同的字母大小寫的名稱，它會將它們解譯為不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="7b24d-126">This means that when the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="7b24d-127">比方說，它可解譯`ABC`和`abc`解釋為個別項目。</span><span class="sxs-lookup"><span data-stu-id="7b24d-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="7b24d-128">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="7b24d-128">XML Namespaces</span></span>  
 <span data-ttu-id="7b24d-129">在建立 XML 項目常值時，您可以指定 XML 命名空間前置詞的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="7b24d-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="7b24d-130">如需詳細資訊，請參閱[XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="7b24d-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b24d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b24d-131">See Also</span></span>  
 <span data-ttu-id="7b24d-132">[在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="7b24d-132">[Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="7b24d-133"> [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)</span><span class="sxs-lookup"><span data-stu-id="7b24d-133"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)</span></span>
