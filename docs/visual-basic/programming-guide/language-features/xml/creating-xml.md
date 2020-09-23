---
title: 建立 XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: a6a927c8dc1a4f3e38a99a1f730be68a2566d048
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090023"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="8e278-102">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="8e278-102">Creating XML in Visual Basic</span></span>

<span data-ttu-id="8e278-103">Visual Basic 可讓您直接在程式碼中使用 *XML 常* 值。</span><span class="sxs-lookup"><span data-stu-id="8e278-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="8e278-104">XML 常值語法代表 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件，它類似于 XML 1.0 語法。</span><span class="sxs-lookup"><span data-stu-id="8e278-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="8e278-105">這可讓您以程式設計方式更輕鬆地建立 XML 元素、檔和片段，因為您的程式碼具有與最終 XML 相同的結構。</span><span class="sxs-lookup"><span data-stu-id="8e278-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e278-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="8e278-106">In This Section</span></span>  
  
|<span data-ttu-id="8e278-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="8e278-107">Term</span></span>|<span data-ttu-id="8e278-108">定義</span><span class="sxs-lookup"><span data-stu-id="8e278-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="8e278-109">XML 常值概觀</span><span class="sxs-lookup"><span data-stu-id="8e278-109">XML Literals Overview</span></span>](xml-literals-overview.md)|<span data-ttu-id="8e278-110">XML 常值的簡介，以及它們之間的關聯性 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8e278-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="8e278-111">XML 中內嵌的運算式</span><span class="sxs-lookup"><span data-stu-id="8e278-111">Embedded Expressions in XML</span></span>](embedded-expressions-in-xml.md)|<span data-ttu-id="8e278-112">描述如何在 XML 常值中使用內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="8e278-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="8e278-113">如何：建立 XML 常值</span><span class="sxs-lookup"><span data-stu-id="8e278-113">How to: Create XML Literals</span></span>](how-to-create-xml-literals.md)|<span data-ttu-id="8e278-114">描述如何使用 XML 常值，在程式碼中建立 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="8e278-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="8e278-115">XML 常值中的空白字元</span><span class="sxs-lookup"><span data-stu-id="8e278-115">White Space in XML Literals</span></span>](white-space-in-xml-literals.md)|<span data-ttu-id="8e278-116">描述 Visual Basic 如何將空白字元視為 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="8e278-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="8e278-117">XML 常值和 XML 1.0 規格</span><span class="sxs-lookup"><span data-stu-id="8e278-117">XML Literals and the XML 1.0 Specification</span></span>](xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="8e278-118">描述 Visual Basic 中的 XML 常值語法與 XML 1.0 規格之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="8e278-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="8e278-119">如何：將運算式內嵌在 XML 常值中</span><span class="sxs-lookup"><span data-stu-id="8e278-119">How to: Embed Expressions in XML Literals</span></span>](how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="8e278-120">描述如何在執行時間使用 XML 常值中的內嵌運算式來建立內容。</span><span class="sxs-lookup"><span data-stu-id="8e278-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="8e278-121">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="8e278-121">Names of Declared XML Elements and Attributes</span></span>](names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="8e278-122">描述 XML 專案和屬性的命名方針。</span><span class="sxs-lookup"><span data-stu-id="8e278-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e278-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e278-123">See also</span></span>

- [<span data-ttu-id="8e278-124">XML</span><span class="sxs-lookup"><span data-stu-id="8e278-124">XML</span></span>](index.md)
