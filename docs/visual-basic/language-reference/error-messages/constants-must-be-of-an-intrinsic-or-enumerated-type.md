---
title: 常數必須是內建或列舉類型，而不是類別、結構、型別參數或陣列類型
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 702472751810c2d2bd08ece944ef0ffafc2049b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="eb6f8-102">常數必須是內建或列舉類型，而不是類別、結構、型別參數或陣列類型</span><span class="sxs-lookup"><span data-stu-id="eb6f8-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="eb6f8-103">您嘗試將常數宣告為類別、 結構或陣列型別，或包含泛型類型定義的型別參數。</span><span class="sxs-lookup"><span data-stu-id="eb6f8-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="eb6f8-104">常數必須是內建類型 (`Boolean`， `Byte`， `Date`， `Decimal`， `Double`， `Integer`， `Long`， `Object`， `SByte`， `Short`， `Single`， `String`， `UInteger`， `ULong`，或`UShort`)，或`Enum`類型根據其中一個整數類資料類型。</span><span class="sxs-lookup"><span data-stu-id="eb6f8-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="eb6f8-105">**錯誤 ID:** BC30424</span><span class="sxs-lookup"><span data-stu-id="eb6f8-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eb6f8-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="eb6f8-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="eb6f8-107">宣告常數作為內建或`Enum`型別。</span><span class="sxs-lookup"><span data-stu-id="eb6f8-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="eb6f8-108">常數也可以是特殊值，例如`True`， `False`，或`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="eb6f8-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="eb6f8-109">編譯器會考慮這些預先定義的值是適當的內建類型。</span><span class="sxs-lookup"><span data-stu-id="eb6f8-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6f8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb6f8-110">See Also</span></span>  
 [<span data-ttu-id="eb6f8-111">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="eb6f8-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="eb6f8-112">資料類型</span><span class="sxs-lookup"><span data-stu-id="eb6f8-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="eb6f8-113">資料類型</span><span class="sxs-lookup"><span data-stu-id="eb6f8-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)
