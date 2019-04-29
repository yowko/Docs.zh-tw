---
title: 類型 'type1' 的值無法轉換成 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: c8480c6fab2bff931950ebc21d0a8affe3c41c66
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774812"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="6b538-102">類型 'type1' 的值無法轉換成 'type2'</span><span class="sxs-lookup"><span data-stu-id="6b538-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="6b538-103">類型 'type1' 的值無法轉換成 'type2'。</span><span class="sxs-lookup"><span data-stu-id="6b538-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="6b538-104">您可以使用 'Value' 屬性，若要取得的第一個元素的字串值 '\<parentElement >'。</span><span class="sxs-lookup"><span data-stu-id="6b538-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="6b538-105">已嘗試將 XML 常值隱含轉換成特定類型。</span><span class="sxs-lookup"><span data-stu-id="6b538-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="6b538-106">您無法將 XML 常值隱含轉換成指定的類型。</span><span class="sxs-lookup"><span data-stu-id="6b538-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="6b538-107">**錯誤 ID:** BC31194</span><span class="sxs-lookup"><span data-stu-id="6b538-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6b538-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="6b538-108">To correct this error</span></span>  
  
- <span data-ttu-id="6b538-109">使用 XML 常值的 `Value` 屬性以 `String`形式來參考其值。</span><span class="sxs-lookup"><span data-stu-id="6b538-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="6b538-110">使用 `CType` 函式、另一個類型轉換函式或 <xref:System.Convert> 類別，將值轉換為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="6b538-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b538-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b538-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="6b538-112">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="6b538-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="6b538-113">XML 常值</span><span class="sxs-lookup"><span data-stu-id="6b538-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="6b538-114">XML</span><span class="sxs-lookup"><span data-stu-id="6b538-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
