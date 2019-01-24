---
title: 常數必須是內建或列舉類型，而不是類別、結構、型別參數或陣列類型
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 0f4cb04558bf9768de22f432a1c59203643aba6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595835"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="a65d4-102">常數必須是內建或列舉類型，而不是類別、結構、型別參數或陣列類型</span><span class="sxs-lookup"><span data-stu-id="a65d4-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="a65d4-103">您已嘗試宣告為類別、 結構或陣列類型或型別參數所包含的泛型類型定義的常數。</span><span class="sxs-lookup"><span data-stu-id="a65d4-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="a65d4-104">常數必須是內建類型 (`Boolean`， `Byte`， `Date`， `Decimal`， `Double`， `Integer`， `Long`， `Object`， `SByte`， `Short`， `Single`， `String`， `UInteger`， `ULong`，或`UShort`)，或有`Enum`以其中一種整數類資料類型為基礎類型。</span><span class="sxs-lookup"><span data-stu-id="a65d4-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="a65d4-105">**錯誤 ID:** BC30424</span><span class="sxs-lookup"><span data-stu-id="a65d4-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a65d4-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a65d4-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="a65d4-107">宣告作為內建常數或`Enum`型別。</span><span class="sxs-lookup"><span data-stu-id="a65d4-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="a65d4-108">常數，也可以是特殊值，例如`True`， `False`，或`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="a65d4-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="a65d4-109">編譯器會考慮這些預先定義的值必須是適當的內建類型。</span><span class="sxs-lookup"><span data-stu-id="a65d4-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65d4-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a65d4-110">See also</span></span>
- [<span data-ttu-id="a65d4-111">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="a65d4-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="a65d4-112">資料類型</span><span class="sxs-lookup"><span data-stu-id="a65d4-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="a65d4-113">資料類型</span><span class="sxs-lookup"><span data-stu-id="a65d4-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
