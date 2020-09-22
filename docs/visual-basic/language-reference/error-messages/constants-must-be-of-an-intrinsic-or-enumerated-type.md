---
title: 常數必須是內建或列舉類型，而不是類別、結構、型別參數或陣列類型
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: a9bbf27615233f4282e481710a0234b2fa589f63
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874557"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="73f69-102">常數必須是內建或列舉類型，而不是類別、結構、型別參數或陣列類型</span><span class="sxs-lookup"><span data-stu-id="73f69-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>

<span data-ttu-id="73f69-103">您已嘗試將常數宣告為類別、結構或陣列類型，或宣告為包含泛型型別所定義的型別參數。</span><span class="sxs-lookup"><span data-stu-id="73f69-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="73f69-104">常數必須是內建類型 (、、、、、、、、、、、、、 `Boolean` `Byte` `Date` `Decimal` `Double` `Integer` `Long` `Object` `SByte` `Short` `Single` `String` `UInteger` `ULong` 或 `UShort`) ，或是以 `Enum` 其中一個整數類型為基礎的型別。</span><span class="sxs-lookup"><span data-stu-id="73f69-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="73f69-105">**錯誤識別碼：** BC30424</span><span class="sxs-lookup"><span data-stu-id="73f69-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="73f69-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="73f69-106">To correct this error</span></span>  
  
1. <span data-ttu-id="73f69-107">將常數宣告為內建函式或 `Enum` 類型。</span><span class="sxs-lookup"><span data-stu-id="73f69-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2. <span data-ttu-id="73f69-108">常數也可以是特殊值 `True` ，例如、 `False` 或 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="73f69-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="73f69-109">編譯器會將這些預先定義的值視為適當的內建類型。</span><span class="sxs-lookup"><span data-stu-id="73f69-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f69-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73f69-110">See also</span></span>

- [<span data-ttu-id="73f69-111">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="73f69-111">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="73f69-112">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="73f69-112">Data Types</span></span>](../../programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="73f69-113">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="73f69-113">Data Types</span></span>](../data-types/index.md)
