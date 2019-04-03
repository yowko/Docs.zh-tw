---
title: 在 Visual Basic 中建立 XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: d847f589bc47f8ab3d6691666bbd879e795db0c6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813037"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="ee150-102">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="ee150-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="ee150-103">Visual Basic 可讓您使用*XML 常值*直接在您的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="ee150-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="ee150-104">XML 常值語法表示[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件，而且這是類似於 XML 1.0 語法。</span><span class="sxs-lookup"><span data-stu-id="ee150-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="ee150-105">這可讓您更輕鬆地以程式設計方式建立 XML 項目、 文件和片段，因為您的程式碼有相同的結構，為最後的 XML。</span><span class="sxs-lookup"><span data-stu-id="ee150-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee150-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="ee150-106">In This Section</span></span>  
  
|<span data-ttu-id="ee150-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="ee150-107">Term</span></span>|<span data-ttu-id="ee150-108">定義</span><span class="sxs-lookup"><span data-stu-id="ee150-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="ee150-109">XML 常值概觀</span><span class="sxs-lookup"><span data-stu-id="ee150-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="ee150-110">簡介 XML 常值和它們之間的關係[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ee150-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="ee150-111">XML 中內嵌的運算式</span><span class="sxs-lookup"><span data-stu-id="ee150-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="ee150-112">描述如何在 XML 常值中使用內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="ee150-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="ee150-113">如何：建立 XML 常值</span><span class="sxs-lookup"><span data-stu-id="ee150-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="ee150-114">描述如何在程式碼中使用 XML 常值建立的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="ee150-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="ee150-115">XML 常值中的空白字元</span><span class="sxs-lookup"><span data-stu-id="ee150-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="ee150-116">描述 Visual Basic XML 常值中處理泛空白字元的方式。</span><span class="sxs-lookup"><span data-stu-id="ee150-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="ee150-117">XML 常值和 XML 1.0 規格</span><span class="sxs-lookup"><span data-stu-id="ee150-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="ee150-118">描述如何在 Visual Basic 中的 XML 常值語法與 XML 1.0 規格。</span><span class="sxs-lookup"><span data-stu-id="ee150-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="ee150-119">如何：將運算式內嵌在 XML 常值</span><span class="sxs-lookup"><span data-stu-id="ee150-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="ee150-120">描述如何在 XML 常值中使用內嵌的運算式，在執行階段建立的內容。</span><span class="sxs-lookup"><span data-stu-id="ee150-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="ee150-121">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="ee150-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="ee150-122">描述 XML 元素和屬性命名指導方針。</span><span class="sxs-lookup"><span data-stu-id="ee150-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee150-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee150-123">See also</span></span>

- [<span data-ttu-id="ee150-124">XML</span><span class="sxs-lookup"><span data-stu-id="ee150-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
