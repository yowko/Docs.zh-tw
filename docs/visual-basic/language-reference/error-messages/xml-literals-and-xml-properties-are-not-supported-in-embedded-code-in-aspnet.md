---
title: ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 861677636f9a73015b26efec30df728d07fbdf72
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870208"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="1397a-102">ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性</span><span class="sxs-lookup"><span data-stu-id="1397a-102">XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>

<span data-ttu-id="1397a-103">ASP.NET 內的內嵌程式碼不支援 XML 常值和 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="1397a-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="1397a-104">若要使用 XML 功能，請將程式碼移至程式碼後端。</span><span class="sxs-lookup"><span data-stu-id="1397a-104">To use XML features, move the code to code-behind.</span></span>  
  
 <span data-ttu-id="1397a-105">XML 常值或 XML 軸屬性是在內嵌程式碼中定義 (`<%= =>` 在 ASP.NET 檔中) 。</span><span class="sxs-lookup"><span data-stu-id="1397a-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>  
  
 <span data-ttu-id="1397a-106">**錯誤識別碼：** BC31200</span><span class="sxs-lookup"><span data-stu-id="1397a-106">**Error ID:** BC31200</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1397a-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1397a-107">To correct this error</span></span>  
  
- <span data-ttu-id="1397a-108">將包含 XML 常值或 XML 軸屬性的程式碼移至 ASP.NET 程式碼後端檔案。</span><span class="sxs-lookup"><span data-stu-id="1397a-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1397a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1397a-109">See also</span></span>

- [<span data-ttu-id="1397a-110">XML 常值</span><span class="sxs-lookup"><span data-stu-id="1397a-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="1397a-111">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="1397a-111">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="1397a-112">XML</span><span class="sxs-lookup"><span data-stu-id="1397a-112">XML</span></span>](../../programming-guide/language-features/xml/index.md)
