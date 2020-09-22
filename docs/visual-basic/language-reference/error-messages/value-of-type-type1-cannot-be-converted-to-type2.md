---
title: 類型 'type1' 的值無法轉換成 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 8c80429db618e1bcadce1a58a6514d625f0b3cf1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870233"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="bc17e-102">類型 'type1' 的值無法轉換成 'type2'</span><span class="sxs-lookup"><span data-stu-id="bc17e-102">Value of type 'type1' cannot be converted to 'type2'</span></span>

<span data-ttu-id="bc17e-103">類型 ' type1 ' 的值無法轉換成 ' type2 '。</span><span class="sxs-lookup"><span data-stu-id="bc17e-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="bc17e-104">您可以使用 ' Value ' 屬性來取得 ' ' 第一個元素的字串值 \<parentElement> 。</span><span class="sxs-lookup"><span data-stu-id="bc17e-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="bc17e-105">已嘗試將 XML 常值隱含轉換成特定類型。</span><span class="sxs-lookup"><span data-stu-id="bc17e-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="bc17e-106">您無法將 XML 常值隱含轉換成指定的類型。</span><span class="sxs-lookup"><span data-stu-id="bc17e-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="bc17e-107">**錯誤識別碼：** BC31194</span><span class="sxs-lookup"><span data-stu-id="bc17e-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bc17e-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="bc17e-108">To correct this error</span></span>  
  
- <span data-ttu-id="bc17e-109">使用 XML 常值的 `Value` 屬性以 `String`形式來參考其值。</span><span class="sxs-lookup"><span data-stu-id="bc17e-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="bc17e-110">使用 `CType` 函式、另一個類型轉換函式或 <xref:System.Convert> 類別，將值轉換為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="bc17e-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc17e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc17e-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="bc17e-112">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="bc17e-112">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="bc17e-113">XML 常值</span><span class="sxs-lookup"><span data-stu-id="bc17e-113">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="bc17e-114">XML</span><span class="sxs-lookup"><span data-stu-id="bc17e-114">XML</span></span>](../../programming-guide/language-features/xml/index.md)
