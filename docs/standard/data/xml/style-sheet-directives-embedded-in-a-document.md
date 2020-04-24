---
title: 內嵌在文件中的樣式表指示詞
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 19e25ab7262bb006144eea71e74bd7454066b3f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710150"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="69563-102">內嵌在文件中的樣式表指示詞</span><span class="sxs-lookup"><span data-stu-id="69563-102">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="69563-103">有時候，現有的 XML 會包含 `<?xml:stylesheet?>` 的樣式表指示詞。</span><span class="sxs-lookup"><span data-stu-id="69563-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="69563-104">Microsoft Internet Explorer 將它視為 `<?xml-stylesheet?>` 語法的不同寫法。</span><span class="sxs-lookup"><span data-stu-id="69563-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="69563-105">XML 資料包含 `<?xml:stylesheet?>` 指示詞時，如果嘗試將這個資料載入 XML 文件物件模型 (DOM)，則會擲回例外狀況 (如同下列資料所示)。</span><span class="sxs-lookup"><span data-stu-id="69563-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="69563-106">因為 DOM 將 `<?xml:stylesheet?>` 視為無效的 **ProcessingInstruction**，所以會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="69563-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="69563-107">根據 Namespaces in XML 規格，任何 **ProcessingInstruction** 只能是無冒號名稱 (NCName)，相對於限定名稱 (QName)。</span><span class="sxs-lookup"><span data-stu-id="69563-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="69563-108">根據 Namespaces in XML 規格的第 6 節，在文件中，讓 **Load** 和 **LoadXml** 方法與規格相符的效果如下：</span><span class="sxs-lookup"><span data-stu-id="69563-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="69563-109">所有的項目型別和屬性名稱都包含零或一個冒號。</span><span class="sxs-lookup"><span data-stu-id="69563-109">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="69563-110">沒有任何實體名稱、ProcessingInstruction 目標或標記法名稱包含冒號。</span><span class="sxs-lookup"><span data-stu-id="69563-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="69563-111">如果 `<?xml:stylesheet?>` 包含冒號，即違反了第二個項目符號中的規則。</span><span class="sxs-lookup"><span data-stu-id="69563-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="69563-112">根據全球資訊網協會 (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/) (建立樣式表與 XML 文件的關聯 1.0 版建議事項)，能建立 XSLT 樣式表與 XML 文件關聯的處理指示為 `<?xml-stylesheet?>`，以破折號取代冒號。</span><span class="sxs-lookup"><span data-stu-id="69563-112">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="69563-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69563-113">See also</span></span>

- [<span data-ttu-id="69563-114">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="69563-114">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
