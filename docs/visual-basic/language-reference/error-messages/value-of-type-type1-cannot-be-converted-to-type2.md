---
title: 類型 'type1' 的值無法轉換成 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 4a0f3eb2b1603899e9acc1273c023ec5d0ed3132
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913351"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="8030d-102">類型 'type1' 的值無法轉換成 'type2'</span><span class="sxs-lookup"><span data-stu-id="8030d-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="8030d-103">類型 'type1' 的值無法轉換成 'type2'。</span><span class="sxs-lookup"><span data-stu-id="8030d-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="8030d-104">您可以使用 'Value' 屬性，若要取得的第一個元素的字串值 '\<parentElement >'。</span><span class="sxs-lookup"><span data-stu-id="8030d-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="8030d-105">已嘗試將 XML 常值隱含轉換成特定類型。</span><span class="sxs-lookup"><span data-stu-id="8030d-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="8030d-106">您無法將 XML 常值隱含轉換成指定的類型。</span><span class="sxs-lookup"><span data-stu-id="8030d-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="8030d-107">**錯誤 ID:** BC31194</span><span class="sxs-lookup"><span data-stu-id="8030d-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8030d-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="8030d-108">To correct this error</span></span>  
  
- <span data-ttu-id="8030d-109">使用 XML 常值的 `Value` 屬性以 `String`形式來參考其值。</span><span class="sxs-lookup"><span data-stu-id="8030d-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="8030d-110">使用 `CType` 函式、另一個類型轉換函式或 <xref:System.Convert> 類別，將值轉換為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="8030d-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8030d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8030d-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="8030d-112">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="8030d-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="8030d-113">XML 常值</span><span class="sxs-lookup"><span data-stu-id="8030d-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="8030d-114">XML</span><span class="sxs-lookup"><span data-stu-id="8030d-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
