---
title: ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: bda92b4244631f66142499a94be562854b35437e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406465"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="4cdff-102">ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性</span><span class="sxs-lookup"><span data-stu-id="4cdff-102">XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>
<span data-ttu-id="4cdff-103">ASP.NET 內的內嵌程式碼不支援 XML 常值和 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="4cdff-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="4cdff-104">若要使用 XML 功能，請將程式碼移至程式碼後置。</span><span class="sxs-lookup"><span data-stu-id="4cdff-104">To use XML features, move the code to code-behind.</span></span>  
  
 <span data-ttu-id="4cdff-105">XML 常值或 XML 軸屬性是在 ASP.NET 檔案中的內嵌程式碼（）內定義 `<%= =>` 。</span><span class="sxs-lookup"><span data-stu-id="4cdff-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>  
  
 <span data-ttu-id="4cdff-106">**錯誤識別碼：** BC31200</span><span class="sxs-lookup"><span data-stu-id="4cdff-106">**Error ID:** BC31200</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4cdff-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4cdff-107">To correct this error</span></span>  
  
- <span data-ttu-id="4cdff-108">將包含 XML 常值或 XML 軸屬性的程式碼移至 ASP.NET 程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="4cdff-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cdff-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cdff-109">See also</span></span>

- [<span data-ttu-id="4cdff-110">XML 常值</span><span class="sxs-lookup"><span data-stu-id="4cdff-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="4cdff-111">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="4cdff-111">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="4cdff-112">XML</span><span class="sxs-lookup"><span data-stu-id="4cdff-112">XML</span></span>](../../programming-guide/language-features/xml/index.md)
