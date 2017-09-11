---
title: "在 Visual Basic 中建立 XML |Microsoft 文件"
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
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
caps.latest.revision: 24
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
ms.openlocfilehash: ec45ab4dc7d4c9282d444c00b0b262b3d8dd4da1
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="5ae82-102">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="5ae82-102">Creating XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="5ae82-103">可讓您使用*XML 常值*直接在您的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="5ae82-103"> enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="5ae82-104">XML 常值語法代表[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]物件，並且會類似於 XML 1.0 語法。</span><span class="sxs-lookup"><span data-stu-id="5ae82-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="5ae82-105">這可讓您更輕鬆地以程式設計方式建立 XML 項目、 文件和片段，因為您的程式碼有最後的 XML 的結構相同。</span><span class="sxs-lookup"><span data-stu-id="5ae82-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ae82-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="5ae82-106">In This Section</span></span>  
  
|<span data-ttu-id="5ae82-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="5ae82-107">Term</span></span>|<span data-ttu-id="5ae82-108">定義</span><span class="sxs-lookup"><span data-stu-id="5ae82-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="5ae82-109">XML 常值概觀</span><span class="sxs-lookup"><span data-stu-id="5ae82-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="5ae82-110">簡介 XML 常值和它們之間的關係[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5ae82-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>|  
|[<span data-ttu-id="5ae82-111">XML 中內嵌的運算式</span><span class="sxs-lookup"><span data-stu-id="5ae82-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="5ae82-112">描述如何使用 XML 常值中內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="5ae82-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="5ae82-113">如何：建立 XML 常值</span><span class="sxs-lookup"><span data-stu-id="5ae82-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="5ae82-114">描述如何使用 XML 常值程式碼中建立的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="5ae82-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="5ae82-115">XML 常值中的空白字元</span><span class="sxs-lookup"><span data-stu-id="5ae82-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="5ae82-116">描述如何[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會將 XML 常值中的泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="5ae82-116">Describes how [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="5ae82-117">XML 常值和 XML 1.0 規格</span><span class="sxs-lookup"><span data-stu-id="5ae82-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="5ae82-118">描述如何在 XML 常值語法[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]與 XML 1.0 規格。</span><span class="sxs-lookup"><span data-stu-id="5ae82-118">Describes how the XML literal syntax in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="5ae82-119">如何：將運算式內嵌在 XML 常值中</span><span class="sxs-lookup"><span data-stu-id="5ae82-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="5ae82-120">描述如何使用 XML 常值中內嵌的運算式，在執行階段建立的內容。</span><span class="sxs-lookup"><span data-stu-id="5ae82-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="5ae82-121">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="5ae82-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="5ae82-122">描述 XML 元素和屬性命名指導方針。</span><span class="sxs-lookup"><span data-stu-id="5ae82-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ae82-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ae82-123">See Also</span></span>  
 [<span data-ttu-id="5ae82-124">XML</span><span class="sxs-lookup"><span data-stu-id="5ae82-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
