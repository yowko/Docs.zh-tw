---
title: XML 命名空間 URI '<uri>' 只可繫結到 'xmlns'
ms.date: 07/20/2015
f1_keywords:
- bc31183
- vbc31183
helpviewer_keywords:
- BC31183
ms.assetid: 0ab1dbce-8397-4959-b2cd-f58798b051a0
ms.openlocfilehash: 9d791ae699f369ebe69e03fc5019d3ca58554224
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406478"
---
# <a name="xml-namespace-uri-httpwwww3orgxml1998namespace-can-be-bound-only-to-xmlns"></a><span data-ttu-id="50403-102">XML 命名空間 URI; 只能系結 `http://www.w3.org/XML/1998/namespace` 至 ' xmlns '</span><span class="sxs-lookup"><span data-stu-id="50403-102">XML namespace URI `http://www.w3.org/XML/1998/namespace`; can be bound only to 'xmlns'</span></span>
<span data-ttu-id="50403-103">URI `http://www.w3.org/XML/1998/namespace` 會用於 XML 命名空間宣告中。</span><span class="sxs-lookup"><span data-stu-id="50403-103">The URI `http://www.w3.org/XML/1998/namespace` is used in an XML namespace declaration.</span></span> <span data-ttu-id="50403-104">此 URI 是保留的命名空間，而且不能包含在 XML 命名空間宣告中。</span><span class="sxs-lookup"><span data-stu-id="50403-104">This URI is a reserved namespace and cannot be included in an XML namespace declaration.</span></span>  
  
 <span data-ttu-id="50403-105">**錯誤識別碼：** BC31183</span><span class="sxs-lookup"><span data-stu-id="50403-105">**Error ID:** BC31183</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="50403-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="50403-106">To correct this error</span></span>  
  
<span data-ttu-id="50403-107">請移除 XML 命名空間宣告，或 `http://www.w3.org/XML/1998/namespace` 使用有效的命名空間 URI 來取代 uri。</span><span class="sxs-lookup"><span data-stu-id="50403-107">Remove the XML namespace declaration or replace the URI `http://www.w3.org/XML/1998/namespace` with a valid namespace URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50403-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50403-108">See also</span></span>

- [<span data-ttu-id="50403-109">Imports 陳述式 (XML 命名空間)</span><span class="sxs-lookup"><span data-stu-id="50403-109">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="50403-110">XML 常值</span><span class="sxs-lookup"><span data-stu-id="50403-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="50403-111">XML</span><span class="sxs-lookup"><span data-stu-id="50403-111">XML</span></span>](../../programming-guide/language-features/xml/index.md)
