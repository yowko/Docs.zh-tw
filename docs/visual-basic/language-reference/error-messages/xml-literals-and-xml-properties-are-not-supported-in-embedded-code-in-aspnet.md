---
title: ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 893fdb1b9b3b5ace6b869c7b64ce7483ff523023
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180679"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="c33d6-102">ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性</span><span class="sxs-lookup"><span data-stu-id="c33d6-102">XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>
<span data-ttu-id="c33d6-103">在 ASP.NET 中的內嵌程式碼中不支援 XML 常值和 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="c33d6-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="c33d6-104">若要使用 XML 功能，將移至程式碼後置的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c33d6-104">To use XML features, move the code to code-behind.</span></span>  
  
 <span data-ttu-id="c33d6-105">內嵌程式碼內定義的 XML 常值或 XML 軸屬性 (`<%= =>`) ASP.NET 檔案中。</span><span class="sxs-lookup"><span data-stu-id="c33d6-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>  
  
 <span data-ttu-id="c33d6-106">**錯誤 ID:** BC31200</span><span class="sxs-lookup"><span data-stu-id="c33d6-106">**Error ID:** BC31200</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c33d6-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c33d6-107">To correct this error</span></span>  
  
-   <span data-ttu-id="c33d6-108">將程式碼，包括 XML 常值或 XML 軸屬性移至的 ASP.NET 程式碼後置檔案中。</span><span class="sxs-lookup"><span data-stu-id="c33d6-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c33d6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c33d6-109">See Also</span></span>  
 [<span data-ttu-id="c33d6-110">XML 常值</span><span class="sxs-lookup"><span data-stu-id="c33d6-110">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="c33d6-111">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="c33d6-111">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="c33d6-112">XML</span><span class="sxs-lookup"><span data-stu-id="c33d6-112">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
