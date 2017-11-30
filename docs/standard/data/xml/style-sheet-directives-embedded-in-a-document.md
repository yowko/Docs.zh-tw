---
title: "內嵌在文件中的樣式表指示詞"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8c5cfcc9f35e4a07e9426a4dd24c1e2f04985f16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="4fdc2-102">內嵌在文件中的樣式表指示詞</span><span class="sxs-lookup"><span data-stu-id="4fdc2-102">Style Sheet Directives Embedded in a Document</span></span>
<span data-ttu-id="4fdc2-103">有時候，現有的 XML 會包含 `<?xml:stylesheet?>` 的樣式表指示詞。</span><span class="sxs-lookup"><span data-stu-id="4fdc2-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="4fdc2-104">Microsoft Internet Explorer 將它做為替代`<?xml-stylesheet?>`語法。</span><span class="sxs-lookup"><span data-stu-id="4fdc2-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="4fdc2-105">XML 資料包含 `<?xml:stylesheet?>` 指示詞時，如果嘗試將這個資料載入 XML 文件物件模型 (DOM)，則會擲回例外狀況 (如同下列資料所示)。</span><span class="sxs-lookup"><span data-stu-id="4fdc2-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 <span data-ttu-id="4fdc2-106">這是因為`<?xml:stylesheet?>`視為無效**ProcessingInstruction** dom 中。</span><span class="sxs-lookup"><span data-stu-id="4fdc2-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="4fdc2-107">任何**ProcessingInstruction**根據 Namespaces in XML 規格，只能是無冒號名稱 (Ncname)，相對於限定名稱 (Qname)。</span><span class="sxs-lookup"><span data-stu-id="4fdc2-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>  
  
 <span data-ttu-id="4fdc2-108">第 6 節 Namespaces in XML 規格，就會有的效果的**負載**和**LoadXml**方法符合規格是文件中：</span><span class="sxs-lookup"><span data-stu-id="4fdc2-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>  
  
-   <span data-ttu-id="4fdc2-109">所有的項目型別和屬性名稱都包含零或一個冒號。</span><span class="sxs-lookup"><span data-stu-id="4fdc2-109">All element types and attribute names contain either zero or one colon.</span></span>  
  
-   <span data-ttu-id="4fdc2-110">沒有任何實體名稱、ProcessingInstruction 目標或標記法名稱包含冒號。</span><span class="sxs-lookup"><span data-stu-id="4fdc2-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>  
  
 <span data-ttu-id="4fdc2-111">如果 `<?xml:stylesheet?>` 包含冒號，即違反了第二個項目符號中的規則。</span><span class="sxs-lookup"><span data-stu-id="4fdc2-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>  
  
 <span data-ttu-id="4fdc2-112">根據全球資訊網協會 (W3C) 將樣式表與 XML 文件產生關聯 1.0 版建議事項 (位於 www.w3.org/TR/xml-stylesheet)(英文)，能使 XSLT 樣式表與 XML 文件產生關聯的處理指示為 `<?xml-stylesheet?>`，以破折號取代冒號。</span><span class="sxs-lookup"><span data-stu-id="4fdc2-112">According to the World Wide Web Consortium (W3C) Associating Style Sheets with XML documents Version 1.0 Recommendation, located at www.w3.org/TR/xml-stylesheet, the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fdc2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fdc2-113">See Also</span></span>  
 [<span data-ttu-id="4fdc2-114">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="4fdc2-114">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
