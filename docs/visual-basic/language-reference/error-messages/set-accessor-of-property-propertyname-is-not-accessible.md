---
title: 無法存取屬性 '<propertyname>' 的 'Set' 存取子
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 3bc50d6762998ca5d8f445d84c8b698c9f46436f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834461"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="98b15-102">'Set' 存取子的屬性 '\<屬性名稱 >' 不能存取</span><span class="sxs-lookup"><span data-stu-id="98b15-102">'Set' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="98b15-103">陳述式嘗試儲存屬性的值，當它並沒有屬性的存取`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="98b15-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="98b15-104">如果[Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)標示為更嚴格的存取權層級比其[Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)，嘗試設定屬性值無法在下列情況：</span><span class="sxs-lookup"><span data-stu-id="98b15-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="98b15-105">`Set`陳述式會標示[私人](../../../visual-basic/language-reference/modifiers/private.md)，而且呼叫程式碼是類別或結構定義的屬性之外。</span><span class="sxs-lookup"><span data-stu-id="98b15-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="98b15-106">`Set`陳述式會標示[Protected](../../../visual-basic/language-reference/modifiers/protected.md)和呼叫的程式碼是不在類別或結構中定義的屬性，也不是在衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="98b15-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="98b15-107">`Set`陳述式會標示[Friend](../../../visual-basic/language-reference/modifiers/friend.md)而且呼叫程式碼不是處於相同的組件中定義屬性。</span><span class="sxs-lookup"><span data-stu-id="98b15-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="98b15-108">**錯誤 ID:** BC31102</span><span class="sxs-lookup"><span data-stu-id="98b15-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="98b15-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="98b15-109">To correct this error</span></span>  
  
-   <span data-ttu-id="98b15-110">如果您可以定義該屬性的原始程式碼控制，請考慮宣告`Set`屬性本身以相同的存取層級的程序。</span><span class="sxs-lookup"><span data-stu-id="98b15-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="98b15-111">如果您沒有定義屬性的原始程式碼控制，或者您必須限制`Set`程序在多個屬性本身，試著將移至具有更好的存取權的程式碼區域中設定屬性值的陳述式存取層級屬性。</span><span class="sxs-lookup"><span data-stu-id="98b15-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98b15-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98b15-112">See also</span></span>

- [<span data-ttu-id="98b15-113">屬性程序</span><span class="sxs-lookup"><span data-stu-id="98b15-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="98b15-114">如何：宣告混合的存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="98b15-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
