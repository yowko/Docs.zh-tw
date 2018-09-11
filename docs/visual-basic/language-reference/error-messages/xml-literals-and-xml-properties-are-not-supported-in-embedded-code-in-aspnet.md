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
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275752"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="ae7a5-102">ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性</span><span class="sxs-lookup"><span data-stu-id="ae7a5-102">XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>
<span data-ttu-id="ae7a5-103">在 ASP.NET 中的內嵌程式碼中不支援 XML 常值和 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="ae7a5-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="ae7a5-104">若要使用 XML 功能，將移至程式碼後置的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae7a5-104">To use XML features, move the code to code-behind.</span></span>  
  
 <span data-ttu-id="ae7a5-105">內嵌程式碼內定義的 XML 常值或 XML 軸屬性 (`<%= =>`) ASP.NET 檔案中。</span><span class="sxs-lookup"><span data-stu-id="ae7a5-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>  
  
 <span data-ttu-id="ae7a5-106">**錯誤 ID:** BC31200</span><span class="sxs-lookup"><span data-stu-id="ae7a5-106">**Error ID:** BC31200</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ae7a5-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ae7a5-107">To correct this error</span></span>  
  
-   <span data-ttu-id="ae7a5-108">將程式碼，包括 XML 常值或 XML 軸屬性移至的 ASP.NET 程式碼後置檔案中。</span><span class="sxs-lookup"><span data-stu-id="ae7a5-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae7a5-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae7a5-109">See Also</span></span>  
 [<span data-ttu-id="ae7a5-110">XML 常值</span><span class="sxs-lookup"><span data-stu-id="ae7a5-110">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="ae7a5-111">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="ae7a5-111">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="ae7a5-112">XML</span><span class="sxs-lookup"><span data-stu-id="ae7a5-112">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
